---
layout: post
title: "Blinking LEDs with Raspberry Pi-electronics explained"
date: 2018-09-01
categories: Raspberry Pi Electronics
photo: /img/raspbpihelloworld.gif

---
![image-title-here](/img/raspbpihelloworld.gif)

After a long wait for my ‘Adeept Ultimate Starter learning Kit for Arduino MEGA 2560 LCD1602 Servo Motor’ to come from China. (Can be found below at Wish.com)….

[https://www.wish.com/feed/tabbed_feed_latest/product/5b38fc4c155cec3126f8222f?&source=tabbed_feed_latest]

![image-title-here](/img/screen-shot-2018-09-30-at-09-30-26.png)

…I had more than enough bits and bobs to start with. First I had to identify the components of the toolkit. After doing some research online I found to blink an LED I needed:

 -   Breadboard
 -  420Ω resistor
 -  Jumper wires
 -  Raspberry pi

![image-title-here](/img/20180922_110709-e1538301455313.jpg)
![image-title-here](/img/20180922_110703-e1538301408216.jpg)


Rummaging through the kit, I found the breadboard and peeled away a few wires from the multi-coloured ‘Male to Female’ wire bundle easily enough. It took me a while to realise that the minuscule flimsy plastic caps resembling a bobby pin were in fact the LEDs.

Before I could build a circuit I needed to understand the breadboard structure, flow of electricity through the board and the function of a resistor.

A breadboard serves as the base of an electronic circuit. It is partitioned in a way that the two vertical strips (blue and red lines) down the side of the board are continuous but do not cross over to the middle of the board while the horizontal holes (green lines) are linked together linearly but do not cross the overlap defined by the middle of the board. A strip of conductive metal lines these rows and a set of connected holes can be referred to as a ‘node’. A component inserted in a node will be electrically connected to anything else placed in that row.

![image-title-here](/img/bread_expl-e1538299391381.jpg)


A resistor can be thought of as a dam wall-it resists the current or flow of water (in our case electric charge) obstructing the volume of flow . Resistors come in varying strengths (resistance). A 220Ω resistor permits a total voltage (raspberry pi voltage output minus 220Ω) to reach our LED component.

The potential difference (voltage) across an ideal conductor is proportional to the current through it. The constant of proportionality is called the “resistance”.

The formula for voltage is given by Ohm’s law:

> V = IR

Where V is the potential difference between 2 points taking a resistance R into account. 5V is the GPIO voltage output for the model of my Raspberry Pi 3 B+.

> 5 = I × R

I’ve chosen to experiment with a 220 Ω resistor since the other resistors in the kit are either 1KΩ or 10KΩ. I’m expecting the LEDs to be extra bright since a 420Ω resistor is recommended.

> I = 5/220

> I = 1/4.4 Amp

> I = 250mA

Therefore the total current flowing to my LED component will be 250mA.

Understanding the topology of your GPIO board can be achieved with the bash ‘pinout’ command:

```pinout```

![image-title-here](/img/pinout.png)

I used pins 9 (ground) and 11 (GPIO17) for output.

After hooking up the jumper cables to the correct pins, inserting the resistors and LED leg pins-the long leg goes to positive (anode), the short one goes to the minus (cathode)- I imagine the circuit looks something like this:

Electricity flows from point A (GPIO pin) to B (ground). If there is no wire going to ground the circuit will not be complete and the current will not flow. This circuit can be easily adapted to add more LEDs by adding 3 extra wires to divert the flow (output) of the LEDs to ground.

A simple python script was stitched together from reading raspberry pi’s excellent documentation.

[https://www.raspberrypi.org/documentation/usage/gpio/python/README.md]




