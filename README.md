# Slime88 TKL PCB
 A F13 TKL Multi-Layout Hotswap H88-Compat Type-C PCB, designed in KiCAD 6.0.

![image](https://user-images.githubusercontent.com/23428162/170872810-64eff0b5-b5bb-4125-aa0f-7605366ba552.png)

![image](https://user-images.githubusercontent.com/23428162/170872794-1a198b70-811a-41c9-a83d-e31948047410.png)


## Features
- Fits the h88(c) standard
- Uses the RP2040 MCU (new), with 16MB of external flash
- Uses Kailh Hotswap Sockets
- Added anti-shearing to the hotswap sockets
- Holes of hotswap socket holes are plated, you can still solder in a switch, should a hotswap socket ever shear off for whatever reason
- Multi-layout (see below)
- Removable USB-C connector, as well as a JST connector for [Unified Daughterboard](https://github.com/ai03-2725/Unified-Daughterboard) support (for F13 TKL boards that are compatible with the daughterboard version of the h88c)
- Has cutouts for a gummy o-ring mount (Same as the hineybush h88c pcb, for boards such as the Freebird TKL or TGR Jane V2 CE)
- SWD header for debugging
- Has unused MCU GPIO pins broken out
- ESD chip (SRV05-4) to prevent damage from electrostatic discharge
- Polyfuse to prevent overcurrent
- Optimized for manufacturing and assembly with JLCPCB
- Bonus: Curved traces and teardrops

> Also, `Sleep-Lib` is just the library by [Sleepdealer](https://github.com/Sleepdealr), used in his [RP2040 Design guide](https://github.com/Sleepdealr/RP2040-designguide).

## WIP/Ideas
- Spare components on the board (i.e. diodes)
- Add physical reset switch (you currently have to short the pins on the SWD header manually)
- Add physical boot switch (you currently have to short the BOOT pins manually)
- Version with flex cuts (Already done but removed for acoustic reasons. See the board at [this point in time](https://github.com/zykrah/slime88/commit/3de3e59620d77a87f4beb085508b7e4e2e0daaf5))
- Update silkscreen graphics
- Add more layout indicators on the top silkscreen of the pcb
- Do something more special with USB shield/ground connection (currently shield is connected straight to ground)


## Multi-Layout Support

> NOTE: ANSI/ISO support works a little bit specially, either combination is soldered in at a time to ensure minimal R3 Cherry profile interference, and avoid having to rotate hotswap sockets 90 degrees to east/west orientation. See second image below.

![image](https://user-images.githubusercontent.com/23428162/170872624-f8572340-62a6-4ea2-b1d4-de3b0a03b0cc.png)

![image](https://user-images.githubusercontent.com/23428162/170872745-08062a99-3614-4d90-9b99-c35b184587f8.png)


## Removable USB C Port

Uses mousebites. Strength/functionality is untested.

![image](https://user-images.githubusercontent.com/23428162/170873526-fdf4c577-7e0c-4878-ab48-44ff42580f77.png)


## How to generate files for Manufacturing (JLCPCB)
I would personally use [this plugin](https://github.com/Bouni/kicad-jlcpcb-tools).

All components should be basic components, apart from the MCU, fuse, and JST connector (extended). 

JLC also does have [kailh hotswap sockets](https://jlcpcb.com/parts/componentSearch?isSearch=true&searchTxt=C2803348) (extended) in its parts library, but you should be very careful with the ANSI/ISO multilayout support. In the BOM, only include either desired combination of sockets (or none of them, and hand solder in the ones you want).

**NOTE: As the USB C connector is top-mounted (all other components are bottom mounted), as of writing, JLCPCB cannot assemble the USB C connector. You will likely have to hand solder it.**

## Silkscreen
For the non-weebs, the silkscreen is based on Rimuru Tempest

![image](https://user-images.githubusercontent.com/23428162/170873337-5e55e027-8117-46ac-941f-4b67e0810e19.png)
