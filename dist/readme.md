# PICOPi
Jul 19, 2016

PICO-8 console and stand-alone cartridge firmware distributed in an SD card image for the Raspberry Pi.

*Note from paloblanco - the following text and the distributables in this directory were fetched from the wayback machine on May 7, 2020. The original author of this content, Guillermo A. Amaral B., sadly passed away a few years ago. These materials have been copied over to here so that they are not lost. If you have information you would like to share about Guillermo, or concerns/information regarding the licensing of these distributables, please submit a pull request.*

*Text fetched from: https://web.archive.org/web/20190606034354/https://guillermoamaral.com/read/picopi/*

## Update
### Sat Jan 20 20:02:51 PST 2018

I’ve rebuilt and open-sourced the PICOPi overlay. You can get your grubby hands on it here: https://github.com/gamaral/rpi-buildroot/tree/picopi

For those interested in building/customizing PICOPi and who are not already familiar with Buildroot: https://buildroot.org/manual.html

### Sat Aug 6 12:43:42 PDT 2016

I sacrificed an extra second or two in boot time for ease of deployment. No more having to flash anything. You can simply unzip the contents of the PICOPi archive onto a standard FAT32 formated SD card.

## What is it?
```
PICO-8 is a fantasy console for making, sharing and playing tiny games and other computer programs. When you turn it on, the machine greets you with a shell for typing in Lua commands and provides simple built-in tools for creating your own cartridges. I fell in love this this little virtual console from day one. It catered perfectly to my 8-bit/16-bit graphic and C64 nostalgia.
```

## PICO-8 on the MinnowBoard
Some time ago, I made a similar image for the Minnowboard since there was no PICO-8 build for ARM at the time:


Soon after Zep released a build for Raspbian and all was good – except for the fact that as an embedded engineer, using Raspbian for this purpose made my skin crawl.

I wanted something that I could just pop in and play some games with in my hotel room, without needing to fiddle around with a full blown desktop, or worry about power cutting out and possibly corrupting the OS.

I was sure I could do better, so I found myself with some free time and I made my own OS image for the PICO-8 on the Raspberry Pi…

![Bender](bender.jpg)

I specially wanted to (optionally) be super wasteful and use a single SD card per cartridge (which you can totally do and it’s great). I mean, can you imagine the tiny labels printed on the SD card? I sure can!

## PICOPi
# Features
- Boots directly to the ‘splorer’ or directly to a console (when not in stand-alone cartridge mode).
- Corruption resistant.
- Crazy-fast boot time.
- HDMI audio output on by default.
- Keymaps supported.
- Nothing on screen but PICO-8.
- Raspberry Pi will do a clean shutdown when PICO-8 does.
- X-Box controller support (tested).
# Distributables
## Raspberry Pi
Tested on Model A, A+, B, B+, CM, Zero.

picopi-rpi1.zip

## Raspberry Pi 2
Tested on Model B

picopi-rpi2.zip

## Raspberry Pi 3
Tested on Model B

picopi-rpi3.zip

## Setup
1. Format your SD card with a single FAT32 partition.
2. Unzip the PICOPi onto the SD card.
3. Unzip the PICO-8 archive (from Lexaloffle) onto the SD card (more information in the PICO-8 section below).

## Linux SD Card Setup
*Note - I cannot find this video anywhere*

## Mac OS X SD Card Setup
*Note - I cannot find this video anywhere*

## Windows SD Card Setup
*Note - I cannot find this video anywhere*

## PICO-8
PICO-8 is not free in any sense of the word.

At the moment of writing it will set you back 15 USD for a lot of games which includes PICO-8.

Download the Raspberry-Pi(ARM) archive, expand it in the first partition of the SD card that’s it. It Should Just Work.

Your first partition should look something like this afterwards:

```
bcm2708-rpi-b.dtb
bcm2708-rpi-b-plus.dtb
bcm2708-rpi-cm.dtb
bootcode.bin
config.txt
fixup.dat
start.elf
pico.pi
pico-8/ <----
```

## Stand-alone Cartridge Mode

Download your favorite cartridge from the PICO-8 website, rename it to rom.p8 or rom.p8.png and place it in the boot partition.

Your first partition should look something like this:

```
bcm2708-rpi-b-plus.dtb
bcm2708-rpi-b.dtb
bcm2708-rpi-cm.dtb
bootcode.bin
config.txt
fixup.dat
rom.p8.png <----
start.elf
pico-pi
pico-8/
```
When the Raspberry Pi board boots, it will automatically load the cartrige file and run it.

## Configuration

## Offline Carts
Download your favorite carts from the PICO-8 website and copy them into the pico-8/carts directory on the SD Card. If the carts directory doesn’t exist, feel free to create it.

## Keyboard Layout
If you wish to switch keyboard layout, you will need to modify the following line in config.txt
```
keymap=us
```
The usual standard Linux system keymaps are available; Valid keymap names include:

* azerty
* dvorak
* es
* fr
* us

## Disable Splorer
It’s possible to boot directly to the console instead of ‘splorer’. To do so, comment out, remove or set the following line in config.txt to off:

```
splorer=on
```