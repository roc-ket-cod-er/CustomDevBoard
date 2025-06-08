---
title: "CustomDevBoard"
author: "Madhav"
description: "A devboard with every imaginable feature."
created_at: "2025-25-5"
---

## Day 1: Brainstroming (May 25)
I knew that I had wanted to create a custom devboard that would both beat every devboard on planet earth in value and features. My first step was choosing a micro-controller. As I had already designed devboard around the weaker rp2040, I decided to step things up with an RP2350B. ![image](https://github.com/user-attachments/assets/9cd9381a-98af-4fcb-982c-be620f0d517f)
This would have some 48 GPIO, which should be ample for any maker. As mentioned previously, I wanted every featuer that I could afford to put into the board, and with a budget of $150 USD, I felt I definetly could get a lot done. After much contemplation, I decided that I wanted to add the following featuers:
1. WIFI
2. A built-in OLED
3. GPS
4. an IMU
5. Built in battery holder
6. BUilt in battery charger
7. A 5V output line
8. A 3.3V line
9. USB-C and USB-micro input ports
10. USB-A / USB-C output ports (for phone-charging, etc.)
11. D2 - A MicroSD card reader
12. D3 - A high current H-Bridge
And hopefully more to come, though I don't really know

Anyways, after getting my goal sort of set. I decided to get ChatGPT to help with some more brainstorming, as I was pretty uncertain about the programmablity, as I would love to have a high-performance board that anyone could use easily.
This was probably my biggest mistake
The way ChatGPT explained the WIFI stuff was with basically no detail, and no matter how much I prompted it, it gave me nothing useful. What a waist of an hour. 

I decided upon using a 4 layer PCB, using easyEDA to make it as quite frankly Kicad is one of the most annoying peices of software I have used (That's probably because I'm used to using easyEDA) The layers would be like this
1. Signals
2. Ground
3. Power
4. Signals

So then, after bothering with all of this I finally set out to start the desing of the board. I looked through those datasheets, and immidiately found my first problem, the power supply. It uses some weird switching super-sensitve powersupply, and as of now I am still working upon a solution.

2 hrs later

Finally found a half solution, though I don't know if it will really work. It is an absolutely essential part of the board. IDK what to do.


**HOURS COMPLETED: 6 (*TOTAL:6*)**

## Day 2: Starting Power and WIFI (May 26)

Ok so there is this weird inductor that the rp2350 uses, so I took a deep dive into the schematic pages and the guidlines, and I think that my current design will, in fact, work.

On the other hand, getting wifi and stuff to work seems like it is going to be the biggest challenge. Getting wifi is honestly the most stupedest and hardest thing I have worked on so far. What, after like an hour of datasheet diving, I found out that to get the official stuff to work it is going to be way to hard, so I am going to add another board onto the thing, an esp32 board, making this have 2 CPUs: you can chose either one to work with, or both. This is going to make power delivery and stuff more complicated, and it is going to require more USB ports to be able to program this effectively, not to mention that as WIFI is so hard to get working it is going to require some very complicated wiring. With those weird things, I think I will have to use a 4-layer pcb, especially as USB can be very finiky with a ground that is far away.

Also, I added a Micro-SD card reaader as a feature I wanted. After seeing how complex wifi is, and how long it took to get working, not to mention the fact that I now have two processors to take care of and make everything work, I am thinking of expanding my budget to the $350 that the advanced projects have availible. Just as the advanced projects page said, I saw that my previous experience was really helpful.

Ok I have gotten everything started, and progress is slow but steady. I have finished the 3.3V to 1.1V switching converter, a big headache in and of itself. Then, I finished the buttons. 

The switching converter is what I was talking about the problem yesterday, and not only is it painful with the schematic, but as there are so many things so densly packed, it is hard to get all the wires doing things even with all of these layers.

**HOURS COMPLETED:4.5 (*TOTAL:10.5*)**

## Day 3: A bit of studying (May 27)

Just a did some studying of the schematics of the rp2350. I also thought of adding an H-bridge, so that you don't have to worry about external wiring. I also did some pcb desing, mainly with the flash.


**HOURS COMPLETED: 1 (*TOTAL:11.5*)**

## Day 4: WHY WIFI????????????????????????? (May 28)

I'm a be honest: wifi might not work. One after and other after another, the problems keep coming. The ESP32 that I was going to use has no real way of connecting it to a USB port, but the other one that I could use requires JLCPCB Standard Assembly. I honestly don't know what to do, as Standard cost $25 vs Economic at $8 for the setup costs. See below for the image of the ESP32 that I was going to use.
![image](https://github.com/user-attachments/assets/4645a7f4-61fe-40be-840f-a30065d8d3ce)
I want to use:
![image](https://github.com/user-attachments/assets/cf4687d3-f92a-421c-b39e-30699047fef8)
But I don't want to spend an extra $18 to use it 😿

On the other front, it seems like the rp2350B part of the board should come along pretty well, as my desing looks close enough to the recomended design.

**HOURS COMPLETED:1.5 (*TOTAL:13*)**

## Day 5: Its Decided. (May 29)

You know what. Enough is enough. The ESP-32 will not bully me anymore. I will use it. I will command it. IT WILL BE MINE!!!!!!!!!!!!!!!

What I mean? I'm going to use the ESP-32-VROOM-32D-N16. I WILL USE IT. After soooooo much research, I will find a way to connect it to a USB port because I have to. I will get wifi.

![images](https://github.com/user-attachments/assets/a294a33f-a145-49bb-abcf-6a5ca37a81ab)

And this is the board I will use ^

Yeah thats about all i got done just some research and hard-core decision making. Gods this took too long.

Ooh and adding a radio might be nice to add.

*About an hour later

Time to see how to connect the ESP32-WROOM-32D-N16 to wifi.

*Studies for an hour

Ok. I think I got the schematic for the USB-UART chip. It wasn't that hard, however whoever made the datasheet deserves to be fired immedieately. If you want you product to sell, make the date sheet read able at least! To make sure that no one has to experience this pain again, I have linked the schematic below:

![image](https://github.com/user-attachments/assets/88ec6c36-8044-4527-9dd1-a58e0d8a17e2)

P.S. ChatGPT hallucinating half the time definitely didn't help. It thought VCC was GND!!!! and then after I corrected it, it the TXD was GND. Bro why can't AI be better ☹️

**HOURS COMPLETED: 3.5 (*TOTAL:16.5*)**

## Day 6: More ESP32ing (May 30)

I solidified my decision to use the ESP32-WROOM-32D-N16 over the ESP32-WROOM-32***E***-N***14***. This is because for the minimul power increase and newerness of the 32E, I would lose out on 12 MB of flash, and to the ultimate makes who would be using my board, that would be simply unacceptable. Like honestly, why whould I take 4MB of memory (on the ESP32) when I only have 16MB on the RP2350, and I could get the 32D which has 16 MB?

Anyways, the REAL work I got done was getting the main power chain of the ESP32:

![image](https://github.com/user-attachments/assets/46f60d95-a8ac-4adc-ba9a-b78622f61f63)

and I also got the interchip communication part done. This would be how the two different chips will comunicate. I also researched all of the pins on the ESP-32 that can't be used. In case you are also making a similar board, know you can't use the SD pins (SD0-3), the CMD, CLK, SENSOR_VP or the SENSOR_VM pins. This also means that UART 1 of the ESP can't be used as it is used internally, so we will use UART 2. Gods I think this took too long.

Anyways, I'm really holding off on the RP2350 part of the board as it is pretty similar to the RP2040, and I have a custom devboard (designed for OnBoard) coming in the mail, and I can see if I made any fatal mistakes that I can learn from and not do on this board.

**HOURS COMPLETED:1.5 (*TOTAL:18*)**

## Day 7: Ethernet? (June 2nd)

I've been having headaches for the past few days, but today I had an idea of using Ethernet. After a bit of research, though, it felt a bit too much, as I already have so many features, including wifi on the ESP32.

**HOURS COMPLETED: 0.5 (*TOTAL:18.5*)**

## Day 8: Coding. (June 3rd)

Ok, well using the main chip is going to be a bit hard, as currently there isn't much micropython support for the RP2350B, however the esp32 stuff should work well, and there is some sort of documentation here:
https://micropython.org/download/WEACTSTUDIO_RP2350B_CORE/
Lets hope it actually works.

**HOURS COMPLETED: 0.5 (*TOTAL:19*)**

## Day 9: Battery Charging (June 4th)

![C379389_C379389-ÕýÃæ](https://github.com/user-attachments/assets/88673be3-e093-4e10-9999-526f04c17d26)

I am thinking of using these chips for battery charging, two of them per board, so that they can individually charge the batteries, though I do not know if it is a good idea. The problem is, these chips require an input voltage higher than an output voltage, so I might just find a chip that can do that.

Ok. I have a new idea: I am going to have a boost converter which will then feed into the TP5100 and stuff and actually charge the thing. A plus of this is that we will be able to get a 12V line!!! This, and I am also starting to decide upon which DC motor driver to use, as I want the 4A rating.

Oh also I want a built in multimeter so that I can access battery voltage and stuff through a not janky circuit as in my current devboard.

Btw, I also attended the meeting :)

**HOURS COMPETED: 4 (*TOTAL:23*)**

## Day 10 (June 5th)

Just a quick study period, today I spent just a few minutes working on making choosing a boost converter (not chosen yet) and then working on some code and stuff that I would include to drive the SSD1306. Because the default font size and stuff is so small, I will be using a special custom font size maker and custom font maker so that whoever uses this OLED will be able to use whichever preloaded font they want to use. As the flash space will be 16 + 16 MB, I feel its ok to load like 5 different fonts and sizes, as they won't take too much space.

**HOURS COMPLETED: 0.5 (*TOTAL:23.5*)**

## Day 11: NitPicks (June 6th)

Today, I worked upon seeing which of my features that I want will really work. A THT display would be nice, but I don't think that it is a good idea. I might come back to it latter though. Anyways, I think that a SD card holder is a very good idea, as they are dirt cheap and there are a billion on JLCPCB parts.

![C393941_C393941-ÕýÃæ](https://github.com/user-attachments/assets/1cb81d69-c512-49cc-99c0-57239e36b1d9)

Something like this ^ should work.

On a sadder note, however, GPS looks like it is going to be very expensive to integrate. With each module coming to almost $6, it will make each board's cost be very high. It would probably put the board out of reach for too many people 😢

**HOURS COMPLETED: 1.5 (*TOTAL:25*)**


## Day 12: A decision

After much contemplation about the previous topic, I have decided that I will, in fact, make the best possible devboard. I hope to make two versions, so that incase I mess something up on the first one, the second will be absolutely perfect, at least if the budget will allow.

Seeing as I think I can make this an advanced project, with the availible $350, I sure can include GPS and all of that stuff, though that comes to arround $70 per board, and holy moly is that a lot. 🤑 Anyways, I am considering sourcing some of the components and then soldering them my self, though getting footprints and stuff to work properly and the risk that I mess up might make the few dollars I save not worth it.

**HOURS COMPLETED: 1.5 (*TOTAL:26.5*)**

## Day 13: USB splitter?

You know what would be really cool? Making this breadboard also have a USB splitter so that anyone can program as many boards as they need, all at once. I would also love to use the inbuilt batteries to power the USB ports, so that it can also be used to charge a phone that is providing it with data. I am thinking of using the FE1.1S as I saw someone else using it in the slack.

![Terminus-HE11SSS0P28](https://github.com/user-attachments/assets/1152c7c6-594e-4ce1-8ec0-b6321c880a6a)

**HOURS COMPLETED: 0.5 (*TOTAL:27*)**
