# Wee Wii

**An open-source custom PCB recreation of the Nintendo Wii, designed for console portabilization.**

*BOM formatting can be done in KiCad for PCBA.*

The Wee Wii is a collection of KiCad files for a fully functional Wii PCB, including a reverse-engineered schematic of the Wii Game Console. The purpose of this project is to eliminate some of the hard-to-debug variables in the trimming process of various Wii portable systems, and to enable more practical board designs to be made. This board is functionally a proof of concept, and is not practical in any current portable design.

The Wee Wii PCB is designed around the Hollywood-1 and Broadway-1 chips. Any 4 layer motherboard is a suitable harvest

<img height="500" alt="Wii PCB v2" src="https://github.com/user-attachments/assets/676c2137-3d66-4cef-b19c-93c996892c54" />
<img height="500" alt="Wii PCB v1" src="https://github.com/user-attachments/assets/9c967248-ca32-4d05-a97c-e2c166d2203f" />
<img height="500" alt="Wii PCB v3" src="https://github.com/user-attachments/assets/8a9cd071-0139-4751-8026-7e89fae7f955" />

*Fusion 360 Render of the pcb*


Attached schematic exported from KiCad:





## Disclaimer

This board requires chips harvested from a Nintendo Wii. This is a high-risk procedure for the components and is not advisable on a working console unless the technician is confident in their skills, or the donor board is non-functional.

It is highly recommended to install Aurelio92's [RVLoader](https://github.com/Aurelio92/RVLoader) before harvesting the components, as this enables booting the custom board without the WiFi and Bluetooth daughterboards.

Some mistakes may be present in the current BOM. A working board was nearly fully populated using passives harvested from a working Wii. Mistakes in the old board requiring bodges were addressed.

<img height="400" alt="Wii Rear Bodges" src="https://github.com/user-attachments/assets/a47d31a1-8bef-4523-9797-472bbdb1e62a" />
<img height="400" alt="BGA Bodges" src="https://github.com/user-attachments/assets/95209819-7cee-4909-b254-de5e24f3f346" />

*preview of my pcb with bodges, before current revision*


A number of BGA nets were revised for accuracy during development, so while the schematic and board is believed to be correct, errors may still be present. If you spot any mistakes, please open an issue. If you want to improve the symbol net names such as the GC card reader pads, disc drive pads, please request a merge.


I have not verified the functionality of the MX chip RTC, or the functionality of the SD card pads.

I have not verified the polarity for the Bluetooth daughterboard, assume BT and BT~ are Data 1 and Data 2 respectively.

<img width="400" alt="image" src="https://github.com/user-attachments/assets/ef8f5b0f-49f0-4fc3-a949-789567c96b5e" />

Image courtesy of BitBuilt [The Definitive Wii Trimming Guide](https://bitbuilt.net/forums/threads/the-definitive-wii-trimming-guide.198/)

## Features

- Compact ~ 62.2 × 71.5mm 4-layer PCB
- Fully reverse-engineered schematic
- WiFi header
- External power solder points
- U10, MX, and USB footprints. No relocation variables
- Passive components on one side for PCBA, excluding harvested chips and bulk capacitance
- Bluetooth vias for soldering twisted-pair enamelled wire to the Bluetooth daughterboard


## Applications

- Acts as a reference and starting point for designing a custom portable Wii.
- Reclaim working chips from dead boards, enabling failed portable consoles to have a second life, or reviving consoles that have failures


## Harvesting

The large BGA components on the Wii are at risk of failure during harvesting, to help improve the likelihood of successful chip harvesting, bake the donor board for 12–24 hours at 100°C before starting. Preheat the board to 150°C before applying top heat.

It is recommended to pull the Hollywood GPU first, as it is console specific and requires the associated NAND chip or a NAND dump to function.

## Production

Using the provided gerbers, they are intended to be produced with 1.2mm thick boards, and 0.5 oz copper internal is sufficient.

If producing using PCBA with JLC, take care that you manually review the BOM components, as JLC does not properly detect correct components, such as this:

<img width="400" alt="image" src="https://github.com/user-attachments/assets/a48f40f4-fe5e-4717-b7a2-a5a115b30543" />

JLC's automatic BOM detects a 70 ohm resistor as 4.7k

It's also worth noting that the Wii BOM uses quite a few components that are considered non standard, and manufacturers will charge more to populate these components, it's worth considering to only have some of these passives populated, like all of the standard decoupling capacitors behind the gpu and cpu, to reduce manual component harvesting.

## License

This project is licensed under the CERN-OHL-S-2.0 license. You are free to modify, manufacture, sell, and distribute this hardware. Any derivatives must remain open-source under the same license.


## Credits

While working on this I referenced work and documentation from
[mackieks](https://github.com/mackieks),
[Aurelio92](https://github.com/Aurelio92),
[supertazon](https://github.com/supertazon),
[loopj](https://github.com/loopj),
[VoxelTek](https://github.com/VoxelTek),
and others in the [BitBuilt community](https://bitbuilt.net/).

Notable projects: [AVEflex](https://github.com/mackieks/AVEflex/), [WiFiFlex](https://github.com/mackieks/wififlex), [mxHound](https://github.com/mackieks/mxhound).
