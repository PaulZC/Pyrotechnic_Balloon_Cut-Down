# Pyrotechnic Balloon Cut-Down Device

## Circuit Board Assembly and Configuration

A lightweight wireless cut-down device for use on high altitude balloons.

![Pyro_Cut-Down_V2.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Pyro_Cut-Down_V2.JPG)

![V2_Assembly_11.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/V2_Assembly_11.JPG)
![V2_Assembly_12.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/V2_Assembly_12.JPG)

![Cutter_Test_2kg.gif](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Cutter_Test_2kg.gif)

Designed to be triggered by the [Iridium Beacon Radio Board](https://github.com/PaulZC/Iridium_Beacon_Radio_Board) and equipped with an
[LPRS eRIC4 or eRIC9 integrated radio module](http://www.lprs.co.uk/products/easyradio-ism-modules/eric-soc-rf-modules.html),
the cut-down will be triggered when the eRIC receives its own (unique) serial number on the chosen channel. The number of cut-downs that could be
triggered by a single Iridium Beacon is essentially unlimited.

**New for V2: The Cut-Down now includes a u-blox CAM-M8Q GNSS (GPS) receiver and can be configured to trigger at a pre-set altitude.**

The cutter has been designed to sever size 4N (2.4mm) braided nylon cord.

The cut-down device could also be used to control:
- a nichrome hot wire cord cutter
- a strobe or audible alarm
- any other device which can operate from 3.3V to 4.8V (depending on the battery voltage)

See [Pyro_Cut-Down_V2.pdf](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/Pyro_Cut-Down_V2.pdf) for the schematic,
layout and Bill Of Materials.

The [Eagle](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/Eagle) directory contains the schematic and pcb design files.

The [eRIC](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/eRIC) directory contains the code for the eRIC integrated controller.

Here are the assembly and configuration instructions for V2 of the PCB:

### Blank PCB

Start by having the blank PCBs manufactured. If you are based in the UK or Europe, I can recommend
[Multi-CB](https://www.multi-circuit-boards.eu/en/index.html) who can manufacture PCBs in 1-8 working days and
can process the Eagle .brd file direct - there's no need to generate Gerber files.

My recommended options are:
- Layers: 2 layers
- Format: single pieces
- Surface finish: chemical gold (ENIG)
- Material: FR4, 1.55mm
- Cu layers: 35um
- Solder stop: both sides, green
- Marking print: both sides, white

![V2_Assembly_1](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/V2_Assembly_1.JPG)

### Add solder paste

Multi-CB can also provide you with a solder paste (SMD) stencil for the PCB. My recommended options are:
- SMD stencil for: top layer
- Type: custom
- Pad reduction: yes, 10%
- Thickness: 100um
- Existing fiducials: lasered through
- Text type: half lasered
- Double-sided brushing: yes

Secure the blank PCB onto a flat work surface by locating it between two engineer's squares. I use a sheet of toughened glass
as the work surface as it is both very flat and easy to clean.

![V2_Assembly_2](https://github.com/PaulZC/Balloon_Cut-Down_Device/blob/master/img/V2_Assembly_2.JPG)

Use the two round fiducials to line up the stencil with the PCB. Secure the stencil with tape.

![V2_Assembly_3](https://github.com/PaulZC/Balloon_Cut-Down_Device/blob/master/img/V2_Assembly_3.JPG)

Apply solder paste close to the component cut-outs and then scrape the paste over the stencil using a knife blade
or a similar straight edge. Take appropriate safety precautions when working with solder paste - particularly if you are using
tin-lead solder instead of lead-free.

![V2_Assembly_4](https://github.com/PaulZC/Balloon_Cut-Down_Device/blob/master/img/V2_Assembly_4.JPG)

![V2_Assembly_5](https://github.com/PaulZC/Balloon_Cut-Down_Device/blob/master/img/V2_Assembly_5.JPG)

![V2_Assembly_6](https://github.com/PaulZC/Balloon_Cut-Down_Device/blob/master/img/V2_Assembly_6.JPG)

### Position the surface mount components

Position the components onto the blobs of solder paste using tweezers. A magnifier lamp or a USB microscope will
help you place the components in the correct position. IC3 - the u-blox CAM-M8Q - is probably the trickiest
component to position. Take extra time to make sure it is centered accurately on the pads.

### Reflow the surface mount components

Use a reflow oven to heat the circuit board to the correct temperatures to melt the solder. A reflow oven doesn't need to be expensive. The one shown below was assembled from:

- Quest 9L 800W mini-oven
- Inkbird PID temperature controller and 40A solid state relay
- Type K thermocouple

![Oven.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/Oven.JPG)

Several people have published good reflow oven construction guides, including [this one](http://www.die4laser.com/toaster/index.html).

Use the correct temperature profile for your solder paste, but you won't go far wrong with 160C for four minutes, followed by
210C for one minute, followed by a cool-down with the door open. Use a flashlight to check that the solder has melted across
the whole PCB at 210C. Hold the temperature at 210C a little longer if some of the solder paste still appears 'gray' instead of 'silver'.

All being well, your PCB should look like this:

![V2_Assembly_7.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/V2_Assembly_7.JPG)

### Check for shorts

Carefully examine all the solder joints and correct any shorts you find.

The 'trick' to removing a short is to add more solder or solder paste and then to use
copper solder braid or wick to remove all the solder in one go.

Use a cotton swab dipped in Isopropyl Alcohol (IPA / Propanol / rubbing alcohol) to remove any flux residue.

### Add the non-surface mount components

The non-surface mount components (battery clips, reset switch, pyrotechnic connector, SMA connector) can now be soldered into place.

![V2_Assembly_8.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/V2_Assembly_8.JPG)
![V2_Assembly_9.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/V2_Assembly_9.JPG)

### Lacquer the PCB

I do recommend giving the PCB a coat of lacquer, especially if you are intending to use it on a balloon flight.
Cover all of the surface mount components with [Acrylic Protective Lacquer (conformal coating)](https://uk.rs-online.com/web/p/conformal-coatings/3217324/)
taking care to avoid the I/O pins and the reset switch.

### Configure the eRIC

The eRIC will come pre-programmed with easyRadio V1.5.5. This needs to be replaced with the custom code which you will find in the
[eRIC folder](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/eRIC).

You can find the datasheet for the eRIC on the LPRS website:
- http://www.lprs.co.uk/products/easyradio-ism-modules/eric-soc-rf-modules.html
- http://www.lprs.co.uk/assets/files/eRIC4_9_Datasheet_1.34.pdf

Download and install the latest version of the easyRadio Companion:
- http://www.lprs.co.uk/development-tools/easyradio-evaluation-software.html
- http://www.lprs.co.uk/assets/files/easyRadiosetup%204.1.6.exe

If possible, use an FTDI TTL-232R-3V3 cable to reconfigure the board, although a TTL-232R-5V will work too.
- https://www.ftdichip.com/Products/Cables/USBTTLSerial.htm

Plug the 6-Way connector of the FTDI cable onto one end of an 8-way length of double-height 0.1" header strip. Leave the cable USB connector unconnected for now.

![V2_Assembly_10.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/V2_Assembly_10.JPG)

Insert the header strip through the holes in the PCB and then lean the header strip against the side of the holes to ensure good electrical contact. Now plug
the FTDI USB connector into your computer. LED2 should be flashing once per second; if it is lit continuously ensure you do not have a jumper link connecting
the two "Boot" pads together. If required, press the Reset button to restart the eRIC.

Start the easyRadio Companion. Registering the software is recommended but is optional. Click on the "eRIC" button. Select the COM port for the FTDI
cable in the UART Settings, then click "Open Port".

Ensure the "Settings" vertical tab is selected.

Click on the "Module Info" horizontal tab. Click on "Discover Module". Wait for all of the module information to be collected. Make a note of the eight digit
eRIC serial number; you will need this to be able to trigger the cut-down. Ideally, print the serial number onto a label and stick it onto the eRIC.

![easyRadio_1.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/easyRadio_1.JPG)

Place a jumper link to link the two "Boot" header pins together; then press the Reset button to place the eRIC into bootloader mode. LED2 should light up
continuously. If LED2 is flashing once per second instead, ensure you have the jumper link installed correctly. If required, press the Reset button to restart
the eRIC.

Click on the "Firmware Upgrades" horizontal tab. Click on "Open Firmware File" and browse to the eRIC4_Pyro_CutDown_V2.hex file which you will find in the
[eRIC folder](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/eRIC). Select eRIC9_Pyro_CutDown_V2.hex instead if you are using the 868 / 915MHz
eRIC9.

Leave "Enable Code Protect" selected and then click "Upgrade".

All being well, you should see a green progress bar followed by the message "Firmware Update Complete!".

![easyRadio_2.JPG](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/blob/master/img/easyRadio_2.JPG)

Disconnect the FTDI USB connector from your computer, then remove the header strip.

### Making changes to the eRIC code

If you want to alter the programming of the eRIC, you will need to:
- Follow the instructions in http://www.lprs.co.uk/assets/files/Custom%20programming%20eRIC.zip
- Install the Texas Instruments Code Composer Studio
- Copy and unzip the eRIC_Pyro_CutDown_V2.zip from the [eRIC folder](https://github.com/PaulZC/Pyrotechnic_Balloon_Cut-Down/tree/master/eRIC) into the Code Composer workspace directory
- Right-click in the Project Explorer window, select "Import" then "CCS Projects"
- Select the folder which you unzipped eRIC_CutDown into

You can now make alterations to the code, rebuild the project to produce a new .hex file and then use the easyRadio Companion to programme the eRIC with the new code.

### License

This project is distributed under a Creative Commons Attribution + Share-alike (BY-SA) licence.
Please refer to section 5 of the licence for the "Disclaimer of Warranties and Limitation of Liability".

Enjoy!

**_Paul_**