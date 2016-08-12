Raspberry PI Lora Gateway/Node for RFM92/95/96/98/69HCW Modules
===============================================================

<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-mounted.jpg" height="40%" width="40%" alt="Raspberry PI Lora Gateway/Node">    

This shield is used to hold one or two HopeRF [Lora module][4] Software with Raspbery PI plus one FM12B/RFM69CW/RFM69(H)W.
it's the parent of the small [LoRasPi][11], so please look at LoRasPi [readme][12] to see features and software links.

This board has been mainly inspired from [Uptronics][14] expansion board on which I added some features but it's not a real LoraWAN concentrator, if you need a real concentrator with multiple channels and fully compliant to LoraWan stack capabilities, please see thethingsnetwork [wiki][1] dedicated to gateways.

By the way, with Lora modules installed on this board you can have it working as a Single Channel Gateway or a LoraWan node. For testing, demo or small projects, it can be enought.

Quick features 
==============

- Placement for two RFM92/95/96/98 Lora module (IE one 868MHz and one 433MHz, or 2 channels 868MHz)
- Placement for one RFM12B/RFM69CW/RFM69(H)W classic module
- Placement for choosing single Wire, SMA, u-FL or Thru Hole PCB Mount (Right Angle Tor straight)
by Eightwood Antenna type
- Vertical Antenna placement is possible (easier to drill RPI top enclosure)
- 4 x LED for visual indication
- Each Module reset pin can be connected to a RPI GPIO

Boards arrived from ElectroDragon, all is working as expected.

Detailed Description
====================

Look at the schematics for more informations.

SPI connexion is classic (MOSI/MISO/CLK), Chip Select is CE0 for Module 1 and CE1 for Module 2. Module 3 can be choosen between CE0 and GPIO26 with on board jumper switch.

```
Raspberry PI   RFM9x Module 1
   CE0     <---->  SEL
   GPIO5   <---->  Reset (JP5)
   GPIO25  <---->  DIO0 
   GPIO24  <---->  DIO5 

Raspberry PI   RFM9x Module 2
   CE1     <---->  SEL
   GPIO6   <---->  Reset (JP6)
   GPIO16  <---->  DIO0 
   GPIO12  <---->  DIO5 

Raspberry PI   RFM69/12 Module 3
 IO26/CE0  <---->  SEL
  GPIO13   <---->  Reset (JP13)
  GPIO23   <---->  DIO0 
  GPIO12   <---->  DIO2

Raspberry PI   On Board LEDS
   GPIO4   <---->  LED 4
   GPIO17  <---->  LED 17
   GPIO18  <---->  LED 18
   GPIO19  <---->  LED 19
```

### Hardware Setup

Nothing really complicated, you can wire Reset of each module on a GPIO pin if you want to be able to hardware reset then using software, in this case put jumper on JP5 for Module 1, JP6 for Module 2 and JP13 for Module 3. JPx number is the GPIO so JP5 is for GPIO5 ;-)

If you want to use Module 1 and Module 3 you need to set JP1 (Chip Select of module 3) to IO26 since CE0 is used by Module 1.

### Software Setup

I'm working on two libraries port and Single Channel Gateway to work on Raspberry PI, links are here   

- [LIMC][20] to be LoraWan compliant 
- Excellent [RadioHead][22] library for RFM69, RFM9x modules (and lot of others)
- The Things Network [Single Channel Gateway packet forwarder][24]

I forked all repos to tweak them, but since I'm not sure original authors would like to merge my changes just use my forks. For now it's just in coding state, please be patient, code will be better in some days.

For reference, original libraries and code are [Arduino-LIMC][21], [RadioHead-LIMC][23], [Single Channel Gateway packet forwarder][25]

### Schematic  
![schematic](https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-sch.png)  

### Boards  
<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-top.png" alt="Top" height="50%" width="50%" >&nbsp;&nbsp;<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-bot.png" alt="Bottom" height="50%" width="50%"> 

### Received boards 

<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-top.jpg" height="50%" width="50%" alt="Top">&nbsp;<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-bot.jpg" height="50%" width="50%" alt="Bottom"> 

You can order the PCB of this board [PCBs.io][13]. PCBs.io give me some reward when you order my designed boards from their site. This is pretty good, because I can use these rewards to create and design new boards and order boards for a discounted price and share new boards.

### Assembled and mounted board

Here is my testing board, as you can see, 3 modules on it    
- Module 1 (top left) Lora RFM95 868MHz
- Module 2 (bottom left) Lora RFM98 433MHz
- Module 3 (right) RFM69HW 433MHz

<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-mounted.jpg" alt="Mounted">    

##License

You can do whatever you like with this design.

##Misc
See news and other projects on my [blog][2] 

[1]: https://www.thethingsnetwork.org/wiki/Hardware/Gateways/Overview
[2]: https://hallard.me
[4]: http://www.hoperf.com/rf_transceiver/lora/
[5]: https://github.com/hallard/single_chan_pkt_fwd
[6]: http://www.daveakerman.com/?p=1719
[7]: https://store.uputronics.com/index.php?route=product/product&search=lora&product_id=68
[8]: https://PCBs.io/share/zkD74
[9]: https://github.com/matthijskooijman/arduino-lmic/
[10]: https://github.com/hallard/RadioHead
[11]: https://github.com/hallard/LoRasPI
[12]: https://github.com/hallard/LoRasPI/blob/master/README.md
[13]: https://PCBs.io/share/zvxQ8
[14]: https://store.uputronics.com/index.php?route=product/product&search=lora&product_id=68

[20]: https://github.com/hallard/arduino-lmic
[21]: https://github.com/matthijskooijman/arduino-lmic
[22]: https://github.com/hallard/RadioHead
[23]: http://www.airspayce.com/mikem/arduino/RadioHead/
[24]: https://github.com/hallard/single_chan_pkt_fwd
[25]: https://github.com/jlesech/single_chan_pkt_fwd

