---
title: "How to receive images directly off of Satellites"
tags:
    - Explanation
    - Guide
date: "2024-11-23"
thumbnail: "/assets/img/thumbnail/NOAA.png"
bookmark: true
---

## General Understanding

Most weather satellites like [NOAA](https://www.noaa.gov/) or Meteor M2 transmit images back down to earth over VHF or UHF radio bands.

These are all free to receive without a license, just don't transmit on frequencies you don't know unless you know exactly what you are doing.

They send down images of the earth on different light spectrums and with different data like rain and thermal data overlayed, these can be used for Meteorology or just as a thing you can brag to your friends about.

There are several methods to receive these radio transmissions, from the easy way with an SDR(Software Defined Radio) and a Laptop to the hard ways with just a HAM Radio and a phone.

All you need is a device capable of receiving these frequencies and a device capable of decoding the received transmissions.

In this guide we will go into how to receive analog NOAA APT images, meaning we will just need some simple equipment you might just have laying around at home.

## What is NOAA APT?

NOAA Weather Satellites are a series of satellites sent up by the National Oceanic and Atmospheric Administration for the purpose of further studying our earth and for Meteorology Purposes.

They send down images using APT, (Automatic Picture Transmission) thissystem is an analog image transmission system developed for use on weather satellites.

They also send down images using other types of Transmission but we won't go into that since this is a beginners guide.

## Receiving NOAA APT using an SDR, a Laptop and a V-Diapole Antenna (Easy Method, $30 - $90)

This is the easy method, it costs anywhere between $30 and $90 depending on if you want the good equipment and if you want to DIY some stuff.

Let's first talk about what a Software Defined Radio(SDR) is, an SDR is a device that digitally receives radio signals, the one I'm going to be referencing in this guide is the [RTL-SDR V4](https://www.rtl-sdr.com/V4/), a USB dongle type SDR, which you simply plug into your Computer, get some software like [SDR++](https://www.sdrpp.org/) or [SDR#](https://airspy.com/download/) running (Personally I recommend SDR++) and you're ready to go besides for some simple driver installations.

Another thing you will need with an SDR is an antenna with the correct connector.

In this case we will be using a [V-Diapole Antenna](https://en.wikipedia.org/wiki/Dipole_antenna) (also commonly refferred to as a "Rabbit Ears Antenna") since it is the cheapest and easiest to use in this scenario.

You can either build this kind of Antenna yourself (there are lots of guides for that on the internet) or buy one like the [RTL-SDR Blog Multipurpose Dipole Antenna Kit](https://www.rtl-sdr.com/using-our-new-dipole-antenna-kit/)

Now let's talk about how to set up the software.

In this case, we will be using SDR++.

To set up your RTL-SDR BLOG V4, please use [this guide](https://www.rtl-sdr.com/rtl-sdr-quick-start-guide/) but do not complete Step 13 and further since we will be using SDR++.

Now download SDR++ Nightly from [this page](https://www.sdrpp.org/), extract the downloaded file and open it, it should look something like this: 

![FolderInside](/assets/SDRPPFOLDER.PNG)

Go ahead and open sdr++.exe

This is what you should be greeted with:

![SDRPPSTART](/assets/SDRPPFIRST.PNG)

Firstly, select RTL-SDR as a Source

![SELECTSDR](/assets/SELECTSDR.png)

Now, select your SDR and change the sample rate to the highest possible (for example 2.4 MhZ or 3.2 MhZ), this will ensure you have the highest possible quality.

Also slide the "Gain" slides to the maximum.

![SELECTURANDSR](/assets/SELECTURANDSR.png)

Now that we have our software set up, we simply need to choose which Satellite to receive and learn how to track it.

At the time of writing this there are 3 functional NOAA Satellites you can receive from.

NOAA 15, 18 and 19.

In this case I will be using NOAA 19, but you should just use whichever Satellite passes over you at the most convinient time.

To see the frequencies of these Satellites and where they are/when they will pass over your location, you should use [N2YO](https://www.n2yo.com/).

After searching for whichever Satellite you want to receive, you should land on a page similar to this:

![N2YOFIRST](/assets/N2YOFIRST.png)

The most important information we need to extract is the time of the pass, the Maximum Elevation and the frequency.

![N2YOINFO](/assets/N2YOINFO.png)

1: Start time, this is the time the Satellite will start to be visible/able to be received

2: Max elevation, this is the Maximum elevation in degrees the Satellite will go over the horizon, 1° meaning just barely and 90° meaning directly overhead, I would not recommend trying passes with a Max. Elevation of under 25°

3: Frequency, the first frequency (in this case 137.100MhZ) is the APT Frequency for this particular Satellite.

Now, to actually receive the Satellite you will most likely need to go outside.

So bring a laptop, your radio equipment and your phone with you and set it up in an area with a mostly clear horizon.

Now get an app like [Look4Sat](https://github.com/rt-bishop/Look4Sat) on your phone, this will help you correctly track the Satellite with your Antenna to get the best frequency possible.

Set your Radio setting to WFM on SDR++, then adjust your recording settings to either Audio or Baseband, Audio will have the smallest filesize but a tiny bit of quality loss and Baseband will have a big filesize but you will be able to do the most with it.

![RADIOSETTINGSSDRPP](/assets/SDRPPRADIOSETTINGS.PNG)

Once the satellite starts being visible according to Look4Sat, go ahead and press on Record on SDR++ and start tracking the Satellite with your antenna like this:

![TRACKSAT](/assets/TRACKSAT.PNG)

Each V-Diapole antenna side should be around 53cm long and there should be an angle of about 120° between them.

Now you should get a signal that looks like this on SDR++:

![NOAASIG](/assets/NOAA.png)

If you are using the Audio recording setting you should adjust your Bandwidth tightly around the signal, the bandwidth is the little white selection field around your cursor.

This will make the signal get a little better.

FOR DECODING PLEASE GO TO THE HOW TO USE SATDUMP SEGMENT AT THE END OF THIS GUIDE

## Receiving NOAA APT using a HAM Radio, an Android Device/Laptop and an app (Hard Method, $20 - $50)

This method is slightly harder since you won't be using dedicated equipment, all you will need is a [HAM Radio](https://en.wikipedia.org/wiki/Ham_Radio) like a [Baofeng](https://www.baofengradio.com/) or other cheap chinese ones, all they need to do is be able to receive frequencies around 137MhZ.

All you need the Android Device or Laptop for is recording and decoding the received signal and tracking the satellite.

You can also do the tracking with an Apple device by using [N2YO.com](https://n2yo.com)

For this, first download [Look4Sat](https://github.com/rt-bishop/Look4Sat) and [Satdump](https://www.satdump.org/) on your Android Device.

Look4Sat is used as a way of tracking the Satellite and Satdump is used for decoding the received signal.

Also download any app you can record audio on.

Let's first look at how to use Look4Sat, when you open the app you should be greeted with this screen:

<img src="/assets/LOOK4SATFIRST.png" alt="LOOKSATFIRST" width="540" height="1200">

To start, press on settings

You should now get to this screen, on which you should press the buttons indicated in the image below, this will get your current location over GPS and update the list of available satellites to track.

You can however also just enter your location manually.

<img src="/assets/LOOK4SATSET.png" alt="LOOKSATSET" width="540" height="1200">

Now press the back button to get back to the original screen, then press the button indicated below to get to a list of satellites that are available to be tracked:

<img src="/assets/LOOK4SATFIRSTINT.png" alt="LOOKSATSET" width="540" height="1200">

You will now see a list with a lot of Satellites available.

In this case we will search for NOAA in the search bar above and select the Satellites NOAA 15, 18 and 19 since these are NOAA Satellites that are available to be received using VHF/APT.

In this guide we will focus on NOAA 19.

After pressing on the two checkmarks at the bottom after selecting the Satellites you should see a list of passes.

Go ahead and press on a pass that is at a convinient time for you.

I don't recommend choosing a pass with an elevation of below 25° since you wont be able to receive them well.

Elevation is the amount of ° the Satellite will go over the horizon, 1° meaning just barely and 90° meaning directly overhead

<img src="/assets/LOOK4SATTRACK.png" alt="LOOKSATTRACK" width="540" height="1200">

In the middle you will see the Satellite's path and current location if it is passing overhead, this screen will use your device's sensors to give you a cursor, that way you can see exactly where the Satellite is.

Now get your HAM Radio and tune it to the frequency shown on this screen under APT, it will most likely be 137.XYZ.

After doing that, get to an area where the horizon is mostly clear of trees or building and wait for the pass to start, when the pass starts use your phone to record the tones you will be hearing over the HAM Radio.

For best reception, hold your HAM Radio high into the air.

After the pass is over you will now save this recording and open Satdump on your Phone or Laptop.

## How to use SatDump

While this segment is demonstrated on a Computer, the steps should be the same on your Mobile Device.

After the pass, stop the recording and download [SatDump](https://www.satdump.org/), we will use this to decode the Signal we just got into an image.

Extract the downloaded file and open satdump-ui.exe

This is what you should be greeted with:

![SATDUMPFIRST](/assets/SATDUMPFIRST.PNG)

Firstly, search for "NOAA APT" in the search bar:

![NOAAPTSATDUMP](/assets/SATDUMPNOAAAPT.PNG)

Now select your recording, where you want the images to be stored and if you recorded in baseband or audio.

Also select which NOAA Satellite you recorded and turn off "SDR++ Noise Reduction", Samplerate should be set automatically.

Then press Start to start decoding.

You should first see something like this:

![DECODING1](/assets/DECODING.PNG)

Then it should turn into something like this:

![DECODING2](/assets/DECODING2.PNG)

And after a tiny bit it should send you back to the start screen, this means your decoded images are in the folder you set as output.

This is what you should expect as an output in the folder:

![DECODEDFOLDER](/assets/DECODEDFOLDER.PNG)

Here you see your decoded image in lots of different channels like Thermal, with rain overlay, with a map overlayed, etc.

Congrats, you have done it!

You have received images from a Weather Satellite!

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
