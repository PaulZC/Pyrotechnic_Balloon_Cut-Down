# Pyrotechnic Balloon Cut-Down Device

A lightweight wireless cut-down device for use on high altitude balloons.

![Pyro_Cut-Down_V2.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Pyro_Cut-Down_V2.JPG)

![Cutter_Test_2kg.gif](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Cutter_Test_2kg.gif)

Designed to be triggered by the [Iridium Beacon Radio Board](https://github.com/PaulZC/Iridium_Beacon_Radio_Board) and equipped with an
[LPRS eRIC4 or eRIC9 integrated radio module](http://www.lprs.co.uk/products/easyradio-ism-modules/eric-soc-rf-modules.html),
the cut-down will be triggered when the eRIC receives its own (unique) serial number on the chosen channel. The number of cut-downs that could be
triggered by a single Iridium Beacon is essentially unlimited.

**New for V2: the cut-down now includes a u-blox CAM-M8Q GNSS (GPS) receiver and can be configured to trigger at a pre-set altitude.**

See [How do I configure the altitude limit](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/LEARN.md#how-do-i-configure-the-altitude-limit)
for details on how to set the altitude limit using the I/O pins or via radio.

The cutter has been designed to reliably sever size 4N (2.4mm) braided nylon cord.

The cut-down device could also be used to control:
- a nichrome hot wire cord cutter
- a strobe or audible alarm
- any other device which can operate from 3.3V to 4.8V (depending on the battery voltage)

See [LEARN.md](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/LEARN.md) for further details.

See [ASSEMBLY.md](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/ASSEMBLY.md) for details on how to assemble and configure the PCB.

See [CUTTER.md](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/CUTTER.md) for details on how to assemble the mechanical parts.

See [Pyro_Cut-Down_V2.pdf](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/Pyro_Cut-Down_V2.pdf) for the schematic,
layout and Bill Of Materials.

The [Eagle](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/Eagle) directory contains the schematic and pcb design files.

The [eRIC](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/eRIC) directory contains the code for the eRIC integrated controller.

The [Drawings](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/Drawings) directory contains the drawings for the mechanical parts.

### Disclaimer

As this project involves the use of a very small quantity of smokeless gunpowder, the information contained herein should only be used by responsible adults
in full compliance with local laws and regulations regarding the purchase, transport, storage and use of smokeless powder. Follow the manufacturer's
instructions and safety information at all times. Appropriate Personal Protective Equipment must be used when handling gunpowder. Keep all parts of this
project out of the reach of children. Proceed entirely at your own risk.

The information contained herein is provided in good faith and is believed by the author to be both accurate and safe, but in no event shall the
author be liable for any injuries or damages resulting from the use of this information howsoever caused.

### License

This project is distributed under a Creative Commons Attribution + Share-alike (BY-SA) licence.
Please refer to section 5 of the licence for the "Disclaimer of Warranties and Limitation of Liability".

Enjoy!

**_Paul_**