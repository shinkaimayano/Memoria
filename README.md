# Memoria

A hotswap drop-in PCB for the [V4N4G0N](https://trashman.wiki/keyboards/v4n4g0n) family of keyboards.

## Features
  
- RP2040 MCU with 16MBs (128Mbs) of flash storage.  
- Has integrated aRGB LED indicators (SK6812MINI-E), replacing the soldered single-color THT LEDs of the original.  
  - These pins are broken out if you want to add underglow as well.
- Overcurrent and ESD protection.
- Curved traces, teardrops, and a hatched copper fill for a prettier look.  

The firmware, found [here](https://github.com/shinkaimayano/Firmwares/tree/main/memoria/rev2.0), can be flashed by dragging and dropping the .uf2 file into the Mass Storage Device (MSD) that shows up on the first plug-in of the PCB. Afterwards, it is recommended to use Bootmagic (by holding down the top left key on plug-in) to put it into bootloader. You can short the two pads underneath while plugging it in as a last resort.

## Layout and Renders

This PCB supports the [Jetvan](https://trashman.wiki/pcbs/jetvan) (6.25u) and [Minisub](https://trashman.wiki/en/community/pcbs/minisub) (2.75u-2.25u-1.25u) bottom rows. The KLE can be found [here](http://www.keyboard-layout-editor.com/#/gists/7a51d1ecabd92635db48dc4a6c9a3fa1).

![Layout](/rev%202.0/Images/keyboard-layout.png)
![Front](/rev%202.0/Images/front.png)
![Back](/rev%202.0/Images/back.png)

## Ordering

Current Status: **Working** (***Order at your own risk!***)

The following guide is for ordering these PCBs from [JLCPCB](https://jlcpcb.com/).

1. Click the "Order now" text and upload the zipped gerbers via draging-and-dropping or locating the file via your file explorer.
2. After it finishes uploading, it may or may not display a preview of what it should it look like. If it doesn't, it won't autofill in the dimensions of the PCB. Input these numbers (242.8875mm x 96.7850mm) into the dimensions box if so.
3. You can now pick out your preferred PCB color, finish, and decide if you want to remove the order number silkscreen on the PCB for a bit extra along with some other extra options you can choose.
4. Check the option for "PCB Assembly" and change the assembly side to the bottom. After that, you can select if you want to have five PCBs assembled or two of them.
   - Having five PCBs assembled compared to two is a minor price increase with the benefit of:
      - Having an easy replacement if something goes wrong.
      - Wanting to use a different case without disassembling another build.
      - Being able to give/sell to others that might want it.
5. Upload the BOM & CPL in each box respectively and select "Office Appliance and Accessories &rarr; Keyboard HS Code 847330" for the description.
6. On the next page, you can see the output of the BOM file and check if the parts are correct or if they're out of stock or not. If the hotswap sockets are out of stock, you have three options. You can either:
   - Preorder part number "C5156480" into your parts library and order the PCBs when they arrive.
   - Wait for them to restock.
   - Order without the sockets pre-assembled and solder them on yourself.
7. On the final page, you can now see a preview of where the components are going to be placed and their respective rotations based on the CPL file. Review the positions and rotations and fix them if you need to.
8. At this point, you should be now able to place your order unless you want to order other PCBs with it! Make sure to respond to any e-mails that they send.
   - I would make sure to double check the parts placement after they do their DFM analysis as they changed the rotations of the horizontal diodes even though they were correct in the order preview. (I didn't notice this beforehand and had to fix the PCBs when they arrived. This could have been remedied by selecting "Confirm Parts Placement" after checking the option for "PCB Assembly" in step 4.)

Plate files are available from [Kiser Design's](https://kiserdesigns.bigcartel.com) [Monorail](https://trashman.wiki/en/community/pcbs/monorail) repository ([here](https://github.com/KiserDesigns/monorail)). The plate layout should be either be "Jet" or "Combined" and whether to choose the compression-style plate (V4N R1/2) or the bottom/top mount plate (V3N a.k.a. Hullagon) depends on what case you are using.

- I highly recommend getting your plates cut from [P3D  Store](https://p3dstore.com/products/switch-plates) as they have several materials that are loved by the community. They currently only offer plastic plates though so:
  - If you want a metal plate, you can have them cut from either [SendCutSend](https://sendcutsend.com/) (USA) or [LaserBoost](https://www.laserboost.com/) (EU) by directly uploading the .dxf file to their website.
  - If you want a FR4 plate, you'll need to do a bit of extra work. You can watch [this tutorial](https://www.youtube.com/watch?v=VofKu8A7l3c) if don't know how to convert a .dxf file into usable gerber files. You can order these alongside the PCBs as well.
    - If you have JLCPCB fabricate them, you will most likely get slapped with a fine for needing an excess amount of time to mill out the switch cutouts, wearing out their bits in the process.

## Notes

- Debug pins (SWDIO & SWCLK) are not broken out.
  - As the bootloader is stored in the RP2040's ROM, it would be pratically impossible to brick it.
- Slightly updated the edge cuts to make it a one-to-one match to the original R3 plate file.
  - Fillets were too big and edges were off by a smidge.
- Two switches were flipped on R3 instead of putting the MCU on the bottom row for sanity reasons.
  - This shouldn't effect anything excepting needing a little more attention when installing switches.
- Changed matrix connections of two switches to prevent any chance of them shorting each other compared to previous revisions.
- Plating was added to the bottom stabilizer holes so GND can't be accidentally shorted when using screw-in stabilizers.
- The flower silkscreen was removed in favor for a user-friendly key sizing guide.
- The aRGB on the PCB are slightly off in the vertical direction compared to the plate for cleaner routing.
- The libraries used for this project are my own and [marbastlib](https://github.com/ebastler/marbastlib).
- You need at least KiCad 6 Nightly (2022-10-28 and beyond) to open the source files.
