# Pyrotechnic Balloon Cut-Down Device

## LEARN

A lightweight wireless cut-down device for use on high altitude balloons.

![Pyro_Cut-Down_1.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Pyro_Cut-Down_1.JPG)

![Cutter_Test_2kg.gif](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Cutter_Test_2kg.gif)

Designed to be triggered by the [Iridium Beacon Radio Board](https://github.com/PaulZC/Iridium_Beacon_Radio_Board) and equipped with an
[LPRS eRIC4 or eRIC9 integrated radio module](http://www.lprs.co.uk/products/easyradio-ism-modules/eric-soc-rf-modules.html),
the cut-down will be triggered when the eRIC receives its own (unique) serial number on the chosen channel. The number of cut-downs that could be
triggered by a single Iridium Beacon is essentially unlimited.

The cutter has been designed to sever size 4N (2.4mm) braided nylon cord.

The cut-down device could also be used to control:
- a nichrome hot wire cord cutter
- a strobe or audible alarm
- any other device which can operate from 3.3V to 4.8V (depending on the battery voltage)

See [Pyro_Cut-Down_V1.pdf](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/Pyro_Cut-Down_V1.pdf) for the schematic,
layout and Bill Of Materials.

See [ASSEMBLY.md](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/ASSEMBLY.md) for details on how to assemble and configure the PCB.

The [Eagle](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/Eagle) directory contains the schematic and pcb design files.

The [eRIC](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/eRIC) directory contains the code for the eRIC integrated controller.

See [CUTTER.md](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/CUTTER.md) for details on how to assemble the mechanical parts.

The [Drawings](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/Drawings) directory contains the drawings for the mechanical parts.

### eRIC

The heart of the Cut-Down Device is the eRIC4 or eRIC9 [easyRadio Integrated Controller](http://www.lprs.co.uk/products/easyradio-ism-modules/eric-soc-rf-modules.html).

![Learn_1.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Learn_1.JPG)

Either an eRIC4 or an eRIC9 can be installed. The eRIC4 operates at 402-470 MHz for Europe, APAC and China. The eRIC9 operates at 804-940 MHz for Europe,
North & South America, India and China. Solder the _FREQ_ split pad to select the eRIC9 915 MHz band.

Each eRIC has a unique serial number. The custom code running on the eRIC will trigger the cut-down when it receives a data packet containing that serial number.

The cut-down _PYRO_ output will be enabled when the eRIC receives:
- Its serial number
- Or its serial number followed by a "1"

The cut-down output will be disabled when the eRIC receives:
- Its serial number followed by a "0"

If the serial number of the eRIC is _12345678_, the cut-down will be triggered when the eRIC receives either:
- _12345678_

or
- _123456781_

The cut-down output will be disabled when the eRIC receives:
- _123456780_

If you are using the [Iridium Beacon](https://github.com/PaulZC/Iridium_9603_Beacon) and the
[Iridium Beacon Radio Board](https://github.com/PaulZC/Iridium_Beacon_Radio_Board) to control the cut-down, you will need to send the commands:
- _[RADIO=12345678]_ or _[RADIO=123456781]_ to trigger the cut-down
- _[RADIO=123456780]_ to disable the cut-down

### MPL3115A2

![Learn_2.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Learn_2.JPG)

The cut-down can be equipped with an (optional) MPL3115A2 pressure and temperature sensor. The pressure reading can be converted into altitude using the equation
given in the [MPL3115A2 datasheet](https://www.nxp.com/docs/en/data-sheet/MPL3115A2.pdf) or, more accurately, using the
[Barometric Formula](https://en.wikipedia.org/wiki/Barometric_formula).

Even if the Barometric Formula is used, altitudes above 15km could have an error of +/- 1000m, and so the pressure reading is of little practical use
except as a very coarse upper-altitude limit.

If you want to make use of the pressure reading, please refer to the example code provided in _eRIC_CutDown_Tx_Pressure_and_Temperature.zip_ in the
[eRIC folder](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/eRIC). Programming instructions can be found in
[Making changes to the eRIC code](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/ASSEMBLY.md#making-changes-to-the-eric-code).

### Pyrotechnic output

![Learn_4.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Learn_4.JPG)

Q1 is a DMG3415U-7 P-Channel MOSFET which can switch currents of: 4 Amps continuous; 30 Amps pulsed. By default, the Gate of Q1 is held high by R9, which disables
the MOSFET. When the Gate of Q1 is pulled low by Q2, the full battery voltage is connected to the _PYRO+_ terminal, which triggers the electric
match within the pyrotechnic cutter.

Q2 is an NPN transistor. By default, the Base of Q2 is pulled low by R12, which disables the transistor and prevents it from pulling the Gate of Q1 low.
Q2 is enabled when the _FIRE_ signal connected to its Base goes high.

### Dual NOR gate

![Learn_3.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Learn_3.JPG)

IC3 is a 7402 dual NOR logic gate. It prevents the _FIRE_ signal from accidentally going high, e.g. when the eRIC goes through a power-up reset. _FIRE_ can only
go high if:
- eRIC Pin17 is high (which provides power to the NOR gates)
- eRIC Pin18 is high
- eRIC Pin19 is low

The Input/Output pins on most microcontrollers go into a floating (high impedance) state during reset and can only be configured as outputs once the
embedded code starts to execute. The 7402 NOR gate ensures that _FIRE_ does not accidentally go high during that period.

### Reset supervisor

![Learn_5.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Learn_5.JPG)

IC2 is an MCP111T-240 reset supervisor. It ensures that the eRIC is reset whenever the battery voltage falls below 2.4V.

Normally, the nichrome heating wire inside the electric match will go open-circuit as soon as the match is activated. If this fails to happen, Q1 will continue to
deliver current to the electric match until the batteries are exhausted. IC2 ensures that the eRIC is reset when the battery voltage starts to fall, which in turn
will disable Q1 via IC3 and Q2.

### LEDs

LED1 will illuminate when the PYRO output is active.

LED2 will flash once per second to show that the cut-down is operational. LED2 will be lit continuously when the eRIC is in bootloader mode.

### Diodes

D1 and D2 provide protection for the batteries and USB power pin from each other.

### I/O pins

![Learn_6.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Learn_6.JPG)

The eRIC TxD, RxD, CTS and RTS pins are connected to 0.1" pads on the edge of the circuit board. The order of these pads matches the order of the pins of an FTDI
TTL-232R-3V3 USB to TTL serial cable. The eRIC can be reprogrammed via the FTDI cable.

Two extra pads are connected to the eRIC bootloader pins (Pin11 and Pin12). The eRIC will enter bootloader mode if these pads are shorted together on reset
or power-up. LED2 will be lit continuously when the eRIC is in bootloader mode.

### Antennas

Recommended antenna for the eRIC4 is:
- LPRS ANT-SR433 (Farnell part 2096221)

Recommended antenna for the eRIC9 is:
- LPRS ANT-SR900 (Farnell part 2096219)

http://www.lprs.co.uk/products/antennas-cables-connectors/stubby-antennas.html

The horizontal antenna orientation is important if the cut-down is positioned directly above the Iridium Beacon Radio Board on the balloon cord.

### How much does it weigh?

![Weight.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Weight.JPG)

The total weight of the assembled cut-down is 75.4 grams. This comprises:
- Assembled cutter: 27.2g
- Energiser® Ultimate Lithium AAA batteries: 22.7g
- Assembled circuit board: 19.1g
- Antenna: 6.4g

### Which AAA batteries should I use?
Energiser® Ultimate Lithium batteries. These are rated down to -40°C but tests I've done (using dry ice) show that they continue to work much colder than that.

### How long will the batteries last?

With the eRIC power saving set to 2, the average current draw is 4.6mA at 4.5V. When powered by three Energiser® Ultimate Lithium AAA batteries, the batteries
should last approximately 10 days. This ignores the current drawn by the electric match when the cut-down is activated.

![Current_Draw.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Current_Draw.JPG)

### Do I need to be careful around the battery clips?

Yes! The clips are of course conductive. If you place the circuit board battery-side down on a conductive surface **BAD THINGS WILL HAPPEN!**

### Have you tested it?

Yes. The cutter has been used successfully to sever size 4N (2.4mm) braided nylon cord with test loads of 2kg and 100g.

![Cutter_Test_2kg_1.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Cutter_Test_2kg_1.JPG)

![Cutter_Test_100g.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Cutter_Test_100g.JPG)

### License

This project is distributed under a Creative Commons Attribution + Share-alike (BY-SA) licence.
Please refer to section 5 of the licence for the "Disclaimer of Warranties and Limitation of Liability".

Enjoy!

**_Paul_**