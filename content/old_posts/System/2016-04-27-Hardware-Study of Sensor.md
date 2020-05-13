+++
title = "Hardware Sensors"
date = 2016-04-27
weight = 100
tags = ["sensors"]
+++

{% include toc %}

To develope products using sensors, it is essential to have a knowledge of variety of sensors. This page lists type of sensors, demonstrates about its characteristics and how they can be applied to the real world.

# Distance Sensor

|             |  Ultrasonic           | Infrared             | Laser    |
|-------------| --------------------- | -------------------- |--------- |
|**Method**   | Sound                 | Light                | Light    |
|**Frequency**| High                  | Low                  | -        |
|**Cons**     | distance mesurement | Object detection | Accuracy |
|**Pros**     | Environmental factors (observe signal by soft objects) | inaccurate distance measurement | Cost     |


*Laser beam is often used to measure long distance.

## Ultrasonic

Ultrasonic sensors often enhances **distance measurement** to the object very accurately.

| PARTS          | Datasheet |
|----------------|-----------|
| parallax: PING |[![PING](/images/adobe_PDF_file_icon_32x32.png)](https://www.parallax.com/sites/default/files/downloads/28015-PING-Sensor-Product-Guide-v2.0.pdf) |
| HC-SR04 (Similar to PING but cheaper) |[![HC-SR04](/images/adobe_PDF_fi	le_icon_32x32.png)](http://www.micropik.com/PDF/HCSR04.pdf) |





## Infrared

One of the great features of using infrared sensor is thermal emission. This enhances object come and go by thermal emission. However, thermal emission should be taken carefully depends on environmental factors. the sensor only able to detect object within a range but cannot accurately sense distnace.

| PARTS          | Datasheet |
|----------------|-----------|
| Infrared Sensor Switch |[![Foo](/images/adobe_PDF_file_icon_32x32.png)]() |
| Compound Eye  |[![Foo](/images/adobe_PDF_file_icon_32x32.png)]() |

Compound eye sensor is consisted of a number of infrared-sensitive transistor and LED

**Types:**

- Passive infrared sensor:
Senses thermal radiation transferred to infrared.


- Active infrared distance sensor:
Detects returned sent light from infrared. This notifies distance in a range.

**Applications:**

Hand Dryer, Water tab, rubish bin.

# Smoke and Gas Sensor

There are variety of sensors which senses different kind of chemicals as show below.
MQ2 is one of the cheapest Analog sensor used among developers.

| PARTS          | Application | Datasheet |
|----------------|------|-----------|
| MQ-2           | LPG<br> I-butane<br> Propane<br> Methane<br> Alcohol<br> Hydrogen<br> Smoke<br> | [![Foo](/images/adobe_PDF_file_icon_32x32.png)](https://www.seeedstudio.com/depot/datasheet/MQ-2.pdf)                            |
| MQ-3, MQ-303A  | Alcohol Checker<br> Breathalyser                              | [![Foo](/images/adobe_PDF_file_icon_32x32.png)](https://www.sparkfun.com/datasheets/Sensors/MQ-3.pdf) |
| MQ-4           | CH4<br> Natural Gas  |[![Foo](/images/adobe_PDF_file_icon_32x32.png)](https://www.sparkfun.com/datasheets/Sensors/Biometric/MQ-4.pdf) |
| MQ-7           | Carbox Monoxide | [![Foo](/images/adobe_PDF_file_icon_32x32.png)](https://www.sparkfun.com/datasheets/Sensors/Biometric/MQ-7.pdf) |
| MQ-8           | Hydrogen | [![Foo](/images/adobe_PDF_file_icon_32x32.png)](https://dlnmh9ip6v2uc.cloudfront.net/datasheets/Sensors/Biometric/MQ-8.pdf) |
| MQ-9           | Carbon Monoxide<br> CH4<br> LPG | [![Foo](/images/adobe_PDF_file_icon_32x32.png)](https://solarbotics.com/download.php?file=2274) |


# Switches
Touch Sensors
	- work the same way as the buttons which need voltage and ground lines.

| Types                   |
|-------------------------|
| Buttons                 |
| Microswitch             |
| Potentiometer           |
| QT 113 - Touch Sensor   |
| FlexiForce - analogRead |
| Touch Sensors


# Movement

| Types            | Notes                                                            |
|------------------|------------------------------------------------------------------|
| Tilt Sensor      | adc                                                              |
| vibration sensor | adc                                                              |
| rotary encoder   | counts the rotation of the object                                |
| Thumbstick       | used in joystick of playstation. two types: 3 pins and 5 pins    |
| PIR sensor       | various range of products depends on sensing distance and angle. |


# Light

| Types                          | Notes                 |
|--------------------------------|-----------------------|
| Flame sensor                   | KY-026                |
| Light-dependent resistor (LDR) | visible ray resistors |                                         
| Line detection (line tracer)   |                       |
| color detection                |                       |
| color display (RGB LED)        |                       |
