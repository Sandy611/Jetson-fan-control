# Jetson PWM fan control
  Automagic fan control for the Nvidia Jetson Nano

# Requirements:
  Hardware:
    You will need a 5V PWM fan for this to make any sense.

Additionally, I recommend you use the barrel jack with a 4A power supply.

# Software:
  I will assume you use the standard image on your jetson nano.
  Python 3 should be pre-installed on the jetson nano.
  You can check this using:
  $ python3 --version
  Note:- python3.5 or higher would be fine otherwise, you can install it with:
  $ sudo apt install python3-dev

# How to install:
  Clone the respiratory and run:
  $ sudo ./install.sh
  The script will automatically run at boot time.

# How to customize:
  Open /etc/automagic-fan/config.json with your favorite editor (I'm using nano):
  $ sudo nano /etc/automagic-fan/config.json

You will find the following lines:
{
"FAN_OFF_TEMP":20,
"FAN_MAX_TEMP":50,
"UPDATE_INTERVAL":2,
"MAX_PERF":1
}
FAN_OFF_TEMP is the temperature (°C) below which the fan is turned off.
FAN_MAX_TEMP is the temperature (°C) above which the fan is at 100% speed.
The script interpolates linearly between these two points.

UPDATE_INTERVAL tells the script how often to update the fan speed (in seconds).
MAX_PERF values greater than 0 maximize system performance by setting the CPU and GPU clock speeds to the maximum.

Any changes in the script will be will be applied after the next reboot.
You can run:
$ sudo service automagic-fan restart
to apply changes immediately.

If you suspect something went wrong, please check:
$ sudo service automagic-fan status
