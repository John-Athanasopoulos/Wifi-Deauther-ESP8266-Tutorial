<p align="center"><img src="https://github.com/John-Athanasopoulos/Wifi-Deauther-ESP8266/blob/master/Pictures/coollogo_com-24212736.jpg"></p>

<p align="center">A tutorial on how to make a Wifi Deauther (with beacon and probe attacks included) with an ESP8266 board!</p>

## Introduction
Hello and welcome to my tutorial on how to make a Wifi Deauther with a simple ESP8266 board. There are a lot of tutorials on the internet,
but I realised that all of them either weren't very clear, or lacked some information needed (at least for me). That's the main reason why
I decided that I should make my tutorial on the Wifi Deauther, having collected all the information in one place and trying to make the
instructions simple and short. You can navigate to the sections of the tutorial clicking on the following links:

[Hardware Prerequisites](#What-you-will-need)

[Programming the board](#Programming-the-board)

## What you will need
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

## Programming the board
> IF YOU HAVE A DSTIKE WiFi Deauther MiNi ESP8266 OLED BOARD OR ANY BOARD THAT IS ALREADY PROGRAMMED, SKIP THIS STEP

In order to be able to use the ESP8266 board, we will need to program it to execute the attacks we want. In order to do that, we will
need to download the ARDUINO IDE (found here: <a href="https://www.arduino.cc/en/Main/Software">ARDUINO IDE</a>).
<p align="center">Be careful! We need to download the ARDUINO IDE and not use the ARDUINO WEB EDITOR.</p>

Once we have downloaded the ARDUINO IDE, we need to open it and head to the Navigation Bar. After that, we need to select File(or Arduino)/Preferences and a window will open. In the *"Additional Boards Manager URLs"* field, we need to paste the following links:
<p style="background-color:black;color=#ffffff";>
```
http://arduino.esp8266.com/stable/package_esp8266com_index.json
http://phpsecu.re/esp8266/package_deauther_index.json
```
</p>
Make sure they are on separate lines.
