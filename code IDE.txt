#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x20, 16, 2);

const int sensorPins[] = {2, 3, 4, 5, 6, 7, 8, 9, 10};
const int numSensors = 9;
const int blueLED = 15;
const int greenLED = 11;
const int orangeLED = 12;
const int speaker = 14;

const String gasTypes[] = {
  "Smk", // MQ-2 - Smoke
  "Alc", // MQ-3 - Alcohol
  "Mth", // MQ-4 - Methane
  "LPG", // MQ-5 - LPG
  "Btn", // MQ-6 - Butane
  "CO", // MQ-7 - CO
  "H2", // MQ-8 - Hydrogen
  "Flm", // MQ-9 - Flammable
  "AQ" // MQ-135 - Air Quality
};

bool lastAlert = false;

void setup() {
  Serial.begin(9600);
  lcd.init();
  lcd.backlight();
  lcd.print("LCD TEST");
  lcd.setCursor(0, 1);
  lcd.print("System Online");
  Serial.println("System Initialized");

  for (int i = 0; i < numSensors; i++) {
    pinMode(sensorPins[i], INPUT_PULLUP);
  }
  pinMode(blueLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(orangeLED, OUTPUT);
  pinMode(speaker, OUTPUT);

  digitalWrite(blueLED, HIGH);
  digitalWrite(greenLED, HIGH);
  digitalWrite(orangeLED, LOW);

  delay(300);
}

void loop() {
  bool alert = false;
  String triggeredSensors = "";

  for (int i = 0; i < numSensors; i++) {
    bool detected = false;
    int reading = digitalRead(sensorPins[i]);
    delay(5);

    if (reading == HIGH) {
      detected = true;
    }

    if (detected) {
      alert = true;
      int sensorNum = (i == 8) ? 135 : (i + 2);
      triggeredSensors += "MQ-" + String(sensorNum) + " (" + gasTypes[i] + ") ";
      Serial.print("Gas detected on MQ-");
      Serial.print(sensorNum);
      Serial.print(" (");
      Serial.print(gasTypes[i]);
      Serial.println(")");
    }
  }

  if (alert) {
    digitalWrite(greenLED, LOW);
    digitalWrite(orangeLED, HIGH);
    tone(speaker, 500);
    Serial.println("Speaker activated");
    lcd.clear();
    lcd.print("Alert! Gas:");
    lcd.setCursor(0, 1);
    if (triggeredSensors.length() > 16) {
      triggeredSensors = triggeredSensors.substring(0, 13) + "...";
    }
    lcd.print(triggeredSensors);
    lastAlert = true;
  } else {
    digitalWrite(greenLED, HIGH);
    digitalWrite(orangeLED, LOW);
    noTone(speaker);
    if (lastAlert) {
      lcd.clear();
      lcd.print(".Good condition.");
      lastAlert = false;
    }
  }
  delay(50);
}