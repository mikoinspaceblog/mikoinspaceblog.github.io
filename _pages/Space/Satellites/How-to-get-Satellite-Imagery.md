---
title: "How to receive images directly off of Satellites"
tags:
    - Explanation
    - Guide
date: "2024-06-18"
thumbnail: "/assets/img/thumbnail/NOAA.png"
bookmark: true
---

## General Understanding

Getting Images off of Satellites is pretty easy, all you need is a simple antenna, a Software Defined Radio (SDR) and a computer or even android mobile device.

The Satellites that are most used for this hobby are the American NOAA Satellites and the Russian Meteor M2 Satellites.

Both of them are in a low sun-synchronous and almost polar orbit, meaning the countries they fly over will vary.

![Orbit](/assets/orbit.gif)

They constantly transmit "images" of the surface of the earth, however they are not captured like typical images.

They are being captured by a sort of "scanner" capturing one line of pixels at a time and instantly transmitting them.

## Differences

There are a few differences between NOAA and Meteor M2.

The most obvious one is that NOAA uses analogue tones to transmit the images while Meteor M2 uses digital signals.

They transmit different "types" of images, most commonly theres APT, LRPT and HRPT.

**APT** (Automatic Picture Transmission) is an analog signal with 2 analog channels, the image resolution is also quite low. [Used by NOAA]

**LRPT** (Low Rate Picture Transmission) is a digital signal with 3 digital channels, it is also a higher resolution than **APT**. [Used by Meteor M2]

**HRPT** (High Rate Picture Transmission) has a greater bandwidth than **APT** and **LRPT**, meaning you can get more channels and a higher resolution. [Used by both]

Meteor M2 Satellites also break more often or undergo maintinance.

## Receiving

### Hardware

Receiving these images is quite simple, the most basic setup you could have consists of a V-Diapole antenna, something like an RTL-SDR dongle as an SDR and an old laptop.

You can get a kit with the RTL-SDR BLOG V4 and RTL-SDR V-Diapole for as low as 50€ on a website like amazon.

![Kit](/assets/RTL-SDR-V4-with-Dipole-Antenna-Kit.png)

### Where is the Satellite?

To know where the satellite currently is and when it next passes over your location you can use websites like [N2YO](https://n2yo.com) or an app like [Look4Sat](https://github.com/rt-bishop/Look4Sat)

If you are using a V-Diapole Antenna for receiving, it might be smart to orient it to where the satellite is, which is easy when looking something like [Look4Sat](https://github.com/rt-bishop/Look4Sat) but might be harder when using [N2YO](https://n2yo.com).

### Software for Receiving

You need something like [SDR++](https://www.sdrpp.org/) to actually use the SDR.

If you have a pass coming up soon, position yourself in a relatively free area where you can maintain line of sight with the satellite.

Plug your SDR into your laptop and start up your software, if you are using SDR++ then the process is quite simple.

1.  Simply select your SDR using the Source menu from the side

![Source Menu](/assets/SourceMenuSDR.png)

2. Put the gain up to max

Now the process varies between NOAA and Meteor

### NOAA

For NOAA, you should scroll down to recording settings and select audio

![Source Menu](/assets/AUDIO.png)

As soon as you see a signal like this you should press record, when it dissapears you should wait a bit and then stop recording, after this go to the decoding step.

![Source Menu](/assets/NOAA.png)

### METEOR M2

For Meteor M2, you should select Baseband and scroll back up to select "IQ Correction"

![Source Menu](/assets/BASEBAND.png)

As soon as you see a signal like this you should press record, when it dissapears you should wait a bit and then stop recording, after this go to the decoding step.

![Source Menu](/assets/METEOR.png)

### Decoding

For decoding, the best option would be [SatDump](https://www.satdump.org/)

In SatDump, select the Satellite you just recorded and import your file, then simply press on decode and watch the images flow in.

---

## Example Images

### NOAA

![APT-A](/assets/NOAAIMAGES/APT-A.png)
![APT-B](/assets/NOAAIMAGES/APT-B.png)
![MCIR](/assets/NOAAIMAGES/avhrr_3_rgb_MCIR.png)
![Rain](/assets/NOAAIMAGES/avhrr_3_rgb_MCIR_Rain_(Uncalibrated).png)
![Thermal](/assets/NOAAIMAGES/avhrr_3_rgb_Thermal_Channel.png)
![Map](/assets/NOAAIMAGES/channel_4_projected.png)

### METEOR

![RGB](/assets/METEORIMAGES/msu_mr_rgb_221.png)
![MSA](/assets/METEORIMAGES/msu_mr_rgb_MSA.png)
![BW](/assets/METEORIMAGES/MSU-MR-1.png)
![MAP](/assets/METEORIMAGES/rgb_msu_mr_rgb_321_projected.png)

---

![MIS Logo](/assets/miko.png)

This has been an MIS Blog Post.
