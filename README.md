# Gas Detection System with MQ Sensors and Arduino
## Description
This project is a gas detection system simulated in Proteus 9, using multiple MQ gas sensors connected to an Arduino board. It detects various gases like smoke, alcohol, methane, LPG, butane, CO, hydrogen, flammable gases, and air quality issues. When a gas is detected, it triggers an alarm on a buzzer, displays the alert on an LCD screen, and changes LED indicators. The system includes a C++ code for Arduino, Proteus simulation files, and necessary libraries for the sensors.
The circuit includes:
- 9 MQ sensors (MQ-2 to MQ-9 and MQ-135)
- Arduino Uno
- LCD (I2C, 16x2)
- LEDs (blue for system on, green for safe, orange for alert)
- Buzzer for audio alarm
- Resistors and other components for proper wiring
This is a student project for practicing embedded systems, sensor integration, and simulation in Proteus.
Additionally, there is a 'file' folder containing the project proposal, business plan, and a short video of the project test.
## Features
- **Multi-Gas Detection**: Monitors 9 types of gases using MQ sensors:
  - MQ-2: Smoke (Smk)
  - MQ-3: Alcohol (Alc)
  - MQ-4: Methane (Mth)
  - MQ-5: LPG (LPG)
  - MQ-6: Butane (Btn)
  - MQ-7: CO (CO)
  - MQ-8: Hydrogen (H2)
  - MQ-9: Flammable (Flm)
  - MQ-135: Air Quality (AQ)
- **Real-Time Alerts**: Buzzer sounds, orange LED lights up, and LCD shows "Alert! Gas: [triggered sensors]" when gas is detected.
- **Status Indicators**: Green LED for safe conditions, blue LED for system online.
- **Serial Monitoring**: Outputs detection details to Serial Monitor for debugging.
- **Simulation Ready**: Designed for Proteus 9, with all sensor libraries included.
## Technologies Used
- **Hardware/Simulation**: Arduino Uno, MQ Gas Sensors (MQ-2 to MQ-9, MQ-135), LCD I2C (16x2), LEDs, Buzzer, Resistors (e.g., 0.1k, 4.7k).
- **Software**: Proteus 9 for circuit simulation (downloaded from https://soft98.ir/software/engineering/3535-%D8%AF%D8%A7%D9%86%D9%84%D9%88%D8%AF-proteus.html), Arduino IDE for coding and compiling (downloaded from https://www.yasdl.com/134583/%D8%AF%D8%A7%D9%86%D9%84%D9%88%D8%AF-arduino.html) (includes .hex file for upload).
- **Programming**: C++ with Arduino libraries (Wire.h for I2C, LiquidCrystal_I2C.h for LCD).
- **Libraries**:
  - MQ Sensor Libraries for Proteus: Downloaded from [The Engineering Projects](https://www.theengineeringprojects.com/2016/05/gas-sensor-library-proteus.html) (for default MQ sensors).
  - MQ-135 Library: From [GitHub - satyamkr80/MQ135-GAS-Sensor-Library-Proteus](https://github.com/satyamkr80/MQ135-GAS-Sensor-Library-Proteus).
## Installation and Setup
1. **Download Libraries**:
   - Get MQ sensor libraries from [The Engineering Projects](https://www.theengineeringprojects.com/2016/05/gas-sensor-library-proteus.html).
   - Get MQ-135 library from [GitHub](https://github.com/satyamkr80/MQ135-GAS-Sensor-Library-Proteus).
   - Place the library folders in your Proteus libraries directory (usually `C:\ProgramData\Labcenter Electronics\Proteus 8 Professional\LIBRARY` or similar).
2. **Clone the Repository**:
3. **Open in Proteus**:
- Launch Proteus 9.
- Open the .pdsprj file (simulation project file) from the repository.
- Ensure all sensors and components are loaded from the libraries.
4. **Arduino Code**:
- Open the .ino file in Arduino IDE.
- Install LiquidCrystal_I2C library via Library Manager if needed.
- Compile and upload the .hex file to the Arduino in Proteus (or real hardware).
- The code is in the `code/` folder (or main.ino).
5. **Run Simulation**:
- In Proteus, simulate the circuit.
- Test by triggering sensors (e.g., set "TestPin" high in simulation).
- Monitor LCD, LEDs, buzzer, and Serial output.
Screenshots
Circuit diagram in Proteus:

<img width="1465" height="889" alt="propro" src="https://github.com/user-attachments/assets/2c69bf3a-945f-4437-92d8-e96c2923d2f0" />

## Contributing
This is a private project maintained for personal learning and development.
## License
This project is private and not licensed for public use, distribution, or modification.
