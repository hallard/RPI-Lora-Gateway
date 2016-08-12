Raspberry PI Lora Gateway/Node for RFM92/95/96/98/69HCW Modules
===============================================================

<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-mounted.jpg" height="30%" width="30%" alt="Raspberry PI Lora Gateway/Node">    

This shield is used to hold one or two HopeRF [Lora module][4] Software with Raspbery PI plus one FM12B/RFM69CW/RFM69(H)W.
it's the parent of the small [LoRasPi][11], so please look at LoRasPi [readme][12] to see features and software links.

This board has been mainly inspired from [Uptronics][14] expansion board on which I added some features.

Note, this board is not a real LoraWAN concentrator, if you need a real concentrator with multiple channels and fully compliant to LoraWan stack capabilities, please see thethingsnetwork gateways[wiki][1] 

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
   GPIO5   <---->  Reset
   GPIO25  <---->  DIO0 
   GPIO24  <---->  DIO5 

Raspberry PI   RFM9x Module 2
   CE1     <---->  SEL
   GPIO6   <---->  Reset
   GPIO16  <---->  DIO0 
   GPIO12  <---->  DIO5 

Raspberry PI   RFM69/12 Module 3
 IO26/CE0  <---->  SEL
  GPIO13   <---->  Reset
  GPIO23   <---->  DIO0 
  GPIO12   <---->  DIO2

Raspberry PI   On Board LEDS
   GPIO4   <---->  LED 4
   GPIO17  <---->  LED 17
   GPIO18  <---->  LED 18
   GPIO19  <---->  LED 19
```

### Schematic  
![schematic](https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-sch.png)  

### Boards  
<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-top.png" alt="Top">    
<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-bot.png" alt="Bottom"> 

### Received boards 

<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-top.jpg" height="40%" width="40%" alt="Top">    

<img src="https://raw.githubusercontent.com/hallard/RPI-Lora-Gateway/master/images/RPI-Lora-Gateway-bot.jpg" height="40%" width="40%" alt="Bottom"> 

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
