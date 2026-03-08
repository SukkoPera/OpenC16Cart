# OpenC16Cart
OpenC16Cart is an Open Hardware 8/16/32/64 KB Cartridge for the Commodore 16, Plus/4 and the rest of the Commodore 264 family.

![Board](https://raw.githubusercontent.com/SukkoPera/OpenC16Cart/master/doc/render-top.png)

## Summary
> Like all the other Commodore 8-bit systems, the Plus/4 had a cartridge port for ROM-based software. Because the computer did not do well in the marketplace, however, very few were released. - Bo Zimmerman

One day I decided to fix my old Commodore 16. I found out about [Diag264](http://www.inchocks.co.uk/commodore/Diag264/) and, since I knew that C16 carts weren't exactly common (to this very day of 2026 I have never seen one "in the flesh"!), I was shocked to learn that [people are deliberately destroying genuine carts to use them as donors to build a Diag264](http://blog.tynemouthsoftware.co.uk/2014/03/commodore-264-c16-and-plus-4-diagnostic.html).

Since I had already built an [Open Hardware cartridge for the Commodore 64](https://github.com/SukkoPera/OpenC64Cart), I thought that one for the C16 could not be much different, and so this project was born.

Since I did not own a cartridge, I set out to find images of PCBs of real cartridges on the Net, only to find out that those are rare as well. In the end I found a couple of [top](https://github.com/SukkoPera/OpenC16Cart/blob/master/doc/inspiration-top.jpg)+[bottom](https://github.com/SukkoPera/OpenC16Cart/blob/master/doc/inspiration-bottom.jpg) images, and started to reverse engineer the design from those. With the help of [some service manuals](http://www.zimmers.net/anonftp/pub/cbm/schematics/computers/plus4/index.html), I came up with OpenC16Cart. I then expanded it to have the ability of using bigger (E(E))PROMs which could store multiple ROM images.

With V5, I even added the possibility of having a single-EEPROM 64 kB cartridge spanning both the C1 and C2 slots.

> [!IMPORTANT]
> V5 is a 44-pin cartridge. It is not compatible with a stock C16/+4. To use it, you will need a [Plus4MultiExpander](https://github.com/SukkoPera/Plus4MultiExpander) [^v4].

## Configuration
As of V5, OpenC16Cart might work in different modes. Ideally, the cartridge is used with a 64 kb EEPROM, in which case the following configurations will be available:

### 16 kB Mode
In 16 kB mode, you get 4 slots, which can be selected through appropriate placement of the SW2 and SW3 jumpers:

|ROM Image #|A15|A14|ROM Area   |
|-----------|---|---|-----------|
|0          |0  | 0 |$0000-$3fff|
|1          |0  | 1 |$4000-$7fff|
|2          |1  | 0 |$8000-$bfff|
|3          |1  | 1 |$c000-$ffff|

Note that the cartridge will respond to all C1 and C2 low/high slots. If this is unwanted, cut open JP1/2/3 accordingly (or do not mount D1/2/3). Also note there is no way to respond to a single C2 slot.

### 32 kB Mode
In 32 kB mode, SW2 must be placed in the `DIR` position and 2 banks will be available:

|ROM Image #|A15|ROM Area                                      |
|-----------|---|----------------------------------------------|
|0          |0  |Low ROM: $0000-$3fff<br/>High ROM: $4000-$7fff|
|1          |1  |Low ROM: $8000-$bfff<br/>High ROM: $c000-$ffff|

Within each slot, the low ROM must occupy the first half of the allocated space, while the high ROM will take the other half.

As in 16 kB mode, you might want to play with the jumpers or diodes.

### 64 kB Mode
In 64 kB mode, both SW2 and SW3 must be placed in the `DIR` position and, obviously, only a single bank will be available.

The allocation of the slots is as follows:

|Slot   |ROM Area   |
|-------|-----------|
|C2 Low |$0000-$3fff|
|C2 High|$4000-$7fff|
|C1 Low |$8000-$bfff|
|C1 High|$c000-$ffff|

Note that C2 actually goes first.

## Releases
If you want to get this board produced, you are recommended to get [the latest release](https://github.com/SukkoPera/OpenC16Cart/releases) rather than the current git version, as the latter might be under development and is not guaranteed to be working.

Every release is accompanied by its Bill Of Materials (BOM) file and any relevant notes about it, which you are recommended to read carefully.

**I am not providing ready-to-use gerber files**. If all you want is **to get boards made, I would really appreciate if you did so [in a way that supports the project](#support-the-project)**.

## License
The OpenC16Cart documentation, including the design itself, is copyright &copy; SukkoPera 2019-2025 and is licensed under the [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/).

This documentation is distributed *as is* and WITHOUT ANY EXPRESS OR IMPLIED WARRANTIES whatsoever with respect to its functionality, operability or use, including, without limitation, any implied warranties OF MERCHANTABILITY, SATISFACTORY QUALITY, FITNESS FOR A PARTICULAR PURPOSE or infringement. We expressly disclaim any liability whatsoever for any direct, indirect, consequential, incidental or special damages, including, without limitation, lost revenues, lost profits, losses resulting from business interruption or loss of data, regardless of the form of action or legal theory under which the liability may be asserted, even if advised of the possibility or likelihood of such damages.

## Support the Project
If you want to get some boards manufactured, you can get them from PCBWay through this link:


[![PCB from PCBWay](https://www.pcbway.com/project/img/images/frompcbway.png)](xxx)

You get my gratitude and cheap, professionally-made and good quality PCBs, I get some credit that will help with this and [other projects](https://www.pcbway.com/project/member/shareproject/?bmbid=41100). You won't even have to worry about the various PCB options, it's all pre-configured for you!

Also, if you still have to register, [you can use this link](https://www.pcbway.com/setinvite.aspx?inviteid=41100) to get some bonus initial credit (and yield me some more).

You can also buy me a coffee if you want:

<a href='https://ko-fi.com/L3L0U18L' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi6.png?v=6' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

[^v4]: Although this *might* be amended at some point, that's why there currently is no V4, it was reserved for that.
