# 4-Bit-Binary-Counter-Embedded-C

Overview

This project demonstrates a 4-Bit Binary Counter using the Arduino Uno (ATmega328P) and Embedded C with register-level programming. The LEDs display binary values from 0000 to 1111, representing decimal numbers from 0 to 15.

The project was implemented using direct port manipulation with DDRD and PORTD registers instead of Arduino functions like digitalWrite(). This helped in understanding low-level Embedded C concepts and GPIO control in microcontrollers.

Components Required:
--> Arduino Uno R3
--> 4 LEDs
--> 4 × 220Ω Resistors
--> Breadboard
--> Jumper Wires

Circuit Connections:

LED	AVR Pin	Arduino Pin
LED1	PD2	2
LED2	PD3	3
LED3	PD4	4
LED4	PD5	5

Embedded C Code:
void setup()
{
    DDRD |= 0b00111100;
}

void loop()
{
    for(int count = 0; count <= 15; count++)
    {
        PORTD &= ~0b00111100;

        PORTD |= (count << 2);

        delay(500);
    }
}

Working Principle:

Pins PD2 to PD5 are configured as OUTPUT using the DDRD register.
The program counts from 0 to 15 using a for loop.
Each decimal number is converted into binary automatically.
The binary value is shifted left by 2 positions because the LEDs are connected from PD2 to PD5.
PORTD updates the LEDs to display the binary pattern.
The process repeats continuously.

Concepts Learned:
--> Embedded C Programming
--> Register-Level GPIO Control
--> Bitwise Operations
--> Binary Number Representation
--> Left Shift Operator (<<)
--> AVR Port Manipulation
--> Looping and Timing Control

Output:
The LEDs display binary counting sequence:
0000
0001
0010
0011
0100
...
1111
