# Base Idea

There's **one Useless Pope** and **12 remote buttons**.

Inside the Pope, a raspi is connected via USB to the microcontroller which does all the LED control stuff.
The raspi is also hosting a web page with displays additional actions for controlling the Pop and shows (useless) statistics.
Via a SMB network share, each user can upload individual sounds, which are randomly played if the remote button is pressed.

Each user gets their own remote button. The raspi also creates a Wifi access point. These buttons are automatically connecting to this network.
Via these remote buttons, an action of the Pope will follow. Manly by playing a sound, but other actions are possible.

# Pope Hardware

Required hardware to satisfy all requiested features:

* Raspberry Pi 5
* [A USB Soundcard](https://www.amazon.de/dp/B01N905VOY)
* [NUCLEO-H743ZI](https://www.st.com/en/evaluation-tools/nucleo-h743zi.html#st_all-features_sec-nav-tab)
* car mini ammplifier
* Speaker
* Humidifier
* NEO Pixel LED Background Light
* Many Switches
* Many LEDs
* Stepper motor
* AC/DC 5V power supply for the Microcontroller
* AC/DC 5V USB power supply for the Raspi
* 12V Power supply for the car mini amplifier
* ? Power supply for the humidifier
* Motion detector
* Electric field detector via darlington transistor cascade
* Microphone
* Ethernet Plug
* A LCD panel like the one I already have for the transport station. It can be used to count the rotations.
* 3.5mm analog audio output

## Feature list

* main power switch
* ~~optional~~ audio output
* 

# Remote Buttons

There are 12 remote buttons. When a button gets pressed, this will be sent via wifi to the Pope.

Each button consists of
* [ESP32](https://www.amazon.de/dp/B074RG86SR)
* 1 LED
* 1 Button
* USB connector (either built-in micro-USB port or dedicated cable)
* 1 case (plastic?)


# Software Features

## Base System

* SMB network share with individual folders for each user so that they can modify their sounds
* A reset possibility to reset a folder to the default sounds
* A web page

## Web Page

[Demo page](http://hoffer.cx/tkpapst/)

### Actions

* Sing "Hallelujah!"
* Make white smoke
* Change colour of background LED

### Statistics

* Uptime (when was the Pope turned on == begin of LAN party)
* Number of rotations of the wheel
* List which sound was played most often
* List which user hits their button the most (top 3 active users + number of actions)
* Total number of actions

## Database (MariaDB)

This is the main interface.

* Statistics for the web page
* Control commands for the micricontroller
* Control commands from the buttons
* Control commands to the buttons
* Control commands from the WebPage

## Remote button controlled sounds

The sounds can be transferred to the Pope via SMB share. 
If a button is pressed, a random sound from the users folder will be played.
If multiple users press a button, all sounds will be played at once.
If a sound effect takes longer than 30 seconds, it will fade out.
