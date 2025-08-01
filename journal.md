---
title: "CustomDevBoard"
author: "Madhav"
description: "A devboard with every imaginable feature."
created_at: "2025-25-5"
---

125 Hours

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

I also just labeled EVERY GPIO:

![image](https://github.com/user-attachments/assets/5af3c19c-0bc1-4fb3-81f7-071fb43c97ad)![image](https://github.com/user-attachments/assets/b8abebca-b66f-4032-aafd-c40fe10cec63)


**HOURS COMPLETED 3 (*TOTAL: 48.5*)**

## Day 21 (June 23rd): Realization

So today, I got to work routing some wires, mainly on the ESP32 side. I had done a lot of thinking about where to put the headers, and starting wiring them up. But then I hit a brick wall

![image](https://github.com/user-attachments/assets/d2327552-2e40-4371-bb02-25ec8fbae5f9)

If you see the image, I'll have to wire throught the battery mount hole, or place vias. Not a big deal. But, I then thought that I should put down all the through-hole components, the blocking ones, the most important and unmoveable ones down first.

Enter: the main display:

![image](https://github.com/user-attachments/assets/c2c383c8-316e-441a-bdad-89b83fa76640)


Now this is a big chunky thing which must not be moved around, and idealy would fit in between the batteries. But when I went to move the batteries, they always collided with another part. So, after way too much thought, I have decided to rewire most of the stuff :(  At least I hadn't done anything too complicated so far.

Hence, the rewiring. Adjust the wires is really a big pain, not gonna lie. But hey, atleast it looks beutiful. I am probably going to have to move these wires to the bottom layer though :(

![image](https://github.com/user-attachments/assets/f9186bba-f33a-4971-8d72-6e73918d021e)

![image](https://github.com/user-attachments/assets/701f7d54-6842-420d-bc03-c5172bc464c8) 
![image](https://github.com/user-attachments/assets/85e3b911-04ec-433d-a934-39a782abc03c)

**HOURS COMPLETED: 5.5 (*TOTAL: 54*)**

## Day 22 (June 24th): GPIO

Today, I just worked on routing the GPIO. I had to restart a few times, but it is epic how it looks right now.

![image](https://github.com/user-attachments/assets/75178c3b-eb8a-4fff-8cf7-1f06a4b71a78)

You just have bands of red, blue and green. Yes, three colors. I want to keep my ground plane solid, so I am only going to use the three for routing. If I need more (I probably will) I'll just use a six layer pcb. The advantage is that it will be way easier, and it comes with ENIG for free, so my boards won't be as likely to be messed up. (With HASL 1/5 of my boards basically didn't work)

I also changed the layer of the ESP32's wiring to the bottom, as that way I will be able to SMT components on top of them.

I also spent some time on the LCD, nothing too visible, but just double checking everything and stuff for it's SPI connection.

**HOURS COMPLETED: 4 (*TOTAL:58*))

## Day 23 (June 25th): More GPIO

So today, after way too much time, I HAVE FINISHED THE GPIO!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Here are the photos — I had to use three layers to route them all :(

![image](https://github.com/user-attachments/assets/16fff5b8-c78c-4abb-9393-b23648398f87)| | | |
![image](https://github.com/user-attachments/assets/a449a427-58e7-42ab-ac22-3434bcd3aa03)
![image](https://github.com/user-attachments/assets/df443856-6fde-42b3-ba2e-097ed050c5ab)

I probably have like a million vias as of now, but I have not had to another layer, so as of now, a 4-Layer PCB should work 🤞

it looks so cool I decided to add even more images:

![image](https://github.com/user-attachments/assets/2c6a1f7e-eca4-4db7-8b70-cbdf7a23c3fc)|![image](https://github.com/user-attachments/assets/5a9569ff-a287-4212-8fd4-b2ace614f922)

I'm also now working on wiring the ESP32 power and USB, and am wondering if I should add the capacitive touch sensors.

After burning more time, and I finished the main part of the INA226 circuitry!!

![image](https://github.com/user-attachments/assets/3eaccae8-665b-4411-988c-bca5d2d2eae7)

And, you know what? As a bonus, I even finished the ESP32 part!!!

![image](https://github.com/user-attachments/assets/5f840c00-9002-44d4-8dea-44769870207d)

**MORE BONUSES:** I started an OLED, added a switch for the INA, and um moved the battery!

**HOURS COMPLETED: 5 (*TOTAL:63*)**

## Day 24 (June 26th): More GPIO

Remember how I had said that I finished the GPIOs? well I had put them in the wrong way :(

So after a redesign, I corrected it, but had to go onto the fourth layer :( I think I might have to use the 6 layer PCB :(

![image](https://github.com/user-attachments/assets/8965be6b-5d10-4a56-ab06-8686a0c2a22b)
![image](https://github.com/user-attachments/assets/6478372e-45d0-4cc7-b5cc-c89f8fde2c33)
![image](https://github.com/user-attachments/assets/e898b3d7-9643-4a74-b32c-89e761b15ab8)
![image](https://github.com/user-attachments/assets/52ab2978-d2b2-46fb-911b-ff6840e4259d)

So well here are the pictures of the four layers.

I then went on to designate a set of pins for the I2C connection, and complete the circuitry based upon it!

![image](https://github.com/user-attachments/assets/90ee975e-15c8-4556-81ae-1f200a4d9c0c)

As a side note, I am really wondering how people get their stuff done so fast. Just remodelling the GPIO took me a good 2+ hrs, and then this INA226 datalines stuff took me like another 1+ hr. The biggest reason I can think of is that my board is very dense, and that I am double and triple checking my work? Oh well. Just wanted to put my thoughts down.

Oh yeah, I also moved the battery cases and stuff around so that there would be maximum clearance, and as the following picture suggests, every movement is an absolute pain.

![image](https://github.com/user-attachments/assets/ad8e9b70-9c3b-4a33-9f80-86bcbbab7254)

Just saying, its such a big pain to change even the smallest things. For example, I had hidden the 3.3V and GND nets, and when I show them, even though I have 2 layers with each (3.3V on Top and Inner 2) (GND on Inner 1 & Bottom) it is still a pain to get everything to work because of how dense the wires are around the headers.

FINALLY!!

![image](https://github.com/user-attachments/assets/e9ea6b73-743a-4c80-b07a-4d97f6e2fa44)

I am going to go work on the GPS. I think it is probably sensitive and will require everything else to revolve around it. First up, chosing a module. I know I talked about it before, but I am going to restart as there wasn't many good choices, and now that I have components from LCSC anyways, I have more options.

Ok. there are 2 different types of GPS modules. Those with built in antennas and those without. I need to now figure out which to use. I am leaning towards those with built in ones, as they will be significantly easier, but also harder to find and more expensive. Let me go do some thinking.

**HOURS COMPLETED: 5.5 (*TOTAL: 68.5*)**

## Day 25: June 27: GPS

I never knew that GPS is soooo haarrrrrrrrrddd.

Bro I've literally spend like 2 hours looking for a suitable GPS module, and I can't find a single one. After 2 hours. TWO!!

Well I wish I had something to add but thats it. :( I couldn't find a half decent GPS chip. I might need to use a premanufactured one, but that would just be sad :(


I HAVE GOOD NEWS!!!!!!!!!!!!!!!!!!!!

I found a board!!! It looks like the L80RE-M37 should work, and its less then $5 per GPS module!!!!!!

I don't have to go into tomorow in dispair!

![image](https://github.com/user-attachments/assets/61769293-c7c7-45dc-abe2-2259c684c9f1)

I got a bit side tracked and fixed a small problem with the INA, but I came back to the GPS pretty fast. I am now facing a dilemma. Which GPIOs should I use for the GPS. On the one hand, I can use official UART pins, but then that leaves the user with none availible. Or, I can use any random pins. By doing this, I will have access to a high-speed UART for whatever I want to do, and well, yeah. I am thinking as the GPS module is pretty expensive, I might as well use the official pins, but that leaves no UART on either the RP2350B or the ESP32 open. What to do.

*A bit later

I think I have decided. I am going to use the official pins. More specifically GPIO 12 & 13. They are pretty easy to use, not in the highest density part of the board, and are the official UART0 TX and RX pins. I just feel that the risk is not worth the reward. I could maybe test UART on not official pins, but if I experience data loss, it will be really hard to debug :(

Ok! I finished the GPS part, but I have to say, it wasts a whole ton of space.

![image](https://github.com/user-attachments/assets/8b75ff12-eb94-4f45-a5b6-144eba2bd8aa)

^^Where the red center box is, you can't put any components, and ideally all high-frequency stuff needs to stay away, such as wifi, the microcontrollers, the LCD, and the OLED. the OLED is still a touch too close for my liking, but not much I can do. I could move it away, but thats a lot of work. I might just do it.

You know what? I just did it. I moved the OLED so that the GPS can work with full ability. Apparently, its so strong it can work indoors! Only time will tell...

Threre is still lots of space for more components

![image](https://github.com/user-attachments/assets/1c6cb529-0fca-4796-bae8-4010c87b2531)

Though the inner layers really are sort of filling up. Even then, there is still lots of space. I am thinking that next I will work on the MicroSD card slot as it'll probably also be sensitive, especially with that GPS module there. The IMU will also need to be not around some components probably, so I will make sure to also do *it* afterwards. Then, space (almost definitely) permitting, I'll add the battery charging circuit, the 5V line, the H-Bridge, and um well I'll see.

**HOURS COMPLETED 3.5 *(TOTAL:72*)**

## Day 26: June 28

I did some reaserach on the IMU that I am going to use, and, well, I have to say that it is going to be a pain. I couldn't find many that were supported by JLCPCB's manufacturing process, and the one that was, well, that ran on 1.8V. So, basically, I am going to have to at a 1.8V line and a voltage shifter. Sadness. I started reading the datasheet too.

**HOURS COMPLTED 1 (*TOTAL:73*)**

## Day 27: July 1st: CANADA DAY !!!

On the day of our contry, I started with the circutry to convert the power stuff at 1.8V to the 3.3V.

I decided on a power supply (SSP6206-18NR) and worked on learning how the voltage level changer works.

**HOURS COMPLETED: 2 (*TOTAL:75*)**

## Day 28 (2nd July): IMU!

I finally finished wiring up all the IMU stuff!

![image](https://github.com/user-attachments/assets/39c7c519-c87d-40b9-aed4-8dc7445de9c9)

The three pin components on the left are the MOSFETS used for logic level conversion, and on the bottom right is the power supply. Its so crazy how dense all these components are.

I am now going to go work on the auto-reset stuff. Also, it just takes so much time because every change just makes it so that I need to redo so many things :(

I also tryed making the INA circuit better, but accidentally made it worse so I had to undo it all.

HOURS COMPLETED: 2.5 (*TOTAL:77.5*)**

## Day 29 (JU3): SD Card

Today, I worked on the SD CARD!!!!

![image](https://github.com/user-attachments/assets/6aab8c85-9cfc-452d-86ca-872c3be74631)

Just finding the right spot to put it took me like an hour. I settled on curving the pcb border around the outside so that it is as easy as possible to use the card. Just one problem:

![image](https://github.com/user-attachments/assets/6fb6751f-976a-42b3-8ecd-843de2c04ba5)

The datalines need to go from one side of the board to the other. They are going to end up being a massive block.

I also worked on wiring the card, but I am very uncertain wether its going to work. Here is the schematic I settled on after consulting the Adafruit datasheets and stuff.

![image](https://github.com/user-attachments/assets/a6cab297-7f4f-4d77-819b-dfa5589b65b6)

I really hope this is going to be okay. I am going to go send this to the hardware slack and see if they think its going to work.

HOURS COMPLETED: 2.5 (*TOTAL 80*)

## Day 30 (JU4): POWER!

Today (or rather yesterday as I am post-event journaling) I worked on **POWER!**

I wanted to use many more 3.3V LDOs, however I can't do that because they don't share their load effectively. So I am going to have to work on a buck converter setup. They are significantly more efficent, and thus you can use all the components. I think I will go with the LMR33630ADDAR connected to the battery and the normal one connected to the USB. (Sorry for the lack of detail I don't really remember what I really did yesterday)

HOURS: 1.5 (*TOTAL:81.5*)

## Day 31 (JU5): Datasheets

So, I noticed that the official RP2350 datasheet suggested the NCP1117, so I will check the datasheet.

You know what? This stuff just seems too hard. I might continue to do some research, or hope for the best.

Ok well in the meantime I double checked the datasheet of the ESP32 and added more decoupling capacitors and stuff

HOURS: 2 (TOTAL:83.5)

## Day 32 (JU6): ESP32.

You remember how I said I finished the ESP32 part? Well I redid it to include all the auto-reset firmware and stuff.

![image](https://github.com/user-attachments/assets/caa6584b-1345-4a75-8a21-68366c411316)

That took a lot of time, but it was totally worth it.

For context, look at the previous image:

![image](https://github.com/user-attachments/assets/893f9573-6654-4332-baa0-4292d7b4c1c4)

You can see that it looks so much better, it has more components crammed in, and is just all-round cool. Also, I am now using the official circuitry, so it is more likely to work.

HOURS: 3 (TOTAL:86.5)

## Day 33 (JU7): Double Check

Today I took the time to double check as much of it as I could, with the help of chatgpt.

I am a bit worried about the USB lines, however I have heard that they are very forgiving, so I should probably be okay.

Well not much to write as all I did was double checking...

Oh, and also, I am probably going to finish battery charging next time.

HOURS: 1.5 (TOTAL: 88)

## Day 34 (JU8): 3D

Just look at all of these images: they look soo good!!!!

![image](https://github.com/user-attachments/assets/ef96d7a7-d228-48a4-a530-e98cbe265d65)

![image](https://github.com/user-attachments/assets/556c4164-7122-43c4-9f30-7e2329e7d6bb)

![image](https://github.com/user-attachments/assets/a3dc1a1d-f252-4bae-bdb6-eaa530642592)

Anyways, I'm going to go work on the battery charger.

I have so much space. I don't know what to do with it:

![image](https://github.com/user-attachments/assets/31e533c8-ddc9-41c0-827f-5cfa528e41a9)

The problem is, however, that i can't have throughhole components where the green silkscreen (for the batteries) is:

![image](https://github.com/user-attachments/assets/bd657098-3189-4d5c-b9e2-46df909eb6c0)

Ok so I decided I am going to take a look at some cellular stuff, and it all seems way too expensive, so I am not going to do it. I am putting off doing the battery charging because it will be a pain. I will need a 12V supply, and with that I will have to then feed into the charger and the charger will also be painful to work on :(

**SOME TIME LATER**

Oh I really procrastinated. I double checked my clearances, and decided I can put THT components where the batterycases are, however to do so, I had to move the entire GPS assembly around, which led to some rewiring on the IMU.

![image](https://github.com/user-attachments/assets/229a34dc-10aa-4960-a115-94bb3617f9f8)

I also added a 0.02 ohm shunt resistor for the INA so that the user can use the INA's current measuring feature.

![image](https://github.com/user-attachments/assets/b3e9b4d1-67f3-4d7d-b2f4-c4d723e68926)

I also took a look at some higher current LDOs so that I could power everything without super heating the board.

### YESSIR!

Ok. I did it. I got this stuff to COOOK!!!!

So, I got some LDO's from the battery, so you can have either USB, Battery, Or both connected at the same time. This way, if you suddenly disconnect one, the other can take over and operation never halts. I am still experiencing the current problem, as the LDO will probably overheat if everything is running togeather, so I am using 2 LDOs, one for the ESP, one for everything else. I might chose to add a buck converter later on, though it should be ok as it is.

In terms of battery charging, I am going to use a dedicated USB-C port for it. This port will be set to the highest voltage USB-C can provide, 20V, and then will use a buck converter to reduce the voltage to 12V. Then, the charging circuit will use that, and all will be well. Now, I have to make the actual charging circuit...

One small problem, the LDO I am using for the 12V line can only output 1.5ish amps, so I am going to have to find a way to limit the TP5100. But as a plus, I now have a 3.3V, 5V, 12V, and 20V line when USB is active. (without USB-C I only have the 3.3V line, with a 5V line to maybe come)

![image](https://github.com/user-attachments/assets/9a4280f4-dbcb-4c1e-a085-b86a009d4b37)

![image](https://github.com/user-attachments/assets/9fa966c2-d9ba-4a7c-91c0-01da8076d638)

![image](https://github.com/user-attachments/assets/2878c0a3-37e7-43a4-9514-93f0d39c12d1)

![image](https://github.com/user-attachments/assets/2c65bbec-616f-4c2e-bccd-11e055ae8041)

I might finish the TP5100 and then work on the 3D case after...

HOURS: 6 (TOTAL: 94)

## Day 35 (JU9) BATTERY CHARGING vvvv

So I was worried about the over-heating and stuff, so I used the direct connect for the PCB copper layers, however I just Goolged some downsides, and that led me into a rabbit hole of this stuff, but I think I will be ok, though soldering quality may be affected. I really should get ENIG to counteract, but its so expensive :( (1hr)

Time to go copy the TP5100 example schematic ...

Ok. It was way more work then I was thinking to get all the schematic stuff working, but hey, I think I did it! Below is the schematic, the bare bones schematic. I chose not to include some of the features, etc, and limit the charge current to 1 amp as it was easier to find the appropriate resistors and stuff. The problem is, this thing requires so many unique components that my bill probably went +$30. That is sad, but a something that adds great value to the board...

![image](https://github.com/user-attachments/assets/223f089c-6756-41d8-8f42-d8c091857b12)

OH MY GOOD LORD

I jus realized that i was using 10***P***F capacitors not 10 ***U***F capacitors. I just went through them all, double checking everything. Another thing is, I was using 0402s, which means that they can't hand >6.3V, which a few of my circuits were using, so then, again, I went through them all, and changed the higher voltage ones to 0603s. oh my lord. If I had missed this, my entire board would not have worked, and I wouldn't have knon why...

anyways, back to the topic.

Here is the charging circuit:

![image](https://github.com/user-attachments/assets/362a580b-8782-4024-a26a-0867d61943ca)

(I added a decoupling cap and a 3 ohm resistor, as the datasheet said) Here is the PCB image:

![image](https://github.com/user-attachments/assets/93081756-4e1b-4781-8d45-f8edffe1c44d)

This literally took my like 5 hours to completely do. I am so happy I caught my error --> I though pf and uf were the same!!!!!

Well I'm a log off. I worked way too late on the capacitor stuff, and will probably have to double check stuff in the morning...

### HOURS COMPLETED: 7 (TOTAL:101)

## Day 36 (JU10) Double-Check & User

Today I just worked upon adding some user features, leds, surge protectors, and double checking everything.

First up, surges.

I spent some half an hour studying how they work, and then wiring them up. It was pretty simple of a job for wiring, however, chosing the right one took some time

In terms of LEDs, they also took way too much time, as on my first board the LEDs were way too bright. I did all the math, double checking as I went, and got the LEDs wired up. I have one for the ESP, one for the RP2350B, one at the 20V usb, and one at the SD-card, and two for charge indication.

I also added some user features: a user LED (totaling to 6 LEDs), a user button, and a user switch. They will all be on the back side, but I guess thats ok.

And thats about it. I'll leave you with some amazing images:

<img width="1014" height="622" alt="image" src="https://github.com/user-attachments/assets/1bd14cf5-afcf-4b0e-99d9-421d077a9705" />

<img width="1088" height="849" alt="image" src="https://github.com/user-attachments/assets/ff3dfe07-6578-4b91-ad2d-f6a18329ba63" />

<img width="880" height="824" alt="image" src="https://github.com/user-attachments/assets/f1f4d298-ee3c-46ef-a9ed-4eb7d8c4c76e" />

<img width="1035" height="895" alt="image" src="https://github.com/user-attachments/assets/0c1dee62-e7d3-4475-8082-cb28c125aace" />

<img width="444" height="897" alt="image" src="https://github.com/user-attachments/assets/2a0e96e3-4cbe-4cad-8e8a-c22682bb835c" />

### Hours: 3.5 (TOTAL:104.5)

## Day 37 (JU11) Tooling, User, & Misc

Today, I worked on going over everything, adding a few features, etc.

Two of the biggest problems I saw were that the microSD card's datawires had not been hooked up (whoops!) so I did that, and that the backlight pin on the LCD was not hooked to a gpio for modulation.

I also added a simple legend:

<img width="866" height="625" alt="image" src="https://github.com/user-attachments/assets/b8ecbc69-af28-413b-ae2c-b98553195b8d" />

and this whole thing:

<img width="604" height="540" alt="image" src="https://github.com/user-attachments/assets/ee4f5591-1440-4a04-ad80-ab595e2a4abf" />

this is a voltage shifter, which takes in an external voltage > 3.3V, and converts it into another voltage, provided by the user. It took soo much time to wire everything properly, but hey it is 4 shifters in such a compact area. I might also add a power booster, basically providing like 1a ish output from an input of the user's choice.

more images!!

<img width="703" height="601" alt="image" src="https://github.com/user-attachments/assets/e52a69ab-81a6-4c81-ac6d-a24988878cd5" />

<img width="757" height="579" alt="image" src="https://github.com/user-attachments/assets/31c66b0e-4ae1-4455-aa16-7e47fabfb60a" />

I have now started looking for a mosfet to use. the AO3400A looking nice.

### HOURS: 5.5 (TOTAL 109.5) <sub> (I know this may seem much, but the silkscreen stuff voltage shifters and mounting holes really took this much time) </sub>

## Day 38 (JU 12) POWER!

Today I worked on the circuit for the power amplification, and I made sure it had everything that could possible be needed, including a flyback diode!

<img width="555" height="408" alt="image" src="https://github.com/user-attachments/assets/25f1beca-6b97-4b02-bd0e-1478172a06c3" />

As you can see, for this particular one, I feel like just placing the components to look good, and then wiring after makes it just look so much better.

<img width="955" height="610" alt="image" src="https://github.com/user-attachments/assets/e81798d6-ed3a-4a0b-ba07-51f6662b8e2a" />

Now, when density is need, however, random paterns are better,

<img width="798" height="771" alt="image" src="https://github.com/user-attachments/assets/d31a622e-c795-4ea2-beb1-c4569b4fdba1" />

<img width="971" height="594" alt="image" src="https://github.com/user-attachments/assets/3804cc12-1c36-49e7-8c37-42e59f9479e0" />

but I sort of realized that I have enough space, and maybe I should have prioritized space...

I am probably going to add one or two more sets of these power amplifiers, however using headers that can actually output that much power.

Ok. done!

I think I may have finished the PCB!!!!!!!!!!!

I checked through JLCPCB, and the grand total comes to $212.30!

<img width="416" height="270" alt="image" src="https://github.com/user-attachments/assets/68b36f99-b40e-488b-939b-345ced0df6e7" />

I am not going to lie that was sooo much work :(

Oh yeah, and as for what I did recently, I worked on adding the last power amplifier, and here it is:

<img width="699" height="385" alt="image" src="https://github.com/user-attachments/assets/3a08d811-9352-475e-a04e-d677a2ae0a7b" />

<img width="823" height="682" alt="image" src="https://github.com/user-attachments/assets/8906fcce-42ae-436f-a0e1-8277fc2b4c97" />

I spent way too much time researching about mosfet gate driving and stuff, but eventually settled on using the same thing as the other ones, just with a more powerful connector.

<img width="876" height="337" alt="image" src="https://github.com/user-attachments/assets/7573bf1b-8fc0-4035-856d-a230987433a4" />

Here are the finilized board's pictures:

<sub> top </sub>

<img width="757" height="819" alt="image" src="https://github.com/user-attachments/assets/acfaa506-9f8c-4fc8-b410-1b72d0663212" />

<img width="1206" height="755" alt="image" src="https://github.com/user-attachments/assets/8b532a40-c227-4a59-84da-7a1e1acfb426" />

<img width="437" height="761" alt="image" src="https://github.com/user-attachments/assets/76d35913-3e6b-4d22-bad2-126c5df73ac7" />

<sub> back </sub>

<img width="707" height="798" alt="image" src="https://github.com/user-attachments/assets/58a49a22-2a52-4c74-9bbb-8d52ff9054d1" />

<img width="1327" height="712" alt="image" src="https://github.com/user-attachments/assets/a7a65fd2-ccf1-4fd8-8e1b-a7fd65219843" />

<img width="675" height="885" alt="image" src="https://github.com/user-attachments/assets/a5606885-edf5-4efc-8013-534deac73089" />

Well tomorow I work on the case. I am going to do a quick job, as I have already spent 115 hours...

![5JbRW2](https://github.com/user-attachments/assets/97cf61af-8872-49ca-b90a-34f1e4367c16)

### HOURS: 5.5 (TOTAL: 115)

## Day 39 (JU 13): RTC & 3D

Today I just (not really) quicky added an RTC, on the I2C bus. There are actually a gazillion i2c thingys, so I added some address markers for each. Here is the main part of the board now. I put the RTC under the OLED.

<img width="788" height="844" alt="image" src="https://github.com/user-attachments/assets/2aa6abcd-ab1f-47b0-9bc5-fca854a18a3a" />

<img width="970" height="716" alt="image" src="https://github.com/user-attachments/assets/b0c91e2b-35e3-4cd7-8fa0-caa6a7b56f2d" />

Time to get to 3d modelling...

Ok. I did some modelling, but you know how I was slow for pcb? I am getting through this even slower. I got the side stuff to work, and now when I was doing the top piece, I kept doing something, undoing it... it is hard to get right.

### HOURS: 5 (TOTAL:120)

## Day 40. I think I have finished...

Well lets start off with a screenshot!

<img width="751" height="731" alt="image" src="https://github.com/user-attachments/assets/0d5980ff-48c2-4103-afe8-a08202119d55" />

the blue thing is my case, it is all meant to be printed in one piece, and covers the bottom.

I chose to leave the top open because I would have to design battery covers and stuff, well about my skill level.

So basically, I added stuff, removed stuff, and settled on this. At one point I was also working on a back cover, but I abandoned it.

Also, here is what it all looks like:

<img width="617" height="804" alt="image" src="https://github.com/user-attachments/assets/15a2bcfb-2a38-4ade-b0b0-315b98733946" />

Oh yeah, I also added a switch to control the power to the LCD, and fixed up a bit of wiring. I also added a ground terminal for high-power stuff.

I also have started via-ification!

<img width="548" height="489" alt="image" src="https://github.com/user-attachments/assets/e0b8a0b4-43ab-4f68-a0ed-2cccb18dff84" />

oops.. I just wasted my time. There is a function that places the vias for me!:

<img width="755" height="763" alt="image" src="https://github.com/user-attachments/assets/1cc07d24-6f0a-4e23-b60f-948e4235604a" />

and thus i finished...

will submit tomorow.

### HOURS 5 (TOTAL: 125)

## Sumbiting and tuning

Today I finished the pcb. I just added a small cr2032 holder for the back up batteries. that took some time as there are sooooo many components on the board already, but I did it. Then I just worked on submitting.

## Ordering Parts.

Today, I just worked on adding everything to my cart on LCSC...

And payed for my PCB

### HOURS 1

## Day 41: 3D printing and parts

Today, I went to the library, 10 minutes after it opened, ... and both printers were already booked for the day. I guess I will have to be earlier tomorow ...

Anyways, all the parts arrived, and as far as I can tell, are all working perfectly

#### HOURS 0.5 (TOTAL:126.5)
