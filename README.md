# ps2avr
Information related to ps2avr bootmapper based keyboards

I have a VE.a clone that I got from aliexpress.
This repo records some notes that I made when 
researching the protocol to get/set keymaps from
the keyboard. My goal was to be able do do this via
Linux/Unix because the Bootmapper client only supported
the Mac or Windows. Maybe some of this information will be
helpful to others.

This repo has a backup of the JSON files used to upload the 
layout to the Bootmapper Mac/Windows client.

Unfortunately, the source code is not available for the binaries
embedded in the Bootmapper Adobe Air app.
These binaries are responsible for the actual USB communication
with the keyboard.

However, the source code for the firmware is *probably* here:
https://github.com/showjean/ps2avrU/


What I ended up doing was capture the USB traffic in sigrok while
doing multiple downloads and a single upload.
Those traces are in the sigrok-traces directory.

I will only mention that the firmware code is a bit hard to follow.
The traces show the relevant info.
However, they roughtly correspond to requests made to vusb.c.
The requests are a HID_REPORT_OPTION.
The author then does a switch on the packet length (wut?) as a
way of differentiating messages.
The code then uses OPTION_GET_REPORT_LENGTH_KEYMAP_LAYER1 to
determine which chunk of memory from KEYMAP_ADDRESS to send out.


