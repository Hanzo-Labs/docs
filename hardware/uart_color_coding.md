# UART color coding.

Well generally UART cable come in many forms.

1. breakout board and jumper wires to the PCB pins. and then USB to micro attaches the other end for serial console.
2. USB cable with UART inbuilt like the PL2303 or the CP2102 etc

UART cable color does for the option 2 are the following.

1. Red - Vcc - dont connect it often, if not powered via this pin.
2. Black - gnd - ground wire -> goes to ground  pin on PCB
3. Green - Tx - transmit wire -> goes to the rx pin on PCB
4. White - Rx - receive wire -> goes to the tx pin on PCB

