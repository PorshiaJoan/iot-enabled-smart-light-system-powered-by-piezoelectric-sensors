Abstract
This project aims to develop an IoT-enabled smart lighting system powered by piezoelectric sensors embedded in floor tiles. The system converts mechanical energy generated by footsteps into electrical energy, which powers LED lights. To enhance energy efficiency, the system includes a smart lighting module that adapts to environmental conditions, such as ambient light, to minimize energy wastage. A 5081 microcontroller is used for processing sensor data and managing the system's operations, replacing the Arduino Uno typically used in such applications. The project also features a mobile app for user control and data monitoring, promoting sustainable energy practices in residential and educational settings.
Proposed Project Overview

Electricity Generation Module
   
Piezoelectric Sensors: These sensors are embedded in floor tiles to convert the mechanical pressure from footsteps into electrical energy. The generated electricity is low in voltage and intermittent.

Rechargeable Battery: The low-voltage electrical energy is stored in a rechargeable battery, ensuring a continuous power supply even when the energy generation is sporadic.

Converter: A DC-DC converter boosts the low and inconsistent voltage from the piezoelectric sensors to a level suitable for charging the battery and powering the LED lights.

LED Lights: The stored energy in the battery is used to power LED lights, ensuring energy-efficient lighting in classrooms or homes.

 Energy Conservation Module
   
5081 Microcontroller: The 5081 microcontroller processes data from various sensors and controls the system's operations. It manages the energy flow between the piezoelectric sensors, battery, and lights.
   
LDR Sensor (Light Dependent Resistor): This sensor detects ambient light levels. The microcontroller uses this data to determine whether the lights need to be on or off, ensuring energy is conserved during daylight hours.

Relay Switch: Controlled by the microcontroller, the relay switch regulates the power flow to the LED lights based on the LDR sensor's input, enabling real-time energy conservation.

Mobile App Module
   
System Control: The mobile app allows users to manually override the automatic settings, giving them direct control over the lighting system.

Data Analysis: The app provides insights into the energy generation and consumption patterns, helping users optimize the system's performance.

User Notifications: The app can send alerts regarding energy usage, system performance, or when maintenance is required, ensuring the system operates efficiently.

System Integration and Workflow

The piezoelectric sensors generate electricity, which is stored in the rechargeable battery after passing through the converter.

The 5081 microcontroller continuously monitors ambient light using the LDR sensor and makes decisions about whether to power the LED lights via the relay switch.

The microcontroller also interfaces with the mobile app, allowing users to monitor and control the system. The app processes data from the microcontroller, providing users with real-time information about energy generation and usage.

This project represents a sustainable approach to energy management, leveraging kinetic energy from footsteps and optimizing its use through smart IoT technologies.
Connections for the 8051 Microcontroller

Components:
8051 Microcontroller

Piezoelectric Sensor

Rechargeable Battery

DC-DC Converter

LDR Sensor (Light Dependent Resistor)

Relay Switch

LED Lights

Mobile Interface (Optional, for UART communication)
