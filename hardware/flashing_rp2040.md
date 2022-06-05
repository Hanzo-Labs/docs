# Flashing RP2040

use UF2 approach. nothing fancy here. 

1. Hold BOOT button on the RP2040 PCB and power on , release it.
2. folder shows up in /mnt/<user>/
3. copy the generated uf2 file to /mnt/<user>/<rpi_pico>/
4. device autoresets and starts the program
