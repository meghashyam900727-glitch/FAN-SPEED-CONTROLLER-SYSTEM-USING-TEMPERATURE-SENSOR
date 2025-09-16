
# FAN-SPEED-CONTROLLER-SYSTEM-USING-TEMPERATURE-SENSOR
# EXP 1(A) FAN SPEED CONTROLLER SYSTEM USING TEMPERATURE SENSOR

# Aim:
	To measure the Temperature using DHT11/DHT22/TMP36  sensor with Arduino UNO Board/ESP-32 using Tinker CAD.

# Hardware / Software Tools required:
	PC/ Laptop with Internet connection
    Tinker CAD tool (Online)
	Arduino UNO Board/ESP-32
	Temperature Sensor (DHT11/DHT22/TMP36)

# Circuit Diagram:
<img width="1920" height="1080" alt="Annotation 2025-09-16 010409" src="https://github.com/user-attachments/assets/be1bc95b-c57d-41e0-aee7-e9180f25bdea" />

---
To upload
--

# Procedure // Modify the procedure based on your circuit

Step 1: Set Up the Tinkercad Environment
1.	Log in to Tinkercad: Open Tinkercad in your web browser and log in to your account.
2.	Create a New Circuit: In the Tinkercad dashboard, click on "Circuits" and then select "Create New Circuit."
Step 2: Add Components to the Circuit
1.	Arduino Uno: Drag an Arduino Uno board from the components panel onto the workspace.
2.	TMP36 Sensor: Search for the TMP36 sensor in the components panel and drag it into the workspace.
3.	Breadboard: Drag a small breadboard to the workspace to help with wiring connections.
4.	Resistor (Optional): A resistor may not be necessary for this simple setup, but you can include it for more accurate readings.
5.	Wires: Use wires to connect the components.

Step 3: Connect the TMP36 Sensor to the Arduino
1.	TMP36 Pins:
o	Vout (Middle Pin): Connect this to an analog input pin on the Arduino (e.g., A0).
o	GND (Right Pin): Connect this pin to the ground (GND) on the Arduino.
o	Vs (Left Pin): Connect this to the 5V pin on the Arduino.
2.	Breadboard Wiring:
o	TMP36 Vout (Middle Pin) to Arduino A0: Use a wire to connect the middle pin (Vout) of the TMP36 sensor to the A0 analog input pin on the Arduino.
o	TMP36 GND (Right Pin) to Breadboard GND Rail: Connect the GND pin of the TMP36 sensor to the ground rail of the breadboard.
o	TMP36 Vs (Left Pin) to Breadboard 5V Rail: Connect the Vs pin of the TMP36 sensor to the 5V rail of the breadboard.
o	Arduino GND to Breadboard GND Rail: Connect a wire from the Arduino GND pin to the ground rail on the breadboard.
o	Arduino 5V to Breadboard 5V Rail: Connect a wire from the Arduino 5V pin to the power rail on the breadboard.
Step 4: Write the Arduino Code
1.	Code Editor: Click on the "Code" button at the top of the Tinkercad workspace to open the code editor.
2.	Set the Coding Mode: Ensure the editor is in "Text" mode to write your code in C/C++.
3.	Enter the Code: Write the following code to read the temperature from the TMP36 sensor
Step 5: Simulate the Circuit
1.	Start Simulation: Click the "Start Simulation" button at the top of the workspace to run the circuit and code.
2.	Monitor Output: Open the serial monitor by clicking the "Serial Monitor" button to view the temperature readings in both Celsius and Fahrenheit.
Step 6: Troubleshoot and Refine
1.	Check Connections: Ensure that all connections are made correctly on the breadboard and the Arduino.
2.	Adjust Code: If needed, tweak the code to improve accuracy or change the format of the output.
Step 7: Save Your Work
1.	Stop Simulation: Click "Stop Simulation" to end the simulation.
2.	Save the Circuit: Click "Save" to keep your circuit design and code for future use.


# Program
---
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);  // I2C address might be 0x3F

const int potPin = A2;
const int motorPin = 9;
const int ledPin = 13;

int speedVal = 0;

void setup() {
  pinMode(motorPin, OUTPUT);
  pinMode(ledPin, OUTPUT);

  lcd.init();
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("Fan Controller");
}

void loop() {
  int potValue = analogRead(potPin);      // 0–1023
  speedVal = map(potValue, 0, 1023, 0, 255);  // Map to PWM (0–255)

  analogWrite(motorPin, speedVal);  // DC motor speed
  analogWrite(ledPin, speedVal);    // LED brightness

  int speedPercent = map(speedVal, 0, 255, 0, 100);

  lcd.setCursor(0, 1);
  lcd.print("Speed: ");
  lcd.print(speedPercent);
  lcd.print(" %   ");  // Extra spaces to clear old text

  delay(300);
}

---
To upload
<img width="1920" height="1080" alt="Annotation 2025-09-16 010409" src="https://github.com/user-attachments/assets/5752736d-92b7-47a7-a193-d7bc5e55a96e" />

# Result
<img width="1920" height="1080" alt="Annotation 2025-09-16 010924" src="https://github.com/user-attachments/assets/be52f729-296a-4a3a-b229-c2c4af401649" />
output
https://github.com/user-attachments/assets/15188ece-0db1-44f3-bb30-367e9b8ae167


