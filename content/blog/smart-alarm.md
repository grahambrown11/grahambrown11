---
title: "Is My Alarm Panel Smart?"
date: 2020-11-22
draft: false
menu: blog
weight: 1
---
In this modern world with the Internet everything has become _smart_.
<!--more-->
The smart trend started with the mobile phone - do you remember that brick that almost fit in your pocket with around 14 buttons that could make a phone call and send text messages? Changing its buttons for a touch screen and having Internet connectivity now makes it a smartphone. The phone itself didn’t get smarter, it’s the possibilities that opened up from the new interactive display and being connected to the Internet that earned it the smart label. Other electronics started adopting the smart label like TVs, speakers, light bulbs and even kitchen appliances. But as noted with the smartphone they’re not smart on their own - it's the servers on the Internet they talk to (also known as Cloud Services). 

So if I could add WiFi to my alarm panel that talks to a server does it make it smart? 
I found a module - the EnvisaLink 4 that has ethernet and connects to the DSC alarm panel, but I would prefer a WiFi one as my alarm panel is upstairs and the router downstairs - didn’t want to run an ethernet cable. I then came across an OpenSource project [dscKeybusInterface](https://github.com/taligentx/dscKeybusInterface) which is a library for microcontrollers, so I bought a D1 Mini (ESP8266) and the other electronic components to build my own module.

![Circuit](/images/blog/Alarm%20Circuit.png)

I liked the VirtualKeypad-Web example from the dscKeybusInterface library which has a web server with a good looking web page to control the panel, however that does not really make it smart… HomeAssistant is software that allows you to automate actions to/from smart devices, this is where the smarts come from for my alarm panel, so I combined the virtual keypad with the HomeAssistant-MQTT example. Although I’ve not got anything very smart yet, at least I get notified via my smartphone when the alarm is triggered, and I can use the motion to turn on lights.

![Screenshots](/images/blog/Alarm%20Screenshots.png)

After running for a few weeks, the virtual keypad stopped working and HomeAssistant wasn’t getting events, so I implemented a watchdog which determines if the code stopped running and resets the D1 Mini. The code can be found on my [GitHub](https://github.com/grahambrown11/ESPAlarmPanel).