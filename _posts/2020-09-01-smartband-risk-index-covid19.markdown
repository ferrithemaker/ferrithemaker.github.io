---
layout: post
title:  "covid-19 personal cumulative risk index tracker smartband"
date:   2020-09-01 19:44:00 +0200
categories: esp32,covid19
---

Inspired by the classic radiation dosimeters that we have seen in many documentaries and films, the idea of ​​the project is to create a wearable device that allow us to measure the acc
umulated daily risk of exposure to potentially dangerous environments in relation to the transmission of covid-19.

As we know, one of the main transmission factors of covid-19 is the proximity to other people who may be infected by the virus and therefore, one of the objectives to improve preventi
on is to be in environments where there is a safe distance between people and control the flow of movements around you.

The covid-19 personal cumulative risk index tracker is a wireless device that is configured in promiscuous mode, thus acting as an electromagnetic spectrum analyzer at the frequencies
 used by wireless devices.

Actually, almost everyone wears a device with a wireless connection on them, and every device with this type of connection, even if it is not connected to any network or in use, regul
arly emits a series of beacon signals to identify itself in a unique way.

The covid-19 personal cumulative risk index tracker recognizes these signals and their intensity, density and variability, which allow us to know approximately the flow of people arou
nd you and based on that information, plus a real-time data of local infection cases, the device creates a reliable daily cumulative index of exposure risk, like the radiation dosimet
ers.

The central point of the project is not the hardware itself, quite simple indeed, but the algorithm that calculates this index based on the electromagnetic frequency readings. The ide
a is not simply to detect the number of devices around you, but to analyze the variations of the signals intensity,  and above all, analyze the flow of devices around you. 

These data allow us to calculate what kind of environment we are in, generating various types of profiles:

- Very dense environment and low variability: (moderate / high risk)
- Very dense environment and high variability: (high / very high risk)
- Low dense environment and low variability: (low risk)
- Low dense environment and high variability: (moderate risk)

Based on these profiles we can calculate a daily accumulated index that will tell us not only if at a specific moment we are in a potentially dangerous environment (since this is gene
rally quite obvious), but it will also show us an accumulated value throughout the day, which will give us a global assessment of our daily behaviour (low risk / medium risk / high ri
sk) and will allow us to be aware in order to adjust it and minimize further risks.

This index can be weighted with real time data of local infections rates from online oficial sources like covid-19 API to create a more reliable index.

The device consists of a wireless connectivity microcontroller with the ability to work in promiscuous mode (in our case an ESP32) and a battery (a small power bank or a LiPo battery)
. To display the information you can use an OLED screen (this is the case in the demo example) or simply a color coding system using LEDs to indicate the different levels of accumulat
ed risk.

![Smartband prototype](https://ferranfabregas.me/wp-content/uploads/2020/08/covidsmartband1-rotated-e1598556906614-768x1024.jpg)



Check out the [repo file](https://github.com/ferrithemaker/covid-19-personal-cumulative-risk-index-tracker) to download the code.
