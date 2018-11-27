# CDT-Physical-Computing

## Find me at http://bit.ly/2FHvwRo

<p align="center">
    <img src="images/ICAHLOGO.jpg" alt="ICAHLOGO" width="800">
</p>

# Introduction

Welcome to this tutorial about the Raspberry Pi microcomputer and its amazing capabilities. This tutorial intends to offer you:

1. An overview of Raspberry Pi – one of the most popular microcomputers in use today.
2. A toe-dipping introduction to the Python programming language.
3. An understanding of Raspberry Pi's physical pins, which we can use to make it talk to all sorts of electronics – from within our Python programs!

It may also be useful as a reference during our hackathon.

We will work through this sheet as follows. For each of the following chapters, the tasks are grouped into **ascending order of difficulty**. Please attempt all tasks under **Mandatory exercises**, and if you have time before we move on, have fun with the **Optional exercises**.

**One plea**: If you are done earlier than your neighbour, please help us out by offering your help to them. Explaining something is a sure-fire way to really understand it yourself!

# An Overview of the Raspberry Pi (RPi)

## What is the Raspberry Pi?

Raspberry Pi is a small computer the size of a credit card that you can plug into a monitor, keyboard and mouse. You can use it in the same way as you would use your desktop PC or laptop. You can generate spreadsheets, do word processing, browse the internet, and play games. It also plays high-definition video.

However, what will make it interesting for us is its capability for use in electronics projects! The main aim of the Raspberry Pi is to teach anyone how to use programming and electronics to realise their ideas. Raspberry Pi comes with a free Linux operating system that runs from an SD card, and it is powered by a USB phone charger.

<p align="center">
    <img src="images/pi3card.png" alt="The Raspberry Pi (version 3)" width="400">
    <figcaption align="center">The Raspberry Pi (version 3)</figcaption>
</p>

## Models of Raspberry Pi

Since its original launch in 2012 there have been a number of different models with the most recent model having a quad core processor runnning at 1.4GHz and with 1GB of RAM.

<p align="center">
    <img src="images/rpimodels.PNG" alt="The Raspberry Pi (version 3)" width="800">
</p>
<p align="center">
    <img src="images/rpimodelscompute.PNG" alt="The Raspberry Pi (version 3)" width="800">
    <figcaption align="center">Different Raspberry Pi models through the years</figcaption>
</p>

We will be working with the RPi 3 Model B which is based around a 1.2 GHz 64-bit quad-core ARM Cortex-A53 processor, has 1GB of RAM, while the smaller and cheaper Zero W is based on a 1 GHz single-core ARM1176JZF-S processor with 512GB RAM. Both have 802.11n Wireless and Bluetooth 4.1 included on the chip. Look at them – all of this is included in those black chips soldered onto the boards! That's also why we call these little wonders "System on a Chip" – the entire computer system resides in silicon.

## Physical layout of Raspberry Pi

<p align="center">
    <img src="images/RPI3Blayout.jpeg" alt="The Raspberry Pi (version 3)" width="600">
    <figcaption align="center">Raspberry Pi Layout</figcaption>
</p>

The above picture shows a Raspberry Pi 3. On the right-hand side, you have four **USB ports** and one **Ethernet** port. Next to the USB ports, there is a **USB/Ethernet Controller**, which translates data between the ports and the main processor, because the processor itself doesn't understand the USB or Ethernet protocol. At the top, you can find the **General Purpose Input/Output (GPIO) pins** (40 of them to be precise). Down the bottom middle is the **CSI (Camera Serial Interface) connector**, which allows you to connect mobile-phone-style cameras directly to the Pi. Of course, you also have the option to connect a webcam via USB. At the right-hand side, you can find a **DSI (Display Serial Interface) connector** that you can use to connect an LCD screen. At the bottom, you can find the **HDMI port**, which allows you to connect the Pi straight into a monitor. Next to this port, you can see the **USB power connector** and also an **audio port**. The back side of the Pi houses a micro SD card slot for the SD card containing the operating system and user data – just like a classical hard disk.

## Important Note

Before we continue, please be aware of the following limitations when using your Raspberry Pi.

* Always make sure you supply only 5V to the RPi.
* Unlike Arduino, RPi does not have over-voltage protection on the board (yet), so be careful when making GPIO connections.
* Never connect more than a potential difference of 3.3V to the GPIO pins (for example, when using sensors to feed data into the Pi).
* Never demand that any GPIO pin source or sink more than 16mA.
* Pins can only supply a maximum current of 50mA.

During this workshop, if you are unsure about connecting something new to your Raspberry Pi (particularly anything feeding a voltage or a current into it), do come and ask one of us mentors first – it might prevent your board from frying! Let us now consider what we _can_ do with those pins!

## General Purpose I/O Pins (GPIO)

Your Raspberry Pi is more than just a small computer; it is a hardware prototyping tool! The RPi has **bi-directional I/O pins**, which you can use to drive LEDs, spin motors, or read button presses. Using these pins requires a bit or programming. While you can use a [variety of programming languages](http://elinux.org/RPi_Low-level_peripherals#GPIO_Code_examples) to \"do\" GPIO, we will use a reliable, easy-to-use language throughout this hackathon: **Python**.

###  GPIO Pinout

As we saw above, the GPIO is arranged as a header of 40 electrical pins, which makes it easy to connect it with an external circuit, using jumper wires.

<p align="center">
    <img src="images/rpi_new_pin.jpg" alt="The Raspberry Pi (version 3)" width="300">
    <figcaption align="center">Raspberry Pi GPIO Orientation</figcaption>
</p>

<p align="center">
    <img src="images/RPi_pin_layout.svg" alt="The Raspberry Pi (version 3)" width="200">
    <figcaption align="center">Raspberry Pi GPIO Layout</figcaption>
</p>

The image also shows the additional data protocols that can be accessed through some of the GPIO pins: [Serial (UART)](https://learn.sparkfun.com/tutorials/serial-communication), [I2C](https://learn.sparkfun.com/tutorials/i2c), [SPI](https://learn.sparkfun.com/tutorials/serial-peripheral-interface-spi), Pulse width modulation ([PWM](https://learn.sparkfun.com/tutorials/pulse-width-modulation). We will actually use the I2C protocol to control an external circuit board for DC motors later.


