NOTICE this is just an untested proof of concept

# 486 L2 cache adapter for TSOP32/DIP32

Asynchronous fast SRAM chips in DIP32 package, were phased out. This makes not possible to use new chips to upgrade 486 L2 cache. However there are still compatible SRAM variants in SMT packages.

This project aims to create a PCB design, which allows the retro community to put TSOP32 chip into a DIP32 socket.

# Design

DIP32 sockets usually have the absolute maximum dimensions 10 x 40 mm. The adapter need to be less wide than that (and any exceeding PCB space due to a manufacturing tolerances needs to be sanded out).

TSOP32 type I chips needs to have width below this limit too. This reduces the list of possible chips only few types. Also there is a difference between 3.3V and 5V SRAM pinouts. The 3.3V pinouts would be highly complicated to route on 2 layer PCB.

The resulting list of chips I've found is:

* IS61C1024AL-12TLI
* CY7C109D-10ZXI
* AS7C1024B-12TCN

These chips have dimensions around 8 x 20 mm so there will be almost 1 mm between the side of the chip and the edge of the PCB (2 mm between chips on the motherboard).

Shorter variants seems to exist: IS61C1024AL-12HLI and AS7C1024B-10STC. These have dimensions 8 x 13.4 mm. The PCB could be changed in a way the pads for pins 17 to 32 will be closer to the upper part of the PCB.

Sadly a 1 mm space between chip and the PCB edge is not enough for having THT pins for the DIP32 socket. Only SMT pins can be placed below the SRAM TSOP package. If using a pin like this:

![pinheader](pinheader.png)

The top part needs to be cut and sanded to the wide section, which then needs to be soldered down in a similar way as the BGA or QFN is.

The THT section in the current version of the PCB is using hole size 0.8 mm. So the round/precise pins should fit (usually 0.6 mm). The square pinheader is not supported (it would destroyed the motherboard socket anyway).

All pin sections have extruding copper section nearing the center of the PCB. This should help with QFN-like soldering and it is also allowing for using a 90° angled pinheader.

BTW an older version of the PCB had "half-THT" holes below the TSOP chip, where the pin would end inside the PCB thickness and was soldered only on one side (no copper below the chip). Not sure if this design can be manufactured (essentially a half via), so I removed that.

# Design rules

* Precise (rounded) pinheaders have diameter: 0.47 mm to 0.6 mm
* Hole tolerance (for adapter pins) is: about +- 0.1 mm => THT pad hole diameter 0.8 mm
* Copper clearance to edge: >= 0.2 mm
* Pin mapping is not 1:1, the PCB cannot be used an arbitrary TSOP/DIP adapter

# Links

Sourcing the chips should be possible from Mouser, Digikey and TME, there are probably other sources too:

## IS61C1024AL-12TLI

[TME](https://www.tme.eu/cz/en/details/is61c1024al-12tli/parallel-sram-memories-integ-circ/issi/)
[Mouser](https://eu.mouser.com/ProductDetail/ISSI/IS61C1024AL-12TLI?qs=YdQ7Kj7W0bxK0kzoprU3Cw%3D%3D)
[Digikey](https://www.digikey.com/en/products/detail/issi-integrated-silicon-solution-inc/IS61C1024AL-12TLI/1557110)

## CY7C109D-10ZXI (it seems it is EOL)

[Mouser](https://eu.mouser.com/ProductDetail/Infineon-Technologies/CY7C109D-10ZXI?qs=QxhBKGBQLiLnC0p%252BIVeZeA%3D%3D)
[Digikey](https://www.digikey.com/en/products/detail/infineon-technologies/CY7C109D-10ZXI/1640242)

## AS7C1024B-12TCN

[TME](https://www.tme.eu/cz/en/details/as7c1024b-12tcn/parallel-sram-memories-integ-circ/alliance-memory/)
[Mouser](https://eu.mouser.com/ProductDetail/Alliance-Memory/AS7C1024B-12TCN?qs=E5c5%252Bmu3i39p9b7hUnTiBw%3D%3D)
[Digikey](https://www.digikey.com/en/products/detail/alliance-memory-inc/AS7C1024B-12TCN/4234602)

If you have a courage to make the adapter. Please share your experiences.

Licensed under CC BY-NC-SA 4.0

pc2005
