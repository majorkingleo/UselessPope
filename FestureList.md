# Base Idea

A raspi is connected via USB to the microcontroller who does all the LED control stuff.
The raspi creates a Wifi acces point. The remote buttons are automatically connecting to this network.
Via these remote buttons an action of the pope will follow. Manly by giving a sound, but other 
reaction are possible.

Each TK member gets it's own button. Via a SMB network share each member can upload individual sounds, which are 
randomly played if the remote button is pressed.

The raspi is also hosting a webpage with additional informations and statistics.

# Pope Hardware

Required hardware to satisfy all requiested features.

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

## Feature list

* main power switch
* optional audio output
* 

# Remote Buttons

There are 12 remote buttons. When a button got's pressed this will be sent wia wifi to the pope.
Each button consists of
* [ESP32](https://www.amazon.de/dp/B074RG86SR)
* 1 LED
* 1 Button


# Software Features

## Base System

* SMB network share with individual folders for each user so that they can modify their sounds.
* A reset possibility to reset a folder to the default sounds.
* A web page.

## Web Page

* Number of rotations of the wheel.
* List which sound was played most often, which user hit the button at most.

## Database (MariaDB)
This is the main interface.

* Statistics for the WebPage
* Controll commands for the micricontroller.
* Controll commands from the buttons.
* Controll commands to the buttons.
* Controll commands from the WebPage.

## Remote button controlled sounds

The sounds can be transfered to the pope via smb share. 
If a button is pressed a random sound of the users folder will be pressed.
If multiple users pressed a button all sounds will be played at once.
If a sound effect takes longer than 30 seconds it will be faded out.
