# Slime88 TKL PCB
 A F13 TKL Multi-Layout Hotswap H88-Compat Type-C PCB, designed in KiCAD 6.0.

**This board has now been prototyped! See IRL images below.**

> NOTE: Below images may be outdated.

Renders (KiCAD):

![image](https://user-images.githubusercontent.com/23428162/170985512-ec79f498-7476-4ab6-8150-877c67a25f26.png)

![image](https://user-images.githubusercontent.com/23428162/170985490-84c50a2a-0e6f-46b4-95e9-b4f4e7d632d8.png)

IRL images of rev1 protos:

![image](https://user-images.githubusercontent.com/23428162/175326415-0662c19f-3ceb-414e-bd07-46e49cf91a11.png)

![image](https://user-images.githubusercontent.com/23428162/175326277-7a33a5fa-5684-4a13-b2d9-78f20d463656.png)

![image](https://user-images.githubusercontent.com/23428162/175326340-bfffcaf4-7a37-4090-9176-9de9ad3649e0.png)


## Features
- Fits the h88(c) standard (confirmed working in a KFE CE, should fit F13 frog)
- Uses the RP2040 MCU (new), with 16MB of external flash
- Uses Kailh Hotswap Sockets
- Added anti-shearing to the hotswap sockets
- Holes of hotswap socket holes are plated, you can still solder in a switch, should a hotswap socket ever shear off for whatever reason
- Multi-layout (see below)
- Removable USB-C connector, as well as a JST connector for [Unified Daughterboard](https://github.com/ai03-2725/Unified-Daughterboard) support (for F13 TKL boards that are compatible with the daughterboard version of the h88c)
- Has cutouts for a gummy o-ring mount (Same as the hineybush h88c pcb, for boards such as the Freebird TKL or TGR Jane V2 CE)
- BOOT pins/header for getting into bootloader (short the pins while plugging in) if [bootmagic](https://github.com/qmk/qmk_firmware/blob/master/docs/feature_bootmagic.md) isn't available . Acessible from both sides of the PCB, even when PCB is built in a keyboard. Just remove the **END key/switch** to access it.
- SWD header for debugging
- Has unused MCU GPIO pins broken out
- ESD chip (SRV05-4) to prevent damage from electrostatic discharge
- Polyfuse to prevent overcurrent
- Optimized for manufacturing and assembly with JLCPCB
- Bonus: Curved traces and teardrops

> Also, `Sleep-Lib` is just the library by [Sleepdealer](https://github.com/Sleepdealr), used in his [RP2040 Design guide](https://github.com/Sleepdealr/RP2040-designguide).

## Firmware
~~As of writing, the board runs the rp2040 branch/fork of vial-qmk. I will update this to use the official QMK implementation of RP2040 when it releases.~~ ~~UPDATE: RP2040 support has recently made it into QMK's `develop` branch. It will be fully merged to `master` by Q3 this year. Until then, the official maintainer of vial doesn't intend to merge those changes into their vial repo either, so I have made my own fork for the boards. When vial-qmk is officially updated to use QMK's implementiation of the RP2040, I will update this page once again linking to that, assuming I get the board merged into the official repo too.~~

You can find the up-to-date VIAL firmware [here](https://github.com/zykrah/vial-qmk/tree/vial-stable-zykrah/keyboards/zykrah/slime88). 

UPDATE: The board is now also in [qmk master](https://github.com/qmk/qmk_firmware/tree/master/keyboards/zykrah/slime88). (This particular version will only be VIA compatible). It should automatically be detected in VIA.

![image](https://user-images.githubusercontent.com/23428162/175326634-b620f7c7-f3c0-4445-ab55-75b2404a5e0f.png)

## WIP/Ideas
- Spare components on the board (i.e. diodes)
- Add physical reset switch (you currently have to short the pins on the SWD header manually)
- Add physical boot switch (you currently have to short the BOOT pins manually)
- Version with flex cuts (Already done but removed for acoustic reasons. See the board at [this point in time](https://github.com/zykrah/slime88/commit/3de3e59620d77a87f4beb085508b7e4e2e0daaf5))
- Update silkscreen graphics
- Add more layout indicators on the top silkscreen of the pcb
- Do something more special with USB shield/ground connection (currently shield is connected straight to ground)
- Move ESD chip to before fuse
- ~~Also breakout 3v3 and 5v on the pin breakout~~ Thanks [@vinorodrigues](https://github.com/vinorodrigues)!

## Multi-Layout Support

> NOTE: ANSI/ISO support works a little bit specially, either combination is soldered in at a time to ensure minimal R3 Cherry profile interference, and avoid having to rotate hotswap sockets 90 degrees to east/west orientation. See second image below.

![image](https://user-images.githubusercontent.com/23428162/170872624-f8572340-62a6-4ea2-b1d4-de3b0a03b0cc.png)

![image](https://user-images.githubusercontent.com/23428162/170872745-08062a99-3614-4d90-9b99-c35b184587f8.png)


## Removable USB C Port

Uses mousebites. Strength/functionality is untested.

![image](https://user-images.githubusercontent.com/23428162/170873526-fdf4c577-7e0c-4878-ab48-44ff42580f77.png)


## How to Manufacture the PCBs (JLCPCB)
~~I would personally use [this plugin](https://github.com/Bouni/kicad-jlcpcb-tools).~~

~~All components should be basic components, apart from the MCU, fuse, and JST connector (extended).~~

~~JLC also does have [kailh hotswap sockets](https://jlcpcb.com/parts/componentSearch?isSearch=true&searchTxt=C2803348) (extended) in its parts library, but you should be very careful with the ANSI/ISO multilayout support. In the BOM, only include either desired combination of sockets (or none of them, and hand solder in the ones you want).~~

The manufacturing files (JLCPCBA specific) have been added to the repo, you need to choose betweeen ANSI or ISO enter/pipe hotswap sockets being soldered by default.

You may want to consider generating the manufacturing files for yourself. I have not fully tested the ones that are currently in the repo.

> **NOTE: As the USB C connector is top-mounted (all other components are bottom mounted), as of writing, JLCPCB will charge extra to assemble the USB C connector (Standard assembly, both sides). You will likely have to hand solder it if you don't want to pay too much. Otherwise, seek out a proper PCB manufacturer (which will require further experience/knowledge).**

## Silkscreen
For the non-weebs, the silkscreen is based on Rimuru Tempest

![image](https://user-images.githubusercontent.com/23428162/170873337-5e55e027-8117-46ac-941f-4b67e0810e19.png)
