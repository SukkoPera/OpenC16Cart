# OpenC16Cart
OpenC16Cart is an Open Hardware 8/16/32 KB Cartridge for the Commodore 16, Plus/4 and the rest of the Commodore 264 family.

![Board](https://raw.githubusercontent.com/SukkoPera/OpenC16Cart/master/doc/render-top.png)

### Summary
> Like all the other Commodore 8-bit systems, the Plus/4 had a cartridge port for ROM-based software. Because the computer did not do well in the marketplace, however, very few were released. - Bo Zimmerman

One day I decided to fix my old Commodore 16. I found out about [Diag264](http://inchocks.co.uk/commodore/Diag264/HTMLManual/Diag264.htm) and, since I knew that C16 carts weren't exactly common (I have never seen one "in the flesh"!), I was somewhat surprised to learn that [people are deliberately destroying genuine carts to use them as donors to build a Diag264](http://blog.tynemouthsoftware.co.uk/2014/03/commodore-264-c16-and-plus-4-diagnostic.html).

Since I had already built an [Open Hardware cartridge for the Commodore 64](https://github.com/SukkoPera/OpenC64Cart), I thought that one for the C16 could not be much different, and so this project was born.

Since I did not own a cartridge, I set out to find images of PCBs of real cartridges on the Net, only to find out that those are rare as well. In the end I found a couple of [top](https://github.com/SukkoPera/OpenC16Cart/blob/master/doc/inspiration-top.jpg)+[bottom](https://github.com/SukkoPera/OpenC16Cart/blob/master/doc/inspiration-bottom.jpg) images, and started to reverse engineer the design from those. With the help of [some service manuals](http://www.zimmers.net/anonftp/pub/cbm/schematics/computers/plus4/index.html), I came up with OpenC16Cart. I then expanded it to have the ability of using bigger (E(E))PROMs which could store multiple ROM images.

### Configuration
C16 ROMs are normally 16 or 32 Kb (see list below). OpenC16Cart supports both, 8 KB might or might not work, I'm not aware of any carts of this size.

For the 16 KB configuration, only use the LO ROM. If you are using 64 KB (E)EPROMS, you can store up to 4 images, which you can select using the A14 and A15 jumpers above the LO ROM:

| ROM Image # | A14 | A15 |
|-------------|-----|-----|
| 1           |  L  |  L  |
| 2           |  H  |  L  |
| 3           |  L  |  H  |
| 4           |  H  |  H  |

For the 32 KB configuration, use both the LO and HI ROMs. 32 Kb ROM are usually distributed as two 16 Kb chunks, and one goes on each ROM, in corresponding positions. In this case you will also be able to switch among 4 different images, by moving the A14/A15 jumpers on **BOTH** ROMs.

The cartridge also has some more jumpers, named J1-J6, which are there because the cart I used as "inspiration" had them, but I don't really know whether they have any useful purpose:
- **J1 and J4 MUST be placed horizontally**. The normal position is the middle one. The other positions will probably be useful with 8K ROMs, but since this configuration has not been tested, you should never use them.
- **J2, J3, J5 and J6 go vertically**. The normal position is the upper one.

I'm not aware of any carts using different settings at the moment, so it is recommended to keep them as described above.

## Commodore 16 Cartridge List
Only a handful official cartridges seem to have been released:
* Commodore Jack Attack
* Commodore Viduzzles
* Commodore Atomic Mission (16K)
* Commodore Strange Odyssey (16K)
* Commodore Pirate Adventure (16K)
* Commodore C-16 Tutor
* Commodore Logo (32K)
* Commodore Diagnostic Test (TED Diagnostic Rev 1.5)
* Commodore Script/Plus
* Commodore Financial Advisor

*(The above list is courtesy of [C64 Wiki](https://www.c64-wiki.com/wiki/Commodore_16#Cartridges))*

### License
OpenC16Cart is Open Hardware. If you make any modifications to the board, please contribute them back.

### Support the Project
Since the project is open you are free to get the PCBs made by your preferred manufacturer, however in case you want to support the development, you can order them from PCBWay through this link:

[![PCB from PCBWay](https://www.pcbway.com/project/img/images/frompcbway.png)](https://www.pcbway.com/project/shareproject/OpenC16Cart_V3.html)

You get cheap, professionally-made and good quality PCBs, I get some credit that will help with this and [other projects](https://www.pcbway.com/project/member/shareproject/?bmbid=41100). You won't even have to worry about the various PCB options, it's all pre-configured for you!

Also, if you still have to register to that site, [you can use this link](https://www.pcbway.com/setinvite.aspx?inviteid=41100) to get some bonus initial credit (and yield me some more).

Again, if you want to use another manufacturer, feel free to, don't feel obligated :).

### Get Support
If you need help or have questions, you can join [the official Telegram group](https://t.me/joinchat/HUHdWBC9J9JnYIrvTYfZmg).
