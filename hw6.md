1. Make "hw6" directory and  create python files named as before
2. problems

    Now we will learn how to turn an LED on/off using a push button, 
which is used as a GPIO input from Raspberry Pi GPIO. A push button connection is diaplayed in the following figure:

<img src="imgs/push_button.jpg" alt="push button">

Our hardware wiring is simple. You simply connect the LED to GPIO23 from 
Raspberry Pi. The push button is connected to Raspberry Pi GPIO on GPIO24. 
The complete hardware wiring can be seen in the following figure:

<img src="imgs/button_led.jpg" alt="hardware wiring">

Furthermore, you can write a Python program to read the push button's state. If you 
press the push button, the program will turn on the LED. Otherwise, it will turn off 
the LED. 
# Code for turning the LED on/off using a push button
import RPi.GPIO as GPIO

# Set up GPIO
GPIO.setmode(GPIO.BCM)
GPIO.setup(23, GPIO.OUT)

# Read the push button state
button_state = GPIO.input(24)

# Turn on/off the LED based on the button state
if button_state == GPIO.HIGH:
    GPIO.output(23, GPIO.HIGH)
else:
    GPIO.output(23, GPIO.LOW)

# Clean up GPIO
GPIO.cleanup()
