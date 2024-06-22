# Gas_level_monioring-Raspberry-pi
This project demonstrates a simple application of a gas sensor connected to a Raspberry Pi. The system detects the presence of gas and outputs a message indicating whether gas is present or not.This project involves using a MQ2 gas sensor with a Raspberry Pi to detect the presence of gas in the environment. When gas is detected, the system outputs a message indicating the presence of gas. This can be useful for safety applications and environmental monitoring.

<p align="center">
  <img src="https://github.com/Iswarya-Singaram/Gas_level_monioring-Raspberry-pi/assets/145309713/84e55410-d126-4edb-a8f5-464adb00a903" width="500" height="300">
</p>

## Components
Raspberry Pi 4 or 5<br>
Gas Sensor (e.g., MQ-2, MQ-3)<br>
Breadboard and Jumper wires<br>

<p align="center">
  <img src="https://github.com/Iswarya-Singaram/Gas_level_monioring-Raspberry-pi/assets/145309713/aa9f0152-4d12-48b3-8013-cb64ce76effb" width="500" height="500">
</p>

## Hardware Setup
1. VCC to 3.3V
2. GND to GND
3. D0 to GPIO-7 (digital output pin on Raspberry pi)

## Circuit Diagram

<p align="center">
  <img src="https://github.com/Iswarya-Singaram/Gas_level_monioring-Raspberry-pi/assets/145309713/4bccc842-d9b1-42a1-ae1a-a446f35ce202" width="500" height="300">
</p>

## Software Setup
1.Booting the Raspberry Pi OS

1. If you have already booted your Raspberry Pi and have the OS running, skip to the next step. <br>
2. If not, refer to the following repository https://github.com/Iswarya-Singaram/Raspberry-Pi-Booting-and-VNC-Viewer-Setup for instructions on how to install and boot the OS and viewing the Raspberry Pi via VNC <br>
3. Once connected to your Raspberry Pi, open the Terminal.
   
<p align="center">
  <img src="https://github.com/Iswarya-Singaram/Gas_level_monioring-Raspberry-pi/assets/145309713/3bf4ecd9-acda-439c-b9d2-cd89ef0cf138" width="500" height="300">
</p>

4. Download the necessary libraries
~~~
sudo apt-get install python3-rpi.gpio
~~~

If python3 is not install in your pi use,

~~~
sudo apt-get install python3
~~~
5. Open nano
<li>To check if nano is installed, type:</li>

~~~
nano --version
~~~
<li>If nano is not installed, install it by typing:</li>

~~~
sudo apt-get update
sudo apt-get install nano
~~~

7. Use the following command to open nano and create a file name gas.py
   
~~~
nano gas.py
~~~

<p align="center">
  <img src="https://github.com/Iswarya-Singaram/Gas_level_monioring-Raspberry-pi/assets/145309713/c43e9a80-88e8-4a45-ae01-97fafe06f44e" width="500" height="300">
</p>

8. Paste the following Source code:
~~~
import RPi.GPIO as GPIO
import time

# Set up the GPIO mode
GPIO.setmode(GPIO.BCM)

# Set up the GPIO pin for reading the DO output
DO_PIN = 7  # Replace with the actual GPIO pin number
GPIO.setup(DO_PIN, GPIO.IN)

try:
    while True:
        # Read the state of the DO pin
        gas_present = GPIO.input(DO_PIN)

        # Determine if gas is present or not
        if gas_present == GPIO.LOW:
            gas_state = "Gas Present"
        else:
            gas_state = "No Gas"

        # Print the gas state
        print(f"Gas State: {gas_state}")

        time.sleep(0.5)  # Wait for a short period before reading again

except KeyboardInterrupt:
    print("Gas detection stopped by user")

finally:
    # Clean up GPIO settings
    GPIO.cleanup()
~~~

9. Now, click Ctrl+X to exit nano.
10. Run the python script by
    
~~~
python gas.py
~~~

## Troubleshooting
<li>Ensure all connections are secure.</li>
<li>Check the power supply to the gas sensor.</li>
<li>Verify that the correct GPIO pin is used in the script.</li>
<li>Consult the gas sensor's datasheet for specific details about its operation and requirements.</li>

## Contributing
Contributions are welcome! Please fork this repository and submit pull requests.









