# Introduction
Thorough and simple tutorial on the WiFi Deauther using an ESP8266 board. Based on the work of Stefan Kremser (<a href="https://github.com/spacehuhn">spacehuhn</a>).
Used to launch deauthentication, beacon and other attacks on WiFi networks.


> [!CAUTION]
> Using the WiFi Deauther on networks you don't own is illegal.

## Hardware Prerequisites

### Suitable boards
> [!WARNING]
> Note that there are multiple knock-off boards you can use, however there's always a risk of them not being suitable.

- **DSTIKE WiFi Deauther MiNi ESP8266 OLED**: Already configured board, features a screen that enables its use without the need of it being plugged into a laptop or smartphone.
- **ESP8266 NodeMcu with CP2102** or **ESP8266 NodeMcu with CH340G** : The first one is probably the best choice for this tutorial.
- **WeMos D1 Mini ESP8266 NodeMcu 4M**: Generally most WeMos ESP8266 boards will work, even if they are knock-offs.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/ESP8266Boards.jpg"></p>

> In order: DSTIKE WiFi Deauther MiNi ESP8266 OLED, ESP8266 NodeMcu with CP2102, WeMos D1 Mini ESP8266 NodeMcu 4M.

### Cables needed

All boards (except the DSTIKE WiFi Deauther MiNi ESP8266 OLED) need to be connected with a micro-USB cable to a power source, specifically to a laptop or smartphone.

## Programming the board
> [!NOTE]
> If using the DSTIKE WiFi Deauther MiNi ESP8266 OLED skip this step.

To use the ESP8266 board, we will need to program it. In order to do that, we will need to download the ARDUINO IDE (found here: <a href="https://www.arduino.cc/en/Main/Software">ARDUINO IDE</a>). 

> [!TIP]
> Use the ARDUINO IDE and not ARDUINO WEB EDITOR.

After installing ARDUINO IDE, open it and head to the Navigation Bar. Select File/Preferences (or Arduino/Preferences) and paste the following links in the "Additional Boards Manager URLs" field:

```
http://arduino.esp8266.com/stable/package_esp8266com_index.json
http://phpsecu.re/esp8266/package_deauther_index.json
```
> [!NOTE]
> Make sure they are on separate lines and apply the changes clicking "OK".

Navigate to Tools/Board/Boards Manager, search "esp8266" in the search bar and install both "arduino-esp8266-deauther" and "esp8266" (even if you already have them). After their installation, both will display the word "INSTALLED" next to their name.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/BoardsManager.png"></p>

Connect the board to your laptop with a micro-USB cable and head to Tools. There, your board may be autoselected. If this isn't your case, click on "Board", search the one you have under the sub-category of "ESP8266 Deauther Modules" and select it. If everything has been done correctly, you will see that the port is auto-selected. 

> [!TIP]
> For ESP8266 with CP2102 board, I recommend changing Upload Speed to 115200.


Now, in order to insert the programs we want our board to execute, we will need to download/clone them.


For LINUX users:
```
git clone https://github.com/spacehuhn/esp8266_deauther.git
```

For Windows/MAC users:

Head to <a href="https://github.com/spacehuhn/esp8266_deauther.git">this link</a> and click on Clone or Download/Download ZIP. After that, extract the folder "esp8266_deauther-master".

### Final Steps
- Copy and paste the folder ```esp8266_deauther-master/esp8266_deauther``` inside the "Arduino" folder (inside Documents System Folder)
- Open ```[...]/Arduino/esp8266_deauther/esp8266_deauther.ino``` within ARDUINO IDE
- Press Upload (Arrow under navigation bar)

Your board is set up and ready to use.


## Connecting to the board network
Connect the board to a laptop or smartphone and subsequently connect to the WiFi Network "pwned" using "deauther" as password. Head to your browser and visit ```deauther.me``` or ```192.168.4.1```. You will see the following window:
<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/2020-03-21 (1).png"></p>

Agreeing with the warning given to you grants you permission to the interface through which the attacks will be executed (shown below).

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/Inked2020-03-21 (2)_LI.jpg"></p>

## Using the network and attacking

The interface consists of three pages, Scan, SSID and Attacks.

#### Scan
Scan is broken down into 3 sections. The first is **Access Points**, containing all the nearby Wifi Networks that the Deauther can detect/scan. The others are **Stations** and **Saved Devices**.
To perform a scan, press Scan APS and this will scan for all the nearby Access Points.

#### SSID
> [!NOTE]
> Fake networks that are created might still be recognized by other devices for some time after stopping the attack

SSID holds 4 values:
- SSID: Where you put the name you want to use in the Beacon/Probe Attack
- WPA2 (radio button)
- Number (The number of fake networks that are going to be created)
- Overwrite (radio button - overwrites previous additions)

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/SSIDs.png"></p>

> Example of the creation of 20 WPA2-enabled fake wifi networks named "GitHub"

#### Attacks
In order to launch a Deauth Attack, we will first need to scan for the nearby Access Points and select one of them. Afterwards, we navigate to the Attacks tab and start the Deauth Attack. 
The ESP8266 board closes the connection of WiFi devices by sending deauthentication frames to access points and client devices, as a lot of devices don't use the 802.11w-2009 standard that protects against this attack.
> [!IMPORTANT]
> Select only one target, as you might encounter bugs when selecting multiple.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/DeauthAttack.png"></p>

In order to launch the Beacon Attack, we need to create a number of fake networks (as shown before) and then head to the Attacks tab and start the Beacon Attack.
It is also quoted that Beacon packets are used to advertise access points. By continuously sending beacon packets out, it will look like you created new WiFi networks. 

> [!TIP]
> You can specify the network names under SSIDs.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/BeaconAttack.png"></p>


Finally, for the Probe Attacks a phrase that explains everything is:

Probe requests are sent by client devices to ask if a known network is nearby. Use this attack to confuse WiFi trackers by asking for networks that you specified in the SSID list. 

> [!NOTE]
> It's unlikely you will see any impact by this attack with your home network.

## Settings

In the last page of the board's network, you can customize the settings, meaning you can change the name of the network, the network's password, etc.
> [!TIP]
> It's advised that you change both the name and the password of the network
