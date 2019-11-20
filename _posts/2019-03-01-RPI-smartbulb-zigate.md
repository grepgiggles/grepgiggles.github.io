---
layout: post
title: "Raspberry Pi + Zigate adapter-controlling smart devices"
date: 2019-03-01
categories: Raspberry Pi Zigate
---

#### Materials required
- RPI
- ZiGate usb adapter
- Domoticz software (open source)
- Smart device of choice

#### Smart devices I have tried and recommend
- Philips Hue Smart bulb
- OSRAM smart bulb
- OSRAM smart switch/motion sensor
- Aqara temperature and humidity sensor
- Aqara magnetic door sensor 

### Some background info on ZiGate, ZigBee and Domoticz (skip ahead for setup steps).

Lucky to have been gifted some really cool home automation gadgets, I have been flat out playing with them and attempting to
transform my room into a data monitoring and collecting system. 

One gadget which I use daily is a ZiGate usb on my Raspberry Pi to control my smart bulbs. I find red and orange hues extremely restorative and relaxing after a long day staring at blue light emitting screens. 
Having gotten it for free and being completely ignorant of smart transmitters/adaptars I didn't think much of this dongle at the time. 
Now after doing some research I am realising what a nifty and underrated piece of kit it is.


![image-title-here](/img/20190314_143112.jpg)

![image-title-here](/img/20190314_143247.jpg)

ZiGate is the result of a French kickstarter project [https://www.kickstarter.com/projects/1361563794/zigate-universal-zigbee-gateway-for-smarthome]
It is unique in that it is an *open source* ZigBee adapter hardware allowing my RPi to communicate over a wifi network to multiple smart devices. 
Like bluetooth and wifi, ZigBee is a wireless technology network protocol allowing data transmission between devices. 

ZigBee differs though in the mesh routing technique it uses to link your smart devices. 
ZigBee spans throughout your home linking your sensors and devices to the network in a mesh routing topology, with the potential to accomomodate up to 65,000 device connections in total! 

ZigBee's much lower bandwidth at 250kb/s is  adapted for slower information transfer over a smaller range (10-30 metres)
compared to wifi's bursty 54mb/s, and thus is perfectly adapted for enabling communication between IoT appliances.


![image-title-here](/img/ScreenShot2019-03-11at18.29.53.png)

![image-title-here](/img/ScreenShot2019-03-11at18.41.05.png)

Domoticz is an open source platform designed for controlling a home automation system. It's UI shows the devices present 
on your network. Running on my RPi's local host, it is from here that I switch on my smart bulbs, check my temperature and humidity sensor's reading, 
or operate any other sensors.

The first step in initiating your home control system will be to 
install domoticz on your Raspberry Pi.





## 1. Installing domoticz
[Domoticz documentation](https://www.domoticz.com/wiki/Raspberry_Pi)

In your RPi's terminal:

```curl -L install.domoticz.com | sudo bash```

```cd /home/pi/domoticz/plugins```

```git clone https://github.com/sasu-drooz/Domoticz-Zigate.git```

```git branch -a <https://github.com/sasu-drooz/Domoticz-Zigate.git```

At the time, I was having some difficulty pairing my devices with zigbee so the documentation on wiki suggested to change 
to the beta branch to resolve this issue

```git checkout beta-3.2``` (or whatever the latest branch is)

Restart domoticz on your RPi
```sudo systemctl restart domoticz.service```

## 2. Navigate to the Domoticz web interface

Domoticz runs on your Rpi's local host so you will find domoticz by putting the name of your device (hostname) 
along with :8080. For me, domoticz is hosted over on:

http://lindamelon:8080

## 3. Configure your ZiGate adaptor to Domoticz

Go to the hardware tab

Select Zigate from the pull down

Change the join timeout from 254 to 255 if you want to

Click the "Add" button

## 4. Find and pair your device(s)
Each time you want to add a device:

Reset the bulb or whatever device you are using (e.g. OSRAM bulb: 5 seconds off, on, repeat a total of 5 times)

Go to the Devices tab

![image-title-here](/img/ScreenShot2019-03-11at18.58.47.png)

Refresh if necessary

You should see the device

Click the little icon that looks like an arrow pointing to the right, this should enable the device

Now go to the switches tab, you should now see the controls for the device




I hope this was insightful! I have a fun project planned on the horizon so stay tuned for more IoT updates and tinkering. 



