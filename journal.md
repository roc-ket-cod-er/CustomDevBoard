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

## Day 14: Please? (June 9)

I really want the cellular data stuff, but even no one in the slack could help

Also, after way to much effort, I found out how to do blind vias, buried vias. I also learned how to make the board have slightly curved edges so it isn't so sharp :)

**HOURS COMPLETED: 0.5 (*TOTAL:27.5*)**

## Day 14: USB-C (June 10th)

Ok so I decided today that I am actually going to work on my devboard. So, naturally, I followed the official documentation. I started chapter 2.2, and realized that I wanted USB-C. I though it would be pretty cool, and literally everyone uses it these days so it would be very accessible.

But for some stupid reason, it is so hard to implement. In my previous board, I used micro-USB and it was actually so many times easier. But, for USB-C, you need those weird resistors, apparently you should check some pin that signals overload, and to top it all off, there are 3 main different types of USB-C.

![2023081810452061](https://github.com/user-attachments/assets/ec4592e9-7b26-4f21-9390-b9a1413b7329)

I originally was about to use the 6-pin variant, when I realized that it was for power delivery only. The worst of this all was the fact that ChatGPT started halucinating so badly that I couldn't spot a single true thing it said. I naturally lost trust in it, and getting work done without it was so hard. (Not to mention ChatGPT was overloaded for half the day)

Here is what my schematic is sort of looking like as of now. The right side is the USB_C for the RP-2350B, I will likely mirror this for the ESP32. You know what? They really should make it easier to figure this stuff out. It should not take 3 hours for the USB-C alone :(

![image](https://github.com/user-attachments/assets/bd10160c-986f-40e3-b9a9-fdca5c496e3d)

I also worked on some general routing

I think the coolest routing so far is this one:

![image](https://github.com/user-attachments/assets/1e2254b5-3268-44ec-bb2a-269eeac2f2a0)


Ok, so I started doing the real desining, and oh my goodness, I don't have nearly the board space I need. Even though the board is going to be some 100mm x 100mm, the battery holders alon take up a quarter of the space. I need. Not to mention, the first version of the board took up almost that much space, and V2 is going to have soooo many more components. The ESP-32 alone takes up so much space, I am starting to feel that I might need to find a way to have components on both sides. I am thinking of ordering the battery cases independantly and then soldering them on to the back side, and that alone should make it so that I have enough space, but then I have to pay shipping on that too, and these boards are already coming to a rediculous amount. I wanted it to be $150 for the 5, but now seeing as that is next to impossible, I am targeting $250 for the standard 5 now. The one thing that I do have on my side is that I can now pack components super close to each other, and use vias in pad. This, combined with either a 4-Layer or 6-Layer PCB shoould make it possible. Only time and a big headache will tell. (BTW, I am not nearly done diagraming, I though I would take a break and work on some actuall PCB design, as it would be a nice break. I have worked a rediculous amount today).

![image](https://github.com/user-attachments/assets/c4e85da6-7559-45c9-80e4-862a66ebdc24)

**HOURS COMPLETED: 6 (*TOTAL:33.5*)**


## Day 15: A big problem (June 12)

So today I realized a basically fatal flaw on a V1 board. Basically, the MOSFET I was going to use to prevent backfeeding on the USB port doesn't seem to really work, and I can't use a diode for this either. Like this was a really big problem, and after a good 2 hours thinking about it, I have 2 sollutions

1. Make it so that you can only use one power source at the same time
That would mean that one switch would control it: either USB or Batteries
2. Have differenet buck converters
Another thing I could do was just seperate the converters they use, so that they don't conflict, or maybe lower the battery voltage down to 5V, which is safe for the USB

**HOURS COMPLETED: 2.5 (*TOTAL:36*)**


## Day 16: Flash (June 13th)

Today I just finished the flash

![image](https://github.com/user-attachments/assets/c134b5c6-a145-4ffe-abbb-2803a39d3d19)

![image](https://github.com/user-attachments/assets/4b7e329f-8ab9-4297-89b3-f6a80e926ec6)


I think it looks pretty fire, but I think I could have squeezed it closer to the USB-C. I could have saved a bunch of space :(

As a side note, I also drew the diagram of the decoupling capacitors, and renamed everything so that it wouldn't be so hard in the future

![image](https://github.com/user-attachments/assets/bf096e9f-2c01-4103-8c95-b9eb4c4dcf3a)

**HOURS COMPLETED: 2 (*TOTAL: 38*)**


## Day 17: (June 14 & 15)

Just did some general research, and finding the right components for such niche applications is just soooo hard. Like i wanted to add and xt90 for my board as an easy way to access the batteries, but its just a pain :(

**HOURS COMPLETED: 1.5 (*TOTAL:39.5*)**


## Day 17.1 (June 16)

Just spent a bit of time looking for new parts. I then spent some time thinking about how to best integrate the batteries. This project is starting to look harder and harder the more work I put into it. Not to mention that I should be starting to finish it by now and still haven't finished the basics. Ima lock in right after I finish my homework :)

**HOURS COMPLETED: 0.5 (*TOTAL:40*)**

## Day 18 (June 20th): Main Power

So finally my summatives and exams and everything finished, and as the first day of summer break, I really got COOKING!!!

As of now, the main part is looking like this, with only the batteries mounted on the back-side. I know this is going to increase a lot of cost, but it is a nessasary evil. I will just solder on the battery things my self, after ordering for LCSC.

![image](https://github.com/user-attachments/assets/af6449eb-1f8e-4304-b804-cf4e40127a67)

So far, the most annoying thing I did today was fix up to border outline. The ESP32 needs to be a bit off of the board, and the best way to do so is on the corner. I get maximal pin access, while giving the antenna maximum clearance.

![image](https://github.com/user-attachments/assets/137661c4-4c82-4094-99d2-79706b78dc52)

The thing just is, it is so ridiculously hard, or rather confusing, to get it to work. You need to draw the polygon, right click it, and then click add... > fillets. The worst part of it all was that there is next to no documentation :(

I also looked at a bit of stuff for getting the 3D model of the pcb, and about the crystal and battery placement, though the crystal is for tommorow.

**HOURS COMPLETED: 3 (*TOTAL:43*)**

## Day 19 (June 21): Long day - Lots of work.

Ok so yah today, again, I got so much work done. But first, doesn't this look so fire (I got the main part of the RP2350 done):

![image](https://github.com/user-attachments/assets/d957cda0-e6ad-442b-8b95-da0e80a1f256)![image](https://github.com/user-attachments/assets/578f5a97-a3df-4a21-aa7f-1318afdc876a)


The density is so crazy. I guess lots more is possible with 4-layers

Anyways, got most of the capacitors in the right spot, finished the crystal:

![image](https://github.com/user-attachments/assets/a75d4d72-d227-46de-a815-83b5687d591c)

And I did some of the ESP32 stuff. All in all a very productive (though still a bit slow) day.

**HOURS COMPLETED: 2.5 (*TOTAL:45.5*)**

## Day 20 (June 22nd): Basics

Today, I finished all the basics stuff. The ESP32, although lacking documentation, was sooo many times faster to complete. Here is a picture of the top part of the board with all the components (except batteries, on back side)

![image](https://github.com/user-attachments/assets/63f106b0-6255-42a8-8964-ca990730622b)

The bad news is, however, I'm already at $84 + ~$20 shipping + 18% VAT = $122 already!!! uhhhhhh I guess I can't fit it under $150 :(

GPS alone will be atleast $30 btw. I knew this would happen, but conformation is just sad. Not to mention I might need a 6-Layer PCB and/or ENIG (as my components are delicate. last time with HASL they where barely functioning, one board almost desoldered) and this will drive costs through the roof 😿

I also just labeled EVERY GPIO on the RP2350B:

![image](https://github.com/user-attachments/assets/5af3c19c-0bc1-4fb3-81f7-071fb43c97ad)

**HOURS COMPLETED 3 (*TOTAL: 48.5*)**
