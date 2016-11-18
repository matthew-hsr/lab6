# lab6
Pi Stepper Motor Controls

Lab 6

The Adafruit DC and Stepper Motor HAT is an add-on that enables your Pi to drive up to 4 DC or 2 Stepper motors with pulse width modulation(PWM) speed control. There is a dedicated PWM driver chip onboard to control motor direction and speed. As the chip handles all the motor and speed controls over I2C (Inter-Integrated Circuit), other I2C devices or HATs can be connected to the same pins. You can actually stack up to 32 such Motor HATS, to control 64 stepper motors and 128 DC motors. Let’s see how we can make the motors turn!

The first step is to solder all headers and terminal block onto the HAT, allowing electrical cables to be connected to the HAT easily. It has already been done. Now what?

Let’s do some software preparation on the Pi, in the meantime you can prepare for the motor connections, after the asterisks.

*************Software Prep*************
Same stuff as before, enable I2C on your Pi by starting a terminal and running:
```
	sudo apt-get install -y python-smbus
sudo apt-get install -y i2c-tools
```
Then run
```
sudo raspi-config
```
Go to Advanced Options to enable I2C, then reboot!

Go to an appropriate location (ex. /home/pi/lab6), run the following:
```
git clone https://github.com/adafruit/Adafruit-Motor-HAT-Python-Library.git
cd Adafruit-Motor-HAT-Python-Library
Install python-dev if you haven’t:
sudo apt-get install python-dev
sudo python setup.py install
```
You have finished the software preparation part!
*************Software Prep*************


Since a motor requires a lot of energy, and it puts a lot of noise onto a power supply (because of back emf), it’s best to use another source of power. We therefore changed some AC/DC adapters (a.k.a. Wall warts) into motor power supplies. Without plugging in, connect the power line (with specs written on it) to the negative power supply on the HAT, and the other line (grooved on the side) to positive. Don’t let the two lines short! If you do, you could easily have a burnt board or worse!


The motors we have are bipolar stepper motors, for those who are curious what that means:
http://mechatronics.mech.northwestern.edu/design_ref/actuators/stepper_intro.html

Connect the blue, red cables to the two connectors labelled M1 and green, black to the two connectors labelled M2. Turn off your Pi, help your Pi wear the HAT, power the HAT and then your Pi!


Now it’s time to get the shafts turning!


Go to the previous directory created and go into the folder examples
Then run the following to watch your stepper motor spin!
```
sudo python StepperTest.py
```

Try to read and understand the example! Write your own code to make the motor dance around!

There are 4 kinds of steps that work with any unipolar or bipolar stepper motor for this motor HAT:

Single steps: simplest type of stepping, uses the least power, only uses a single coil
Double steps: uses two coils at once, stronger but requires more power
Interleaved steps: mix of single and double stepping, smoother transition between steps, more strength than single stepping and about 50% more power
Microstepping: mix of single stepping with PWM to slowly transition between steps, slower but much higher precision.

Try to feel the difference between modes by touch!

I2C troubleshoot:
https://learn.adafruit.com/adafruits-raspberry-pi-lesson-4-gpio-setup/configuring-i2c

References:
https://learn.adafruit.com/adafruit-dc-and-stepper-motor-hat-for-raspberry-pi/overview
