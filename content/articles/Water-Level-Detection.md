---
title: "Water Level Detection"
date: 2020-09-19
url: /Water-Level-Detection/
description:
categories: [Projects]
draft: false
---

## Introduction
***
The Water Level Indicator employs a simple mechanism to detect and indicate the water level in an overhead tank or any other water container. The sensing is done by using water sensor . There are a lot of water sensor models available in the market like water sensor(china) model SEN-00235, Grove- water sensor model SEN-00042, water flow sensor model SEN-00043 etc. For this project we’ll use the water sensor (china) model SEN-00235 because it’s cheap & economical. The arduino uno is used for the project to run through coding. Water level indicator will inform the user about different level of water that a container is containing i.e, high/ average/ low . there is also a buzzer system attached to the circuit to let an user know when the container is full. 

## Equipment
***

1. Arduino Uno :  Arduino uno is a microcontroller board based on the ATmega328P (datasheet). It has 14 digital input/output pins (of which 6 can be used as PWM outputs), 6 analog inputs, a 16 MHz ceramic resonator (CSTCE16M0V53-R0), a USB connection, a power jack, an ICSP header and a reset button.

2. Breadboard : A  breadboard is a solderless device for temporary prototype with electronics and test circuit designs. Most electronic components in electronic circuits can be interconnected by inserting their leads or terminals into the holes and then making connections through wires where appropriate.

3. LED lights 3 (red, green, yellow) : In the simplest terms, a light-emitting diode (LED) is a semiconductor device that emits light when an electric current is passed through it
4. Buzzer (x1) : A buzzer or beeper is an audio signaling device, which may be mechanical, electromechanical, or piezoelectric (piezo for short). Typical uses of buzzer & beepers include alarm devices, timers, and confirmation of user input such as a mouse click or keystroke.

5. Jumper wires : Jumper wires are simply wires that have connector pins at each end, allowing them to be used to connect two points to each other without soldering.

6. Water level sensor (SEN-00235) : Water level sensor is an easy-to-use, cost-effective high level/drop recognition sensor, which is obtained by having a series of parallel wires exposed traces measured droplets/water volume in order to determine the water level. Easy to complete water to analog signal conversion and output analog values can be directly read development board to achieve the level alarm effect.

7. 220 ohms resistor (x3) : A resistor is a passive two-terminal electrical component that implements electrical resistance as a circuit element. In electronic circuits, resistors are used to limit current flow, to adjust signal levels, bias active elements, and terminate transmission lines among other uses.

## Connection
***

{{< figure src="/images/water-level-detection/Schematic.jpg" caption="Schematic Diagram" align="center" >}}

{{< figure src="/images/water-level-detection/connection.png" caption="Schematic Diagram" align="center" >}}

## Procedure 
***
- Firstly we connect the arduino with laptop or pc and then using  power cable . Then we upload the prepared code using Arduino IDE. 

- Secondly, we select 3 different color LED ( Red, Green & Yellow ) . Then we  connect the cathode of each led to power rail(blue rail) on breadboard which would be the ground supply and we connect the anode of LED's to different nodes . After that we select 220 ohm resistance and connect them with the LEDs in series connection. Now we will connect those LEDs with Arduino . Red LED is connected with the digital pin 13 , yellow with digital pin 12 and green with digital pin 11.  For this connection we have used male to male jumper wire.   
Thirdly, We now select the sensor and connect the S pin with arduino’s  A_0  pin , sensor’s  positive pin will go with arduino’s  5V pin and lastly negative pin will go with arduino’s ground. All this connection was made with male to female jumper wire. 

- Lastly, will connect the buzzer with Digital pin 8 and ground the other leg of the buzzer. Now the whole circuit is complete to run. 
Now we will take a glass and put the sensor in the glass. And give a power supply to the arduino. Then we will slowly pour the water. As we pour the water, when the water is touching the sensor in its lower part then the red light will turn on. As we pour the water when it touches the middle part of the sensor yellow LED will turn on and similarly when the water level reaches the upper part then the green LED will turn on. And every level has its own value to determine the led on off.

