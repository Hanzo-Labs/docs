# Setting up RPI2040 FreeRTOS

This is rather simple.

```bash

1. git clone https://github.com/Hanzo-Labs/RP2040-FreeRTOS.git
2. cd RP2040-FreeRTOS
3. git submodule update --init --recursive
4. mkdir build
5. cd build
6. cmake ..

```

the above repository already have all the setup needed for FreeRTOS on RPI2040.

Not sure about dual core support but blinky works so far.


