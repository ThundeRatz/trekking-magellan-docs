# Short descriptions

Short list of all features in past and current code. Contains links to current,
closed source as well as open source code and external links to used libraries.
Intended as a file you can Ctrl + F and find what you want. Keep sorted.

* Android:
https://github.com/ThundeRatz/Android-sensors

Android app to send cellphone's sensors data.

* HC-SR04:
https://github.com/ThundeRatz/HC-SR04-driver

Sonar driver. Needs some update to the newer kernel GPIO interface, but we
probably won't touch it since we don't use these sensors anymore. Written to use
interrupts only and no polling, keeps CPU usage pretty low.

* Genetic Algorithm:
http://lancet.mit.edu/ga/

* GPIO:
https://github.com/ThundeRatz/ThunderTrekking/tree/f0a085cac9b1a75d19899b4f36e788fdc78c7f5c/pind

We used to do DMA access (yes, ugly, but all libraries used to do that), until
Device Trees became standard, the DMA addresses were changed and auto
configuration would clash with DMA access. Our so-called Pi-no-DMA driver just
presents some /dev entries to access GPIO's of interest. The RPi was updated not
long before a competition and I did the quickest workaround I could, writing this
driver using the legacy kernel GPIO interface.

* gpio-keys:
https://github.com/ThundeRatz/ThunderTrekking/blob/2e81e65472766f46cc099ce1af3647f8cea8d5d3/Main/scripts/gpio-button-overlay.dts, https://github.com/ThundeRatz/ThunderTrekking/blob/2e81e65472766f46cc099ce1af3647f8cea8d5d3/Main/scripts/gpio-keys.rules

https://www.raspberrypi.org/forums/viewtopic.php?f=107&t=115394 has some
discussion on this overlay.

* GPS
https://github.com/ThundeRatz/ThunderTrekking/blob/f0a085cac9b1a75d19899b4f36e788fdc78c7f5c/Main/src/lib/GPS.cc,
https://github.com/ThundeRatz/ThunderTrekking/blob/5da1e34bb4835452cbc55c29e5cb505803519f7b/gps.c

First one is a C++, newer version and has a few more functions. Second one is
a C version used for a long time.

* I2C header files:
https://github.com/ThundeRatz/ThunderTrekking/blob/5da1e34bb4835452cbc55c29e5cb505803519f7b/include/linux/i2c.h

The Arch header missed some macros and was different from the RPi one, so I started
using this header. It is a merge of relevant fields from https://git.kernel.org/cgit/linux/kernel/git/wsa/linux.git/plain/include/linux/i2c-dev.h,
https://git.kernel.org/cgit/linux/kernel/git/wsa/linux.git/tree/include/uapi/linux/i2c.h and
https://git.kernel.org/cgit/linux/kernel/git/wsa/linux.git/tree/include/uapi/linux/i2c-dev.h.

* I2C module:
https://github.com/ThundeRatz/ThunderTrekking/blob/7939d36c5baf8ae3ef877cb8e73fde49f3e8f13c/mod_i2c.c

I2C workarounds. We had many problems with the bus. This module is a thread
implementing a queue for messages, bus access control, delayed writes in case of
errors and lots of mutexes. Dirty, ugly 385 lines of code that used to work.
Moving devices causing trouble off the bus was much more efficient.

* Joystick
https://github.com/ThundeRatz/ThunderTrekking/blob/5da1e34bb4835452cbc55c29e5cb505803519f7b/joystick.c

/dev/input/js* event interface.

* Kalman filter:
https://github.com/tiagoshibata/KFilter/

* Kinect:
https://github.com/ThundeRatz/ThunderTrekking/blob/5da1e34bb4835452cbc55c29e5cb505803519f7b/kinect_distance.c,
https://github.com/ThundeRatz/ThunderTrekking/blob/5da1e34bb4835452cbc55c29e5cb505803519f7b/kinect_tilt.c

In the end wasn't used in any competition due to limited processing on the robot
and operation under sunlight.

* Lock file:
https://github.com/ThundeRatz/ThunderTrekking/blob/0e82f43fc861ba2d955ca1e31145e3f0ec266390/file_lock.c

Pretty simple, was used in a failsafe to detect main program's end.

* NMEA:
https://github.com/ThundeRatz/ThunderTrekking/blob/7939d36c5baf8ae3ef877cb8e73fde49f3e8f13c/serial_nmea.c

Dropped for GPSd.

* OpenCV:
https://github.com/ThundeRatz/ThunderTrekking/tree/5da1e34bb4835452cbc55c29e5cb505803519f7b/Imagem/algoritmos

* Python code: https://github.com/ThundeRatz/ThunderTrekking/tree/1b2a1373ce95b2dc0f4b0b2b1339965eeeee0eb2

Most of it is also available at https://github.com/ThundeRatz/Python-legacy.
https://github.com/ThundeRatz/Python-legacy/blob/master/README.md says all about
it. Code for image processing isn't included (was a team's choice to make enough
code open so others might start a project but keep central design choices up to
others). Also, tagged *WCXI(2015)*.

* Terminal key input: https://github.com/ThundeRatz/ThunderTrekking/blob/09fff6113b40210e32f71f9e4f57813d088b649f/Main/src/lib/Button.cc

The evdev interface is more suitable.

* Tiva:
https://github.com/ThundeRatz/Motors-Tiva-C-Series-Launchpad

TI's Tiva Launchpad based motor control. To send commands to the board,
https://github.com/ThundeRatz/ThunderTrekking/blob/5da1e34bb4835452cbc55c29e5cb505803519f7b/serial_tiva/serial_tiva.c

* TSIP:
https://github.com/ThundeRatz/ThunderTrekking/blob/7939d36c5baf8ae3ef877cb8e73fde49f3e8f13c/serial_tsip.c

Dropped for GPSd.

* UART:
https://github.com/ThundeRatz/ThunderTrekking/blob/5da1e34bb4835452cbc55c29e5cb505803519f7b/serial_tiva/serial.c

* v4l2:
https://github.com/ThundeRatz/ThunderTrekking/blob/5da1e34bb4835452cbc55c29e5cb505803519f7b/random/v4l2.c

Video4Linux2 access. Just an abandoned draft, later OpenCV was used for camera.
