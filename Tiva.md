#Using the Tiva board

##Using our code (https://github.com/ThundeRatz/Motors-Tiva-C-Series-Launchpad)

Requirements:

- arm-none-eabi-* tools (gcc, ld, optionally gdb)

- TivaWare for C Series

- lm4flash

TivaWare can be downloaded for free at
http://www.ti.com/lsds/ti/arm/arm_cortex_m_microcontrollers/arm_cortex_m4/stellaris_arm_cortex_m4f/toolsw.page,
download links at http://software-dl.ti.com/tiva-c/SW-TM4C/latest/index_FDS.html.
Requires a TI account and filling a few forms to download.

The required files are mostly under a BSD licence and can be found in the internet
(I recommend downloading from TI to get the latest version, but in case you don't
want to create an account and fill their forms):

https://github.com/antoinealb/Tivaware or https://github.com/jhnphm/TivaWare_driverlib
or https://github.com/yuvadm/tiva-c

I haven't tested any of them.

lm4flash is required to flash the board, it can be downloaded at:

https://github.com/utzig/lm4tools

```git clone https://github.com/utzig/lm4tools.git```

##Using ICDI

Requirements:

- arm-none-eabi-gdb

- openocd

Connect openocd to the serial interface:

```openocd -f /usr/share/openocd/scripts/board/ek-lm4f120xl.cfg```

Run arm-none-eabi-gdb. The following might be used as an initialization file:


```
file motor_control.axf # change this to your ELF file
target extended-remote localhost:3333
monitor reset halt
load
set remote hardware-breakpoint-limit 6
set remote hardware-watchpoint-limit 4
b main
c
clear
```

##Creating your code

TivaWare is a great tool for programming, but in case you want an IDE or a more
high-level environment, check
http://www.ti.com/lsds/ti/arm/arm_cortex_m_microcontrollers/arm_cortex_m4/stellaris_arm_cortex_m4f/toolsw.page
for some options.
Keil uVision 4 has built-in compiler and debugger, but the free version is pretty limited
(http://www.keil.com/demo/limits.asp). The Energia project provides an Arduino-like
interface and Arduino compatible functions and is a great choice, too.
