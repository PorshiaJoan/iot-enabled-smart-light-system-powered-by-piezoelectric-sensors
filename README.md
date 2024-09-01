# iot-enabled-smart-light-system-powered-by-piezoelectric-sensors
Abstract
This project aims to develop an IoT-enabled smart lighting system powered by piezoelectric sensors embedded in floor tiles. The system converts mechanical energy generated by footsteps into electrical energy, which powers LED lights. To enhance energy efficiency, the system includes a smart lighting module that adapts to environmental conditions, such as ambient light, to minimize energy wastage. A 5081 microcontroller is used for processing sensor data and managing the system's operations, replacing the Arduino Uno typically used in such applications. The project also features a mobile app for user control and data monitoring, promoting sustainable energy practices in residential and educational settings.
Proposed Project Overview
1. Electricity Generation Module
•	Piezoelectric Sensors: These sensors are embedded in floor tiles to convert the mechanical pressure from footsteps into electrical energy. The generated electricity is low in voltage and intermittent.
•	Rechargeable Battery: The low-voltage electrical energy is stored in a rechargeable battery, ensuring a continuous power supply even when the energy generation is sporadic.
•	Converter: A DC-DC converter boosts the low and inconsistent voltage from the piezoelectric sensors to a level suitable for charging the battery and powering the LED lights.
•	LED Lights: The stored energy in the battery is used to power LED lights, ensuring energy-efficient lighting in classrooms or homes.
2. Energy Conservation Module
•	5081 Microcontroller: The 5081 microcontroller processes data from various sensors and controls the system's operations. It manages the energy flow between the piezoelectric sensors, battery, and lights.
•	LDR Sensor (Light Dependent Resistor): This sensor detects ambient light levels. The microcontroller uses this data to determine whether the lights need to be on or off, ensuring energy is conserved during daylight hours.
•	Relay Switch: Controlled by the microcontroller, the relay switch regulates the power flow to the LED lights based on the LDR sensor's input, enabling real-time energy conservation.
3. Mobile App Module
•	System Control: The mobile app allows users to manually override the automatic settings, giving them direct control over the lighting system.
•	Data Analysis: The app provides insights into the energy generation and consumption patterns, helping users optimize the system's performance.
•	User Notifications: The app can send alerts regarding energy usage, system performance, or when maintenance is required, ensuring the system operates efficiently.
System Integration and Workflow
•	The piezoelectric sensors generate electricity, which is stored in the rechargeable battery after passing through the converter.
•	The 5081 microcontroller continuously monitors ambient light using the LDR sensor and makes decisions about whether to power the LED lights via the relay switch.
•	The microcontroller also interfaces with the mobile app, allowing users to monitor and control the system. The app processes data from the microcontroller, providing users with real-time information about energy generation and usage.
This project represents a sustainable approach to energy management, leveraging kinetic energy from footsteps and optimizing its use through smart IoT technologies.
Connections for the 8051 Microcontroller
Components:
•	8051 Microcontroller
•	Piezoelectric Sensor
•	Rechargeable Battery
•	DC-DC Converter
•	LDR Sensor (Light Dependent Resistor)
•	Relay Switch
•	LED Lights
•	Mobile Interface (Optional, for UART communication)
Basic Connections:
1.	Power Supply:
o	Vcc (Pin 40) → +5V Power Supply.
o	GND (Pin 20) → Ground.
2.	Piezoelectric Sensor to ADC (if needed):
o	The piezoelectric sensor's output is connected to an ADC (Analog-to-Digital Converter) if the 8051 doesn't have an onboard ADC.
o	ADC Data Out → P1.0 to P1.7 (depending on how many bits your ADC uses).
3.	LDR Sensor to ADC:
o	LDR connected in a voltage divider configuration with a fixed resistor.
o	The junction between the LDR and resistor is connected to an ADC channel.
o	ADC Data Out → P1.0 to P1.7 (same port or different based on availability).
4.	Relay Switch:
o	Relay IN → P2.0 (or any other GPIO pin on the 8051).
o	Relay GND → Ground.
o	Relay Vcc → +5V.
5.	LED Lights:
o	LED Anode → Relay Output (NO pin).
o	LED Cathode → Ground.
6.	DC-DC Converter:
o	Input: Piezoelectric sensor output.
o	Output: Connected to Rechargeable Battery.
7.	UART Communication (Optional for Mobile App Interface):
o	TXD (Pin 11) → RX of the serial communication module.
o	RXD (Pin 10) → TX of the serial communication module.
o	GND → Ground.
Keil C Code for the 8051 Microcontroller
#include <reg51.h>

sbit relay = P2^0;        // Relay connected to P2.0
sbit ldr = P1^0;          // LDR sensor connected to P1.0 (ADC output)

void delay(unsigned int time) {
    unsigned int i, j;
    for(i = 0; i < time; i++)
        for(j = 0; j < 1275; j++);
}

void main() {
    relay = 0;  // Initially, the relay is off
    
    while(1) {
        if (ldr == 1) {  // If it's dark (depending on your circuit logic)
            relay = 1;   // Turn on the relay (which turns on the lights)
        } else {
            relay = 0;   // Turn off the relay
        }
        
        delay(100);  // Small delay for debouncing
    }
}
Executing the Code in Keil
1.	Open Keil uVision:
o	Create a new project and select the 8051 microcontroller from the device database.
2.	Write/Import the Code:
o	Copy the provided C code into a new file and save it with a .c extension.
o	Add this file to your project.
3.	Set Up Target Options:
o	Go to Project → Options for Target and configure the oscillator frequency and other settings as per your hardware.
4.	Compile the Code:
o	Click on the Build button (or press F7) to compile the code. Ensure there are no errors.
5.	Generate Hex File:
o	Ensure that the option to generate a HEX file is enabled under Options for Target → Output tab.
6.	Load the Code into the 8051:
o	Use a programmer or an emulator to load the generated .hex file into your 8051 microcontroller.
7.	Test the System:
o	Power the system and observe the behavior of the relay and LED lights in response to the LDR sensor.




