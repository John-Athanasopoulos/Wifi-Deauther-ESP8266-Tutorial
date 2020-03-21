<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/coollogo_com-24212736.jpg"></p>

<p align="center">A tutorial on how to make a Wifi Deauther (with beacon and probe attacks included) with an ESP8266 board!</p>

# Introduction
Hello and welcome to my tutorial on how to make a Wifi Deauther with a simple ESP8266 board. There are a lot of tutorials on the internet,
but I realised that all of them either weren't very clear, or lacked some information needed (at least for me). That's the main reason why
I decided that I should make my tutorial on the Wifi Deauther, having collected all the information in one place and trying to make the
instructions simple and short. You can navigate to the sections of the tutorial clicking on the following links:

<hr>

➼ [Disclaimer](#Disclaimer)

➼ [Hardware Prerequisites](#What-you-will-need)

➼ [Programming the board](#Programming-the-board)

➼ [Connecting to the board network](#Connecting-to-the-board-network)

<hr>

# Disclaimer 
The attacks that this Wifi Deauther can execute are powerful and thus illegal in most countries. Please do make sure you test and use this in networks you own and try not to harm or annoy others. I shall not be held responsible for any damage that you cause with this tool. Because that is its purpose. It is a tool, not a weapon. It is meant for you and me to learn and have fun, not to be used as a way to harm. Be wary of your actions!

# What you will need
The main thing we are going to need to make a Wifi Deauther is an ESP8266 board. However, we have to be careful when we are buying the
board itself, as there are a lot of knock-off products that are low-quality and therefore their attacks are at best mediocre and won't last
for long. The price difference between the original and knock-off products is so small, that really it is not worth buying the knock-off
version of the product. But enough with the words, let's see the boards you can actually use:

• ***DSTIKE WiFi Deauther MiNi ESP8266 OLED*** (this model already has the code needed and a small screen, so you can skip the programming
phase and you can use it without the need of it being plugged into a laptop or smartphone).

• ***ESP8266 NodeMcu with CP2102*** or ***ESP8266 NodeMcu with CH340G*** (although the first one is better by far. It's also the one I
bought so we know it works for sure).

• ***WeMos D1 Mini ESP8266 NodeMcu 4M*** (generally most WeMos ESP8266 boards will work, even if they are knock-offs).

• Other knock-off products that might work, might not (is it really worth taking the risk?).

There are of course a lot of boards that I have not included, as there are countless models of ESP8266 boards. These are just the most
common.
Personally, as I've read the ESP8266 NodeMcu with CP2102 is one of the best boards for this purpose, so if I was able to buy this one I
would definitely stick with it.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/ESP8266Boards.jpg"></p>

> In order: DSTIKE WiFi Deauther MiNi ESP8266 OLED, ESP8266 NodeMcu with CP2102, WeMos D1 Mini ESP8266 NodeMcu 4M

**What else are you going to need though?**
In order for the board to work, you are definitely going to need a power source. The main way you can power up these boards are with a
micro-USB cable. They have to be connected to a laptop or smartphone with a cable and then they can be used by those devices. So you
you are defnitely going to need a micro-USB/USB cable, and if you plan to use it through your smarthphone you will also need a
USB to micro-USB adapter.

# Programming the board
> IF YOU HAVE A DSTIKE WiFi Deauther MiNi ESP8266 OLED BOARD OR ANY BOARD THAT IS ALREADY PROGRAMMED, SKIP THIS STEP

In order to be able to use the ESP8266 board, we will need to program it to execute the attacks we want. In order to do that, we will
need to download the ARDUINO IDE (found here: <a href="https://www.arduino.cc/en/Main/Software">ARDUINO IDE</a>).
<p align="center">Be careful! We need to download the ARDUINO IDE and not use the ARDUINO WEB EDITOR.</p>

Once we have downloaded the ARDUINO IDE, we need to open it and head to the Navigation Bar. After that, we need to select File(or Arduino)/Preferences and a window will open. In the *"Additional Boards Manager URLs"* field, we need to paste the following links:

```
http://arduino.esp8266.com/stable/package_esp8266com_index.json
http://phpsecu.re/esp8266/package_deauther_index.json
```
Make sure they are on separate lines. Then hit "OK" to save and again "OK" to close the window. Now we have to find our Board..
Navigate to Tools/Board/Boards Manager. This is where we can add more boards to our ARDUINO project. Search "esp8266" in the search bar
and install both "arduino-esp8266-deauther" and "esp8266" (You probably already have at least one of them, but do it just in case..).

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/BoardsManager.png"></p>

> After their installation, you should be able to see the word "INSTALLED" next to each


<p align="center"><b>Now we've come to the best part.. The programming of the board.</b></p>

Connect the board to your laptop with a micro-USB cable and head to Tools. There your board may be autoselected. In case this isn't
your case, click on "Board" and search the one you have under the sub-category of "ESP8266 Deauther Modules". When you find it, select
it. If everything has been done correctly and the cable you have is not of poor-quality, you will see that the port is auto-selected.
(For ESP8266 with CP2102 Board buyers, I recommend changing Upload Speed to 115200)

Now, in order to insert the programs we want our board to execute, we will need to download/clone them.

<hr>
• **For LINUX users:** Clone the repository with the command below.

```
~# git clone https://github.com/spacehuhn/esp8266_deauther.git
```

• **For Windows/MAC users:** Head to <a href="https://github.com/spacehuhn/esp8266_deauther.git">https://github.com/spacehuhn/esp8266_deauther.git</a> and click on Clone or Download/Download ZIP. After that, extract the folder "esp8266_deauther-master".
<hr>

After these steps, in the "esp8266_deauther-master" folder you will find an "esp8266_deauther" folder. Copy the last folder and paste it in the "Arduino" folder (Found probably in the Documents System Folder). The next step is to open the "esp8266_deauther.ino" file with Arduino from inside the "Arduino" folder. That means open ARDUINO IDE, and open .../Arduino/esp8266_deauther/esp8266_deauther.ino

Now triple-check that you have correctly selected your Board's module and options and press the Upload button (Arrow under navigation bar).

<p align="center"><b>CONGRATS! YOUR BOARD IS SET UP AND READY FOR USE!</b></p>

<hr>


# Connecting to the board network
In order to use our Wifi Deauther, we need to connect to the board's network. Every time the board is connected to a laptop or smartphone (or any power source if it is a module with a screen), it creates a Wifi Network called "pwned" with "deauther" as password (both changeable in the future). Click on pwned and log into it. Now, in order to access the deauther's attacks, head to your browser and type either "deauther.me" or "192.168.4.1". You will see the following window:
<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/2020-03-21 (1).png"></p>

Read the message written and then press "I HAVE READ AND UNDERSTOOD THE NOTICE ABOVE". You will then be granted permission to the interface through which the actual attacks are going to be executed:

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/Inked2020-03-21 (2)_LI.jpg"></p>

# Using the network and attacking
The interface of the board's network is really user-friendly and you can possibly figure out everything by yourself, as it gives you some very short directions about everything. However, as you probably have never done this again stick with this tutorial and I will guide you through every option. 
The first page is **Scan** and you can easily understand what it does. THe first page is broken down to 3 simple categories. The first is *Access Points*, and these are all the nearby Wifi Networks that the Deauther can detect/scan, then we have *Stations* and lastly the *Saved Devices*.
To perform a scan, press APS and this will scan for all the nearby Access Points. After that, you can select a network that you want to attack with the Deauth Attack (we will get there in 2 minutes)

<hr>

The second page is called **SSIDs**. It holds 4 values:
• SSID: Where you put the name you want to use in the Beacon/Probe Attack
• WPA2 (radio button)
• Number (The number of fake networks that are going to be created)
• Overwrite (radio button - overwrites previous additions)
After you are done, click on Add and if you scroll down you will see as many fake networks that can be used in the Beacon Attack, as the number you have entered in the Number field.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/SSIDs.png"></p>

> Example of the creation of 20 WPA2-enabled fake wifi networks named "GitHub"

<hr>

We have finally arrived to the third and possibly the most important page. It's called **Attacks** and I guess that you can easily understand what you can do in this page. I will demonstrate two types of attacks (Deauth and Beacon) and describe the last one (Probe).

In order to launch a Deauth Attack, we will first need to scan for the nearby Access Points and afterwards select one of them. After that, we navigate to the Attacks tab and we Start the Deauth Attack. Simple, yet effective, the little ESP8266 board will make sure that no-one is able to connect to that Wifi while the attack is being launched.
It is also quoted that:
> The Deauth Attack closes the connection of WiFi devices by sending deauthentication frames to access points and client devices you selected.
This is only possible because a lot of devices don't use the 802.11w-2009 standard that offers a protection against this attack.
Please only select one target! When you select multiple targets that run on different channels and start the attack, it will quickly switch between those channels and you have no chance to reconnect to the access point that hosts this web interface.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/DeauthAttack.png"></p>

<hr>

In order to launch the Beacon Attack, we need to create a number of fake networks (as shown before) and then head to the Attacks tab and start the Beacon Attack. You can see its results immediately.
It is also quoted that:
> Beacon packets are used to advertise access points. By continuously sending beacon packets out, it will look like you created new WiFi networks. You can specify the network names under SSIDs.

<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/BeaconAttack.png"></p>

