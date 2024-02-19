---
title: "AudioCodes ATA Teams SIP Gateway Integration"
date: 2024-02-19
toc: true
tags: [Teams, Audiocodes, SIP Gateway]
categories: [Teams, Devices]
draft: true
---

## Overview

In an attempt to review the integration of an ATA to the Teams SIP Gateway, purchased an Audiocodes MP112 as the simpliest and cheapest option.

Audiocodes recently released an onbarding guide as a walkthrough but typically there are always hidden assumptions that might stomp the process.

[Audiocodes ATA MP1xx Teams SIP Gateway Integration](https://www.audiocodes.com/media/pafhki3d/onboarding-audiocodes-ata-to-microsoft-sip-gateway-for-teams.pdf)

### Requirements
- MP1xx
- Crossover cable
- Analog endpoint

Device Firmware
Microsoft supported firmware -  6.60A.367.[001-005] (At the time of writing)

Download firmware : [MP-11x FXS/FXO](files/MP11x_SIP_F6.60A.367.005.zip)

## Setup & Activation

- Reset the device ( Hardware )
- Run initial setup through a crossover cable
  - Change network settings to adjust for Internet access
  - If necessary
    - Add public DNS
    - Add public NTP
    - Reset the board ( Software )
- Upgrade firmware to supported version
  - 6.xxx as the time of writing
- Do follow the guide


According to the guide, the ATA will reboot after applying ini changes but this might not be the case, at least for me until i reset the device and burn the config.
The ATA will reboot and the only way to know if it worked is if the .ini config file took the new values and Microsoft .cmp configuration. 

An example of how my .ini file looks is




https://aka.ms/siplogin

## Experience

Once the setup and activation is complete, the platform works pretty smooth, I was able to dial in/out of the analog phone.

In-call progress
Join a meeting
Advanced capabilities ?
Actions


## Reports and Metrics

Add report


## Conclusion

Troubleshooting might be a problem if this process is not very well documented


