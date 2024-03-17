# DongleHider+ Framework Laptop Expansion Card

Want to use a Logitech Unifying Dongle (or similar) without having a dongle permanently sticking out and giving up on a precious expansion card slot?  

Now there's the `DongleHider+`!  

Simply (permanently) mount the dongle inside the card and still have an USB A port available!  

There even is room and solder pads for 1-2 additional dongles. Your imagination (and physics) are the only limits!

See also the [thread on Mastodon about the build process etc](https://chaos.social/@LeoDJ/112040053271880119).

<p float="left" style="display: flex; flex-wrap: wrap; align-items: center;">
  <img src="doc/DongleHider+ assembled.jpeg" width="49%" />&nbsp;
  <img src="doc/DongleHider+ installed.jpg" width="49%" />
</p>


## Compatibility Notes

The expansion card was only tested on **Windows** and **AMD** Framework **13 and 16** laptops as of right now. There the following behaviour has been observed:
- With only a dongle active, the CH334 hub IC draws around 20mA. (In addition to the ~25mA of the Unifying dongle)
  - When nothing is connected to the hub, it goes to sleep and draws <1mA. (But this is seldomly the case with a dongle permanently attached to it :P )
- Despite earlier fears, the USB 3 "route-around-2.0-hub" topology doesn't seem to cause problems in the wild, except:
- When connected to a **USB4 capable expansion card slot** and an external **USB 3 device** is plugged in, the **internal dongle stops working**, but is still displayed as connected in Windows.
  - As soon as the USB 3 device gets unplugged, the internal dongle immediately begins to work again (probably without a re-enumeration).
  - USB 2 devices seem to work without a problem for the most part, although one of the tested USB thumb drives took a few re-plugs until it enumerated.
  - This behaviour is not seen on the other non-USB4-capable expansion card slots, there USB 3 devices work great alongside the internal dongle

It's currently unclear what the behaviour would be under Linux or on Intel laptops. <sup>[You can help expand this]</sup>
  


### Dongles

This project was aimed first and foremost at Logitech Unifying dongles. But you can check if your dongle would fit by disassembling it and checking its size against the CAD model (linked below).  
Keep in mind that there is more room under / above the PCB too. (I just made the cutout so a Unifying dongle PCB would fit neat-ish)

The Unifying dongles can be disassembled pretty easily:
|||
|---|---|
| <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/7/7d/Logitech_unifying_receiver.jpg/640px-Logitech_unifying_receiver.jpg" width="200px" /> | **Gen 1:** <br>Carefully break off the plastic from the metal part using a pair of pliers. <br>(Can be glued back together, if needed)|
| <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2e/Logitech_Unifying_Receiver_USB.jpg/566px-Logitech_Unifying_Receiver_USB.jpg" width="200px" /> | **Gen 2:** <br>Slide flat screwdriver (or similar) between the metal and the orange plastic of the front of the USB a plug and carefully pry open the metal shell until it slides off. <br>[Youtube video](https://www.youtube.com/watch?v=NB5uVCrXxT8) |


## PCB
- [View the latest schematic and board view](https://kicanvas.org/?github=https%3A%2F%2Fgithub.com%2FLeoDJ%2FFW-EC-DongleHiderPlus%2Ftree%2Fmain%2FDongleHiderPlus_PCB) thanks to KiCanvas.
- [Interactive HTML BOM](https://leodj.github.io/FW-EC-DongleHiderPlus/DongleHiderPlus_PCB/DongleHiderPlus_PCB.ibom.html)
- I've ordered the PCB and assembled it myself, but it should be able to be mostly assembled by PCBA services (like JLCPCB) too. The Gerber/BOM/CPL files are provided in the [PCB/jlcpcb/production_files/](DongleHiderPlus_PCB/jlcpcb/production_files/) folder.

<p float="left" style="display: flex; flex-wrap: wrap; align-items: center;">
  <img src="doc/PCB 3D.png" width="49%" />&nbsp;
  <img src="doc/PCB assembled.jpeg" width="49%" />
</p>


## Mechanical Design

- The [CAD model](https://cad.onshape.com/documents/ed6483270486e65268e8fd84/w/d29ba2284b9bcf206122f777/e/2459b9ec86bce6d6c9526a6b?renderMode=0&uiState=65e6561b74c806687c72f766) for the shell etc. was done in OnShape.
- The PCB is fastened to the case using 3 M2x3 self-tapping screws
- Simply print the .step file from the [Mechanical/](Mechanical/DongleHiderPlus_Shell.step) folder. I printed it lying down with 0.1mm layer height and supports (for the lip on the bottom). But standing vertically (on the USB-C hole side) should work too.

<p float="left" style="display: flex; flex-wrap: wrap; align-items: center;">
  <img src="doc/Shell CAD.png" width="49%" />
</p>