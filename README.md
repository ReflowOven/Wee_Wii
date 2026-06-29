# Wee Wii

**A fully reverse-engineered, open-source PCB recreation of the Nintendo Wii, designed as a foundation for portable console designs.**


The Wee Wii is a KiCad project of a fully functional Wii PCB and schematic, built by reverse engineering the original boards. The purpose of this project is to shrink the Wii's board size, and avoid having to cut the stock console down to get the console into a form factor of your choice. This board design also eliminates some of the variables when shrinking boards down to a smaller size, and does not require cutting and sanding powerplanes and data connections to have a functional console. Rather than being a direct portable console, this board design is intended to be a reference design for integrating the Wii hardware into custom portable builds.

The Wee Wii PCB is designed around the Hollywood-1 and Broadway-1 chips. Any 4 layer motherboard is a suitable donor.

<img height="500" alt="Wii PCB v2" src="https://github.com/user-attachments/assets/676c2137-3d66-4cef-b19c-93c996892c54" />
<img height="500" alt="Wii PCB v1" src="https://github.com/user-attachments/assets/9c967248-ca32-4d05-a97c-e2c166d2203f" />
<img height="500" alt="Wii PCB v3" src="https://github.com/user-attachments/assets/636df447-9e8c-421b-b984-d017f136029e" />


*Fusion 360 Render of the pcb above*

---

<img height="500" alt="Example Page1" src="https://github.com/user-attachments/assets/c04b5fe3-61f1-4dbd-ae62-461faa6031e2" />

<img height="600" alt="Example Page2" src="https://github.com/user-attachments/assets/4ea2d846-7b20-4585-9e50-6c2425667c86" />


*Short preview of the schematic above, the full schematic is split into multiple sheets for readability*


## Notes

This board requires chips harvested from a Nintendo Wii. This is a high-risk procedure for the bga components and is not recommended on a working console unless the technician is experienced, or the donor board is non-functional.

It is highly recommended to install Aurelio92's [RVLoader](https://github.com/Aurelio92/RVLoader) before harvesting the components, as this enables booting the custom board without the WiFi and Bluetooth daughterboards.

**The PCBA revision has now been fully tested. Functionality and BOM is now up to date.**

<img height="600" alt="PCBA_WII_TOP" src="https://github.com/user-attachments/assets/5977ba31-5215-45df-8a70-582d588d69a9" />
<img height="600" alt="PCBA_WII_BOT" src="https://github.com/user-attachments/assets/1f1b23d4-04dc-4f22-8ae7-bbdb4136febf" />

*preview of the newest assembled boards with PCBA / new components, Fully working*

---

**First fully assembled board, formerly required bodges because of small errors**

<img height="400" alt="Wii Rear Bodges" src="https://github.com/user-attachments/assets/a47d31a1-8bef-4523-9797-472bbdb1e62a" />
<img height="400" alt="BGA Bodges" src="https://github.com/user-attachments/assets/95209819-7cee-4909-b254-de5e24f3f346" />

*preview of pcb with bodges, before current revision*

---

BGA nets were iteratively revised for clarity and accuracy during development. The schematic and board is believed to be correct, but errors may still be present. If you spot any mistakes, please open an issue.



The bluetooth via nets have been changed in the schematic as of Jun 2026, if you are referencing the BitBuilt community's relocation guide, Data 1 -> BT~ and Data 2 -> BT, the old net was technically reversed since the bluetooth vias are actually USB.

<img width="400" alt="image" src="https://github.com/user-attachments/assets/ef8f5b0f-49f0-4fc3-a949-789567c96b5e" />

Image courtesy of BitBuilt [The Definitive Wii Trimming Guide](https://bitbuilt.net/forums/threads/the-definitive-wii-trimming-guide.198/)

---

## Features

- Compact 62.2 × 71.5mm 4-layer PCB
- Fully reverse-engineered schematic
- WiFi header
- Bluetooth vias for soldering twisted-pair enamelled wire to the Bluetooth daughterboard
- External power solder points
- U10, MX, and USB footprints. No relocation variables
- Passive components on one side for PCBA
- BOM for PCBA


## Applications

- Acts as a reference and starting point for designing a custom portable Wii.
- Reclaim working chips from dead boards, enabling failed portable consoles to have a second life, or reviving consoles that have general failures


## Harvesting

The large BGA components on the Wii are at risk of failure during harvesting, to help improve the likelihood of successful chip harvesting, bake the donor board for 12–24 hours at 100°C before starting. Preheat the board to 150°C before applying top heat.

It is recommended to pull the Hollywood GPU first, as it is console specific and requires the associated NAND chip or a NAND dump to function.

It is useful to inspect the substrate of the chips after harvest to ensure that no packages have swelled up, and taking a multimeter and measuring the various power rails resistance to ground, if any of these are very different than soldered to a board, the chips are very likely dead. 1.8V is an outlier, because it has a current biased voltage divider on the rail, which reads about 36 ohms in circuit. Out of circuit the GDDR3 should read 10K+.


## Production

Using the provided gerbers, they are intended to be produced with 1.2mm thick boards, and 0.5 oz copper internal is sufficient.

If producing using PCBA with JLC, take care that you manually review the BOM components, as JLC does not properly detect correct components, such as this:

<img width="400" alt="image" src="https://github.com/user-attachments/assets/a48f40f4-fe5e-4717-b7a2-a5a115b30543" />

In this image, JLC's BOM parser detects a 70 ohm resistor as 4.7k.

---

It's also worth noting that the Wii BOM uses quite a few components that are considered non standard, and manufacturers will charge more to populate these components, it's worth considering to only have some of these passives populated, like the standard decoupling capacitors behind the gpu and cpu.
Some of the components that nintendo populated related to the RAM BOM do function within a few percentage points, it is functional to use the nearest common resistor value for some of the ram resistor networks, such as 68R.

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
