---
title: "Traffic Control System"
date: 2021-10-07
url: /Traffic-Control-System/
description:
categories: [Projects]
draft: false
---
## Introduction

Nowadays, the use of private vehicles is very common, so the number of vehicles on the road is increasing exponentially. Roads without supervision or guidance can lead to traffic jams and accidents. 
Traffic lights are signaling devices used to control the flow of traffic. The traffic lights will provide directions to users (drivers and pedestrians) through lights displaying standard colors. The three colors used for traffic lights are (red, yellow and green). This system should be used to control traffic lights to ensure smooth and safe traffic. 

## Project Objective

In this project a traffic light controller system based on Arduino is designed for double pathway. It is a simple implementation of a traffic control management.

## Project appliances

{{< figure src="/images/Traffic-Control-System/Appliance.png" caption="Required Appliances" align="center" >}}


## Methodology

A brief description about the setup and working methods of these two systems is attached below :

### Double pathway Traffic Management
In this case, the traffic control of two opposite Lanes is designed. 6 LEDs (3 for each lane), 2 LCDs, and 4 7-segments are required to design the circuit. A brief discussion on the circuit setup and whole working method is discussed below:
## Circuit Setup:

- 2 LCDs are connected to the Arduino through I2C Buses of respective Slave Address (0x27 and 0x20).  
- 2 counters (1 for each lane) are set by 7-segment to show the interval of different phases.
- 2 pairs of Red, Green, and Yellow are connected to the Arduino to indicate the vehicles of two lanes whether they have to move, stop, or stop their engine for certain period.

### Working Algorithm:
- Both the LEDs and LCDs will indicate respective directions such that, when vehicles in one lane is moving, the other will stop. So, when RED light blinks in first lane, GREEN light blinks on second.
- Pedestrians can move only when the vehicles are stopped otherwise they can go and cross the road. 
- After a particular interval, the green and red lights stops and Yellow light turns on for a certain time. Now, vehicles of first lane have to Stop the engine and vehicles of second lane have to Start them as displayed on the LCD. 
- Finally, Green light blinks on the second lane and indicates its vehicles to move while pedestrians have to stop. On the contrary, Red light on the first lane its pedestrians to move and vehicles to stop.
This whole scenario is repeated simultaneously to control a safe and organized traffic management for 2 pathway.

## Proteus Simulation Diagram

{{< figure src="/images/Traffic-Control-System/simulation.png" caption="Simulation Using Proteus" align="center" >}}

## Code 

```
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd1(0x27, 16, 2);
LiquidCrystal_I2C lcd2(0x20, 16, 2);
byte LUT[] = {0x3F, 0x06, 0x5B, 0x4F, 0x66, 0x6D, 0x7D, 0x07, 0x7F, 0x6F};//0 to 9

#define G1r2 8
#define Y1y2 9
#define R1g2 10
#define C1 11
#define C2 12
int i, j;

void setup() {
  DDRD = 0xFF;
  DDRB = 0xFF;
  lcd1.init();
  lcd1.backlight();
  lcd2.init();
  lcd2.backlight();
}

void loop() {
  for (j = 2; j >= 0; j--)
  {
    lcd1.setCursor(2, 0);
    lcd1.print("Vehicles-GO!");
    lcd1.setCursor(0, 1);
    lcd1.print("Pedestrians-Stop");
    lcd2.setCursor(1, 0);
    lcd2.print("Vehicles-STOP!");
    lcd2.setCursor(1, 1);
    lcd2.print("Pedestrians-Go");
    digitalWrite(Y1y2, LOW);
    digitalWrite(G1r2, HIGH)
for ( i = 9; i >= 0; i--)
    {
      for (int k = 0; k < 100; k++) //delay=(5+5)*100=1000ms
      {
        digitalWrite(C1, LOW);
        digitalWrite(C2, HIGH);
        PORTD = LUT[j];
        delay(5);
        digitalWrite(C1, HIGH);
        digitalWrite(C2, LOW);
        PORTD = LUT[i];
        delay(5);
      }
    }
    lcd1.clear();
    lcd2.clear();
  }
 for ( i = 5; i >= 0; i--)
  {
    lcd1.setCursor(0, 0);
    lcd1.print("Stop The Engine");
    lcd2.setCursor(0, 0);
    lcd2.print("Start The Engine");
    digitalWrite(G1r2, LOW);
    digitalWrite(Y1y2, HIGH);
    for (int k = 0; k < 100; k++)
    {
      digitalWrite(C1, LOW);
      digitalWrite(C2, HIGH);
      PORTD = LUT[0];
      delay(5);
      digitalWrite(C1, HIGH);
      digitalWrite(C2, LOW);
      PORTD = LUT[i];
      delay(5);
    }
    lcd1.clear();
    lcd2.clear();
  }
for (j = 2; j >= 0; j--)
  {
    lcd1.setCursor(0, 0);
    lcd1.print("Vehicles-STOP!");
    lcd1.setCursor(0, 1);
    lcd1.print("Pedestrians-Go");
    lcd2.setCursor(2, 0);
    lcd2.print("Vehicles-GO!");
    lcd2.setCursor(0, 1);
    lcd2.print("Pedestrians-Stop");
    digitalWrite(Y1y2, LOW);
    digitalWrite(R1g2, HIGH);
    for ( i = 9; i >= 0; i--)
    {
      for (int k = 0; k < 100; k++)
      {
        digitalWrite(C1, LOW);
        digitalWrite(C2, HIGH);
        PORTD = LUT[j];
        delay(5);
        digitalWrite(C1, HIGH);
        digitalWrite(C2, LOW);
        PORTD = LUT[i];
        delay(5);
      }
    }
    lcd1.clear();
    lcd2.clear();
  }
for ( i = 5; i >= 0; i--)
  {

    lcd1.setCursor(0, 0);
    lcd1.print("Start The Engine!");
    lcd2.setCursor(0, 0);
    lcd2.print("Stop The Engine");
    digitalWrite(R1g2, LOW);
    digitalWrite(Y1y2, HIGH);
    for (int k = 0; k < 100; k++)

    {

      digitalWrite(C1, LOW);
      digitalWrite(C2, HIGH);
      PORTD = LUT[0];
      delay(5);
      digitalWrite(C1, HIGH);
      digitalWrite(C2, LOW);
      PORTD = LUT[i];
      delay(5);

    }
    lcd1.clear();
    lcd2.clear();

  }
}


```

## Project Implemtation

- The traffic light controller in this system can be implemented practically and could be expanded further
- This traffic light controller includes a crosswalk signaling system.
-  Can be used in narrow junction point places such as “Old Dhaka” also in local housings of Dhaka. 
- Underdeveloped countries can implement this at a low cost and can utilize their manpower of traffic police in other sectors. 

## Limitation
- In case of port shortage, Arduino MEGA can be used
- Pedestrian input wasn’t considered
- In the time of maintenance alternative ways should be considered

## Conclusion 

In the following project, we tried to demonstrate the traffic control management system for a two way traffic. We implemented the circuit both in Protues and in hardware. We have used 7 Segment display for countdown and LCD display for indicating the traffic signs to both the pedestrians and the drivers. While implementing the project in hardware we faced some difficulties i.e. we could not use two LCDs due to having similar I2C slave address. This issue was not faced in proteus. If we implement this project in real life it will be very much cost efficient due to simple structure and installation. Any kind of traffic system won’t be fruitful unless people follow the rules.

