---
title: "AudioCodes ATA Teams SIP Gateway Integration"
date: 2024-02-19
toc: true
tags: [Teams, Audiocodes, SIP Gateway]
categories: [Teams, Devices]
featuredimage: /blog/images/ATASipGateway.png
featuredimagepreview: images/ATASipGateway.png
---

## Overview

In an attempt to review the integration of an ATA to the Teams SIP Gateway, purchased an AudioCodes MP112 as the simplest and cheapest option.

AudioCodes recently released an onbarding guide as a walkthrough but typically there are always hidden assumptions that might stomp the process.

[Audiocodes ATA MP1xx Teams SIP Gateway Integration](https://www.audiocodes.com/media/pafhki3d/onboarding-audiocodes-ata-to-microsoft-sip-gateway-for-teams.pdf)

### Requirements
- MP1xx
- Crossover cable
- Analog endpoint

- Device Firmware:
  - Microsoft supported firmware -  6.60A.367.[001-005] (at the time of writing)

Download firmware directly from AC or download from here (at the time of writing) : [MP-11x FXS/FXO 6.60A.367.005](files/MP11x_SIP_F6.60A.367.005.zip)

## Setup & Activation

- Reset the device ( Hardware Reset)
- Run initial setup through a crossover cable
  - Change network settings to adjust for Internet access
  - If necessary
    - Add public DNS
    - Add public NTP
    - Reset the board ( Software Reset )
- Upgrade firmware to supported version
  - 6.xxx as the time of writing
- Do follow the guide


According to the guide, the ATA will reboot after applying ini changes but this might not be the case for everyone, at least for me until i reset the board and burn the config.
The ATA will reboot and the only way to know if it worked is if the .ini config file took the new values and Microsoft .cmp configuration (See your .ini file or reboot the device)
Keep an eye for the proxyip and trunkgroup in the config file

Snippets of my config file look like this

```
;**************
;** Ini File **
;**************

;Board: MP-112 FXS
;Board Type: 56
;Serial Number: 
;Slot Number: 1
;Software Version: 6.60A.367.005
;DSP Software Version: 204IM3=> 660.15
;Board IP Address: xxx.xxx.xxx.xxx
;Board Subnet Mask: xxx.xxx.xxx.xxx
;Board Default Gateway: xxx.xxx.xxx
;Ram size: 32M   Flash size: 8M 
;Num of DSP Cores: 1  Num DSP Channels: 3
;Profile: NONE 
;License Key limits aren't active full features capabilities are available !;
;----------------------------------------------


[SYSTEM Params]

DNSPriServerIP = 9.9.9.9
DNSSecServerIP = 1.1.1.1
IniFileURL = 'https://uswe.dm.sdg.teams.microsoft.com/device/state/OnBoarding/mmiiaacc
/00908F96C8131708115506mfuhDT85vi6fNBs4U9Cx/lang_en/xxxxxxxxxx.ini'
CmpFileURL = 'http://noam.httpblob.sdg.teams.microsoft.com/firmwares/audiocodes/MP11X.cmp'
AutoUpdateCmpFile = 1
;VpFileLastUpdateTime is hidden but has non-default value
AUPDCheckIfIniChanged = 1
;AUPDLastIniCRC is hidden but has non-default value

[ ProxyIp ]

FORMAT ProxyIp_Index = ProxyIp_IpAddress, ProxyIp_TransportType, ProxyIp_ProxySetId;
ProxyIp 0 = "obsbc-uswe.sdg.teams.microsoft.com", 2, 1;
ProxyIp 1 = "mainsbc-uswe.sdg.teams.microsoft.com", 2, 2;

```

Follow the guide:

In Teams Admin Center:

- Provision the device
- Generate pairing code
- Dial **55**<code> | Wait for the tone
- Wait for sign in
- Go to https://aka.ms/siplogin and authenticate with the account that is licensed based on your pstn solution
- The ATA will be displayed as the device/user  in the SIP Gateway dashboard

![](images/SIPGatewayATA.png)




## Experience

Once the setup and activation is complete, the platform works well, I was able to dial in/out of the analog phone.

- I have not tested additional features like calling policies, e911
- In TAC, there are no capabilities for In-call progress metrics, only completed calls
- There are no actions, just device information.


## Conclusion

There is still more to uncover but so far the integration is complete. Different requirements required custom solutions, setup and configuration
Troubleshooting might be a problem if this process is not very well documented
High availability might come as a concern for certain requirements but that would be more on the ATA configuration and setup.


