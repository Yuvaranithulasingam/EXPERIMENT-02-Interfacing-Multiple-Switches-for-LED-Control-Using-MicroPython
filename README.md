# EXPERIMENT-02-Interfacing-Multiple-Switches-for-LED-Control-Using-MicroPython

### NAME:YUVARANI T
### DEPARTMENT:CSE(IOT)
### ROLL NO:212222110057
### DATE OF EXPERIMENT:

## AIM
To interface multiple switches with the Raspberry Pi Pico and control LEDs using MicroPython.

## APPARATUS REQUIRED

Raspberry Pi Pico

2 Push Button Switches

2 LEDs (Light Emitting Diodes)

330Ω Resistors

Breadboard

Jumper Wires

USB Cable

## THEORY

FIGURE-01: RASPBERRY PI PICO PINOUT DIAGRAM

Raspberry Pi Pico is a microcontroller board based on the RP2040 chip. It supports MicroPython, making it suitable for IoT and embedded applications. The Raspberry Pi Pico is a compact microcontroller board featuring a 40-pin layout, including power, ground, GPIO, and communication interface pins. It operates with a dual-core ARM Cortex-M0+ processor and supports MicroPython and C/C++ programming.

The power pins include VBUS (5V from USB), VSYS (1.8V to 5.5V input), 3V3(OUT) (regulated 3.3V output), and multiple ground (GND) connections. The board offers 26 multi-purpose GPIO pins (GP0 to GP28), which can be used for digital input, output, PWM, and communication interfaces such as I2C, SPI, and UART. It also features three analog-to-digital converter (ADC) pins (GP26, GP27, GP28), used for reading analog sensor values, along with an ADC_VREF pin to set the reference voltage.

For communication, I2C (SDA, SCL), SPI (MOSI, MISO, SCK), and UART (TX, RX) interfaces are mapped across different GPIO pins, allowing seamless connectivity with sensors and peripherals. All GPIO pins support PWM (Pulse Width Modulation), making it useful for motor control, LED brightness adjustment, and sound applications. The BOOTSEL button enables USB mass storage mode for firmware flashing, while the DEBUG pins (SWD interface) provide debugging capabilities. With its low power consumption, flexible GPIO options, and rich interface support, the Raspberry Pi Pico is widely used for IoT, embedded systems, robotics, and automation projects.

WORKING PRINCIPLE

The switches are connected as inputs to GPIO pins of the Pico.

The LEDs are connected as outputs.

A MicroPython script reads the switch states and controls the LEDs accordingly.

### CIRCUIT DIAGRAM
 
 ![image](https://github.com/user-attachments/assets/1c7234b9-5041-4156-94b8-0b846adb6b8e)
    Figure-01 circuit diagram of digital input interface 


Connect switch 1 to GP2 and switch 2 to GP3.

Connect LED 1 to GP14 via a 330Ω resistor.

Connect LED 2 to GP17 via a 330Ω resistor.

Connect the other terminals of the switches to GND.

## PROGRAM (MicroPython)
```
from machine import Pin
from time import sleep

switch1 = Pin(2,Pin.IN)
switch2 = Pin(3,Pin.IN)

led1 = Pin(15,Pin.OUT)
led2 = Pin(16,Pin.OUT)
while True:
    sw1_state = switch1.value()
    sw2_state = switch2.value()

    print("Switch 1 State:",sw1_state)
    print("Switch 2 State:",sw2_state)
    led1.value(0)

    if sw1_state==1 and sw2_state==1:
        led1.value(0)
        led2.value(0)

    elif sw1_state==1:
        led1.value(1)
        sleep(0.5)
        led1.value(0)
        led2.value(0)

    elif sw2_state==1:
        led1.value(0)
        led2.value(1)
        sleep(0.5)
        led2.value(0)

    sleep(0.5)
```
## OUTPUT

### CIRCUIT CONNECTION:

![image](https://github.com/user-attachments/assets/baeeb437-eeec-460f-ae38-0d45ae9b7eb6)

### SWITCH 1 ON:

![image](https://github.com/user-attachments/assets/105652c0-c204-4bdc-bcc0-c6684cf3fc24)

### SWITCH 2 ON:

![image](https://github.com/user-attachments/assets/57c5772f-d39d-4b1c-8b77-5cddc0f2f611)

### BOTH SWITCH ON:

![image](https://github.com/user-attachments/assets/4e680f6d-8c08-446e-b6ad-cca91f4d0d9c)

### TIMING DIGAGRAM:

![image](https://github.com/user-attachments/assets/a36cfd27-7de7-411b-bd98-4fff64753c20)

## RESULTS

The multiple switches connected to the Raspberry Pi Pico successfully controlled the LEDs based on their states, confirming the proper interfacing of digital inputs and outputs.

