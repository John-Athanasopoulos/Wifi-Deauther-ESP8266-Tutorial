# Introduction
This is a tutorial on how to make a Wifi Deauther with a simple ESP8266 board. There are a lot of tutorials on the internet,
but most of them either weren't very clear, or lacked some information needed. This tutorial aims to simplify the whole process and collects all the information in one place.

<hr>

➼ [Disclaimer](#Disclaimer)

➼ [Aknowledgement](#Aknowledgement)

➼ [Hardware Prerequisites](#What-you-will-need)

➼ [Programming the board](#Programming-the-board)

➼ [Connecting to the board network](#Connecting-to-the-board-network)

➼ [Using the network and attacking](#Using-the-network-and-attacking)

➼ [Settings](#Settings)

➼ [Personal Information](#Personal-Information)

<hr>

# Disclaimer 
The attacks that this Wifi Deauther can execute are powerful and thus illegal in most countries. Please do make sure you test and use this in networks you own. I shall not be held responsible for any damage that you cause with this tool. Be wary of your actions, as this tutorial is solely for learning purposes.

# Aknowledgement
This tutorial is based on the work of Stefan Kremser (<a href="https://github.com/spacehuhn">spacehuhn</a>). My contribution is just to simplify the steps of the creation of the Deauther tool and nothing more.

# Hardware Prerequisites
The hardware used is an ESP8266-type board. There are knock-off products, however you are advised not to use them. Below you can see a list of boards that are suitable for this project:

• ***DSTIKE WiFi Deauther MiNi ESP8266 OLED***: This model already has the code needed and a small screen, so you can skip the programming phase and you can use it without the need of it being plugged into a laptop or smartphone.

• ***ESP8266 NodeMcu with CP2102*** or ***ESP8266 NodeMcu with CH340G*** : The first one is probably the best choice for this tutorial.

• ***WeMos D1 Mini ESP8266 NodeMcu 4M***: Generally most WeMos ESP8266 boards will work, even if they are knock-offs.

• Other ESP8266-type boards might work.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/ESP8266Boards.jpg"></p>

> In order: DSTIKE WiFi Deauther MiNi ESP8266 OLED, ESP8266 NodeMcu with CP2102, WeMos D1 Mini ESP8266 NodeMcu 4M.

For the board to work, you are definitely going to need a power source. The main way you can power up these boards is with a micro-USB cable. They have to be connected to a laptop or smartphone with a cable and then they can be used via those devices. Thus, you will also need a micro-USB/USB cable and possibly an adapter if you want to use it through your smartphone.

# Programming the board
If your board is already programmed, this step is not needed.

In order to be able to use the ESP8266 board, we will need to program it to execute the attacks we want. In order to do that, we will need to download the ARDUINO IDE (found here: <a href="https://www.arduino.cc/en/Main/Software">ARDUINO IDE</a>). Use the ARDUINO IDE and not ARDUINO WEB EDITOR.

Once we have downloaded the ARDUINO IDE, we need to open it and head to the Navigation Bar. After that, select File/Preferences (or Arduino/Preferences) and paste the following links in the *"Additional Boards Manager URLs"* field:

```
http://arduino.esp8266.com/stable/package_esp8266com_index.json
http://phpsecu.re/esp8266/package_deauther_index.json
```
Make sure they are on separate lines and apply the changes clicking "OK".

Navigate to Tools/Board/Boards Manager. This is where we can add more boards to our ARDUINO project. Search "esp8266" in the search bar and install both "arduino-esp8266-deauther" and "esp8266" (You probably already have at least one of them, but still do it). After their installation, both will display the word "INSTALLED" next to their name.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/BoardsManager.png"></p>

Connect the board to your laptop with a micro-USB cable and head to Tools. There, your board may be autoselected. If this isn't your case, click on "Board" and search the one you have under the sub-category of "ESP8266 Deauther Modules". When you find it, select it. If everything has been done correctly and the cable is functional, you will see that the port is auto-selected. (For ESP8266 with CP2102 board, I recommend changing Upload Speed to 115200).

Now, in order to insert the programs we want our board to execute, we will need to download/clone them.


• **For LINUX users:** Clone the repository with the command below.

```
~# git clone https://github.com/spacehuhn/esp8266_deauther.git
```

• **For Windows/MAC users:** Head to <a href="https://github.com/spacehuhn/esp8266_deauther.git">https://github.com/spacehuhn/esp8266_deauther.git</a> and click on Clone or Download/Download ZIP. After that, extract the folder "esp8266_deauther-master".


After these steps, in the "esp8266_deauther-master" folder you will find an "esp8266_deauther" folder. Copy and paste it in the "Arduino" folder (Found probably in the Documents System Folder). The next step is to open the "esp8266_deauther.ino" file with Arduino from inside the "Arduino" folder. That means open ARDUINO IDE, and open .../Arduino/esp8266_deauther/esp8266_deauther.ino.

Now triple-check that you have correctly selected your Board's module and options and press the Upload button (Arrow under navigation bar).
Your board must be set up and ready to use.


# Connecting to the board network
In order to use our Wifi Deauther, we need to connect to the board's network. Every time the board is connected to a laptop or smartphone (or any power source if it is a module with a screen), it creates a Wifi Network called "pwned" with "deauther" as password (both changeable in the future). Click on pwned and log into it. Now, in order to access the deauther's attacks, head to your browser and type either "deauther.me" or "192.168.4.1". You will see the following window:
<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/2020-03-21 (1).png"></p>

Read the message written and then press "I HAVE READ AND UNDERSTOOD THE NOTICE ABOVE". You will then be granted permission to the interface through which the actual attacks are going to be executed:

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/Inked2020-03-21 (2)_LI.jpg"></p>

# Using the network and attacking

The interface consists of three pages, Scan, SSID and Attacks.

The first page is **Scan** and is broken down into 3 sections. The first is *Access Points*, and these are all the nearby Wifi Networks that the Deauther can detect/scan, then we have *Stations* and lastly the *Saved Devices*.
To perform a scan, press Scan APS and this will scan for all the nearby Access Points.


The second page is called **SSIDs**. It holds 4 values:
- SSID: Where you put the name you want to use in the Beacon/Probe Attack
- WPA2 (radio button)
- Number (The number of fake networks that are going to be created)
- Overwrite (radio button - overwrites previous additions)
After you are done, click on Add and if you scroll down you will see as many fake networks that can be used in the Beacon Attack, as the number you have entered in the Number field.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/SSIDs.png"></p>

> Example of the creation of 20 WPA2-enabled fake wifi networks named "GitHub"


The third page is called **Attacks**. I will demonstrate two types of attacks (Deauth and Beacon) and describe the last one (Probe).

In order to launch a Deauth Attack, we will first need to scan for the nearby Access Points and afterwards select one of them. After that, we navigate to the Attacks tab and we Start the Deauth Attack. Simple, yet effective, the little ESP8266 board will make sure that no-one is able to connect to that Wifi while the attack is being launched.
It is also quoted that the Deauth Attack closes the connection of WiFi devices by sending deauthentication frames to access points and client devices you selected.
This is only possible because a lot of devices don't use the 802.11w-2009 standard that offers a protection against this attack.
Please only select one target! When you select multiple targets that run on different channels and start the attack, it will quickly switch between those channels and you have no chance to reconnect to the access point that hosts this web interface.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/DeauthAttack.png"></p>


In order to launch the Beacon Attack, we need to create a number of fake networks (as shown before) and then head to the Attacks tab and start the Beacon Attack. You can see its results immediately.
It is also quoted that Beacon packets are used to advertise access points. By continuously sending beacon packets out, it will look like you created new WiFi networks. You can specify the network names under SSIDs.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/BeaconAttack.png"></p>


Finally, for the Probe Attacks I will just quote this phrase that explains everything:

Probe requests are sent by client devices to ask if a known network is nearby. Use this attack to confuse WiFi trackers by asking for networks that you specified in the SSID list. It's unlikely you will see any impact by this attack with your home network.

# Settings

In the last page of the board's network, you can customize the settings, meaning you can change the name of the network, the network's password, etc. It is advised you change both the name and the password. You can see part of the Settings Page below:

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/Settings.png"></p>
