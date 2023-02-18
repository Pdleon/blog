---
title: "Teams SIP Gateway - Enable and Provision Polycom VVX 500"
date: 2021-12-07
tags: [Teams, Telephony,Phones,Polycom]
---

## Introduction

When this new feature was released, it was time to dust my old Polycom VVX 500 phone and provision it for Teams basic call functionality.

The official Microsoft documentation for all the pre-requisites and supported devices can be found here:

- <https://docs.microsoft.com/en-us/microsoftteams/sip-gateway-plan>

- <https://docs.microsoft.com/en-us/microsoftteams/sip-gateway-configure>


## Procedure

- Enable your custom or global policy to enable SIP devices can be used for calls

![](images/SIPGateway03a-EnableCallPolicySIPDevice.png)

- I went deep dive immediately and ignored a very important step which caused me some wasted time and some troubleshooting efforts. Go ahead and reset your phone to factory defaults.

![](images/SIPGateway01-RestoretoDefaults.png)

- Set your clock, time zone and profile and change the default admin password

![](images/SIPGateway02-SetupTimeandProfile.png)

- Set your provisioning server URL based on your location

> Americas: http://noam.ipp.sdg.teams.microsoft.com

![](images/SIPGateway03-ProvisioningServerURL.png)


- If all the network ports and firewall pre-requisites are met, let the magic take place automatically. The phone will reboot a couple of times perhaps downgrading or upgrading the firmware in my scenario to the approved VVX500 firmware 5.9.6.2327

- Reaching the provisioning server

![](images/SIPGateway04-ContactingProvisioningServer.png)

- Phone restarting

![](images/SIPGateway05-RestartingPhone.png)

- Initializing and setting the firmware to the approved version

![](images/SIPGateway06-WelcomeBoot.png)

- Network initializing

![](images/SIPGateway07-InitialNetwork.png)

- Provisioning successful

![](images/SIPGateway08-ProvisionSuccessFul.png)

- Press on the phone sign in button and the following screen will appear

![](images/SIPGateway09-DeviceLogin01.png)

- On your computer or mobile device, go to <https://microsoft.com/devicelogin> and enter the code that appears on the phone, authenticate if required

![](images/SIPGateway10-Devicelogin02.png)

- You are now signed in

![](images/SIPGateway11-DeviceLogin03.png)

- Phone is now ready for inbound and outbound calls

![](images/SIPGateway12-PhoneSignedin.png)

- The phone now appears registered in the tenant. As you can see, there are two objects due my previous attempt that did not work as I did not reset the phone to factory defaults, leaving a ghost object. As of today, I cannot delete this object nor I can find this device in Azure AD or Intune. Until I figure this one out, this can be an administrative hassle.

![](images/SIPGateway13-PhoneRegistered.png)

In Azure AD, I can trace my failed and successful attempts to sign in but I cannot find this object yet.

![](images/SIPGateway14-AzureSignDetails.png)


## Final Thoughts

Process was straight forward and a nice to have feature in case you have an old supported phone around and want to register for basic Teams' meetings and PSTN functionality.

This process may not scale well for a large corporation with large volume of older phones and do not want to invest in new devices or my preferred choice of a certified headset. For C level, admins or the average user, I do not recommend as a primary device but evaluate as last resource or a specific use scenario.

Read the official documentation for all the working functionality and the current limitations.

Still need to evaluate this process and functionality further, as a common area device and test it with conditional access so I don't have any notes or thoughts yet.