## Code
***
```
int level;
const int analog_0=0;
int l1=13;
int l2=12;
int l3=11;
int l4=10;
 
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  pinMode(l1,OUTPUT);
  pinMode(l2,OUTPUT);
  pinMode(l3,OUTPUT);
  pinMode(l4,OUTPUT);
 pinMode(8,OUTPUT);
}

void loop() {
  
  // put your main code here, to run repeatedly:
level=analogRead(analog_0);
Serial.println(level);
if(level>500&&level<550)
{ digitalWrite(l1, HIGH);
  digitalWrite(l2, LOW);
   digitalWrite(l3, LOW);
    digitalWrite(l4, LOW);
  
  }
else if(level>600&&level<620)
 {
  digitalWrite(l1, LOW);
  digitalWrite(l2, HIGH);
   digitalWrite(l3, LOW);
    digitalWrite(l4, LOW);
  
  }

else if(level>620&&level<630)
 {
  digitalWrite(l1, LOW);
  digitalWrite(l2, LOW);
   digitalWrite(l3, HIGH);
    digitalWrite(l4, LOW);
  
  }

else if(level>630&&level<650)
 {
  digitalWrite(l1, LOW);
  digitalWrite(l2, LOW);
   digitalWrite(l3, LOW);
    digitalWrite(l4, HIGH);
    digitalWrite(8, HIGH);
  }
}
``` 

## Working Principle
***
There are several type of sensors detection but the most simple detects the presence of water by its conductivity.  Tap water contains dissolved ions that permit conduct of electricity (pure distilled water won’t conduct electricity). 

{{< figure src="/images/water-level-detection/levelofwater.jpg" caption="Water Level" align="center" >}}

The sensor is generally a set of parallel wires, one set connected to a positive power source such as a battery and the other to a negative source. The two sets of wires do not touch, so no current flows between them. But when the sensor gets wet, a current will flow between the positive and negative wires. In this process, if resistance is high, current flow will be low & vice versa. The more we immerse the sensor the more the flow of current will be obtained cause as we’re immersing the sensor the value of resistance getting decreased.

 By this method it sends signal to the arduino . Aduino has two parts. One is the hardware another part is the software. Hardware part takes the signal from the sensor and that received value is run through the code to give indication for our output. Now arduino sends signal to the bread board to turn on the required light for high/average/low water level indication. And if the water level exceeds the high level mark then the buzzer will turn on automatically for the arduino coding function.

 ## Applications and Usage
 ***

 The water level indicator is used in many sectors. Though it seems to be a very simple project, it plays a vital role in water saving. Some of the main applications are
-	The water level indicator is used in hotels and home apartments, in commercial complexes and in factories.
-	It is used in residential and commercial swimming pools.
-	It is used as fuel level indicators in vehicles.
-	It is used in water tanks to indicate the water level.
-	It is also used in steam level monitoring.


The water level indicator can be used in many other ways such as
-	To start and stop water pumps (We didn’t use the code here).
-	In open wells.
-	Where cooling towers are used.
-	Tsunami warning and sea level monitoring and any other ways where water levels need to be monitored and controlled.

## Advantages and Disadvantages
***

**Advantages:** There are many advantages of water level indicators. Some of them are described below.

1.	Maintenance: Water level indicators need a very little maintenance. Anybody can hear the buzzer when the water reaches maximum level and control.

2.	Installation: it is easy to install and everyone can understand how to use it. It has a compact and good design.

3.	Money saver: It helps save money by limiting the waste of water and electricity. We can easily switch off the power supply when we hear the buzzer. So there’s no wastage of water and electricity. Again, for automatic indicators/controllers it limits the unnecessary water/electricity usage and overtime the money saved is quite substantial.

4.	Power saver: The water level indicator is ideal at saving power. Usually, regulating water levels can consume electricity and wastewater. However, with automatic controllers, the electricity usage is limited as well as less water needed to regulate supply.

5.	Water maximization: It can maximize the water used in appropriate time while automatically lessening the water used at idle time.

**Disadvantages:** There are some disadvantages of water level indicators.
1.	It needs to be replaces after a year or two.
2.	There is no guarantee of the LED lights.
3.	The electronic devices may be damaged easily.
4.	This project may not be able to handle high power.

## Discussion 

****
In the following project we’ve tried to demonstrate water level indication through arduino uno and water sensor. The project was done very carefully so that none of the equipments get damaged  and the circuit setup was done with proper caution and safety . This project and it’s function related to it is used worldwide specially in green house to measure the moisture, rain level detection, fuel level detection in tanker etc. Though this project has got some drawbacks but still it is an economical and environment friendly project.