---
title: "Auto Attendant Toll Fraud Call"
date: 2017-03-17
tags: [Sonus, Auto Attendant]
excerpt: "Configuring and troubleshooting Toll Fraud calls through an Auto Attendant"
categories: [Teams, Voice, IVR]
---

## Problem

Customer  received an email from SIP provider advising of a possible fraud  occurrence. [Source Number] has alarmed for a growing volume of calls to  [+1264xxxxxxx], please verify that destination number is authorized for  business.



![img](https://lh3.googleusercontent.com/nf6tWexCKykmxDbX0BW-IuIlumIADMfWuo9rvHbTiSC1-0_fMfxVeHhIfmBfYEp7HGBk8yezgPJn1JBKrO7zJo_EukedV2m4hmL-pCK9JM-W8GvLNzp9CxWB0U9FDt74aRdXsOBeo95I0Eow1vHOV9PZhlPSS3udcxU0MbQukflVYnlrSBTFcE5xGWrFbD1G_Y0v7Ag7kIAFbUtBP6M3sSo4WCMDmLJZY0DDUqYsP_qZCJ0ONkuIl0q4S5y-T7VEo_NRxXThD25jp5TRhkwf6T0p3ZmBO53ybMQKcVGMVXyAP2WFCiiL1EXCSbhmFgCnhdW5uyG-w2FEFdqXG0d25yj96saiJD80iYrKkZqFU_z4CXJoaXEcCO41bBEj8gXxU-mhCdgCGF4l1rkLklbsi5UCPjpyyztaLtVP191cMJavD9JZ7m4PXXWOPR2jIkDkoVyPqA0shT2Q5bAKyOeiZau9P0amkhgyickjVyBtoaXzASLG1vaYy13JJY_vwDUELohQCICHyPY8h-zEKc6dURcvlkCBNrjTPrsj2uI7lCWPcnxILWmbLOHt1PSv-ZEqh7FX7XW9kc-XUBVfXx5p2f_Tg8qaluQVuZkrEENlWmRyIX9ocKVFU3LMFwlUutIuR8K8fw7EZsfEPsXaw01w_iuqed1DBOPoT6yU24D7=w259-h194-no)



## Troubleshooting

- Search for the source number to identify the user/object assigned to that number.
- Rely on the user activity report under Skype monitoring reports to retrieve more information on the number[s] called.
  - We  can see that there is a large volume of calls (275) to this number  located in Anguilla which the business has no need to interact with.



![img](https://lh3.googleusercontent.com/j33qYL1Mn5yruwfQv-zWocY7yJuPfuxKYj_ZBQYukaf9NDUGXu2co2L4IGTR4x84nvy23PDqIpJ6kALp5nA6570p52SWniA45Sxru50TnitoPE2ZdI9JC-kG8qj49kOfETJEu7l2F0NcAP29e6AaOQZhhnySoxzlaIGuST06BnAf_22_gygm4pJZluLU2OwFJUA7Iq4ljauRY9RSLObbJNeyOP9PJbsDQvtOa6efFdHRx9Dbcm-W3nDZb_NdjdhG91-r_yUeVp6LReh8AuMqvaniMo95MXVJjXWGNDZZc28lK92xqi5CYhWuTlw2Z3qrV9TQWyxLacFabJ3H819joDndtCeaz5xiY1FpUZ6QY4KbFr1KwY-ksdDeK5RF5_ThPtjbt-Gu8aDYA5VInOxLVZdt5iZ5p2_kvQo9C2VOUkfkt6HGDKKcNC4yY00v-QOCbf87NWhvWchVCBkmldirCvGily3eNxskl4tIv-8oIe6RdP4IQaqQGQCjYgeFV7wLxffctr9F8RrHTT47iGmhvu1-grRddfHguxDumFTcRE3WlY4LoJGy0Ep5fWSYUBYAc6G8c-dMB-tT9sKBlP7CxmESS7AkKqurpJv1thbEXZCRoaM6njtwhP-_GxK8zDmkANxe-O4SSHgWNlJwlOO43NTpSVnJBjNhY8JQaXAf=w1183-h810-no)



When  we dig into the details of this call, the most important detail is the  “Referred by” field which will point you out the object that is placing  the calls from  and in our case it was an auto attendant hosted in O365  which its dial plan and voice policy allows to dial out 11 digit number  with the country code of North America +1



![img](https://lh3.googleusercontent.com/saX3d-whMAmk2BUYZqJ6OAvdE-jDQLXIKUuO0dmijjy5FdTcbv6yOZNlDUvQVPyHZXmQdYTD57fjbH26b1DjQq6Wp9YrzDwZoOggkCdU6eBOy_-k_bXbGXDHCnGlrf_wQ6qlbGug3N1B87gmfKAO--bSyq8q2YVjDFy0SpJkfF7VhX6sjrKGlBcVkorCqBSX-JMQhnT9h9lnlPrHCPppkWudOwRsVasj9iotDgcH9WlcUIYGc_RB_swzzcvhvCj3Pxw1AQM39cb4NAu13jocHtjvNXKfoCzVwxSmZ5AMrx4BBZvjY3LgyFdc_w6YdvtZ37h0ePW001M92UKppKD96zdJnzVKf4lXw4SRQGIM2tBfhXxbA_eTuKrS5k0aw9u57iJJ92Bx4qRnKeGWvEMdWjSJ5Pl1wEhCHCitXEDXYGkMwHcG4MLo-5I8Znb5KNeTXzlXc3V76EKwmywoxmXHawE2faXfqFNdnjVvNFKm5hQQ_vVnZCzu-KsnpPNAHf4aKJdsJaiEO33361MR1KWFMZIW9Hs4eOatKkrO872gKr-fxPh69ptUZxL279r2uwyvOMm3bCTO5vvDQCWvSG0ptSfHIioibzt0MM96iXcaBq-puDvbAFQtQp5HALtHv5b5z_uN6KbrbHFA6TJtDVbnAH3LYt2e_AKrvZ-k4I01=w998-h547-no)




##  Solution

There  are multiple ways to address this issue, each solution should be  applied to whatever fits your environment best. In no particular order:

- - Restrict the auto attendant and create dialing rules.
  - Create an outbound trunk configuration rule to manipulate all these area codes and terminate the call.
  - Create  a dial plan and voice policy in Skype that allows/restricts numbers  according to the business requirements and apply it to the Exchange UM  object in Skype.
  - Terminate  [ reject ] the call at the gateway level,  depending on your  environment, this could be done for the calling number [ source ] or  your called number [ destination ].
  - Create  an unassigned number range in Skype, include all the area codes to  block and send that to a recorded announcement. This solution adds  flexibility if for some reason a legit business call gets trapped in the  rule. It can be easily traced, diagnosed, and could politely warn the  caller  to stop such activities.

We  needed to put a plan in place and the easiest and fastest way to  address this was to terminate the call at the gateway level and then  figure it out another solution that fits the environment best.



Here is the list of countries that are part of this loop hole:

| Area |                   Destination                   |
| :--: | :---------------------------------------------: |
| 242  |                     Bahamas                     |
| 246  |                    Barbados                     |
| 264  |            Anguilla (split from 809)            |
| 268  |               Antigua and Barbuda               |
| 284  |             British Virgin Islands              |
| 340  |      US Virgin Islands: St Thomas. St John      |
| 345  |                 Cayman Islands                  |
| 441  |                     Bermuda                     |
| 473  |                     Grenada                     |
| 649  |            Turks and Caicos Islands             |
| 664  |                   Montserrat                    |
| 670  |            Northern Mariana Islands             |
| 671  |                      Guam                       |
| 758  |                    St Lucia                     |
| 767  |                    Dominica                     |
| 784  |             St. Vincent and Grenada             |
| 787  |                   Puerto Rico                   |
| 809  | Caribbean. Bermuda. Puerto Rico. Virgin Islands |
| 868  |               Trinidad and Tobago               |
| 869  |                 St Kitts/Nevis                  |
| 876  |                     Jamaica                     |
| 900  |              Pay_Per_Call Numbers               |
| 939  |                   Puerto Rico                   |
| 976  |              Pay_Per_Call Numbers               |



## Steps

- In our Sonus SBC 2000 we first create a new transformation table and we call it Block Outbound Calls.
  - Add  a new rule, the input field type should be Called Address/Number and  add your regex condition that blocks all numbers destined to the area  codes listed above with any remaining 7 digits.

**^(\+1(242\|246\|264\|268\|284\|340\|345\|441\|473\|649\|664\|670\|671\|758\|767\|784\|787\|809\|855\|868\|869\|876\|900\|939\|976)\d{7})**



![img](https://lh3.googleusercontent.com/q6xqGZhZKBLTmoqlwU3OaCLcS8zewVjcirTF24RPpPMyA7nxnNZJo2SLsnx1mYTdY2pTyIXgShJy0cDkfLQtvmySNrK4DpvZI8o3d9PfA7gSy7Nzp-hfgIsKJ9t4Yk98Nle7LDaB-EDNXOEYMTUWLTnK8gvOvRAj5_qZg3tcA18gKvumHgJH8qVw91xayXOtIKnOHnL95f-_lsANSPMJjCFoMeyW2cDl7Dx9KGg5SU85AKHbpCs1NHdJHooJX3JEI7vPSFVHMd7ly57NL5kw8HrAGyCCs9WQK6wVzxeEZB9SO9po-NwARf6le1EQy8xsu3HMH7inQzimGB-DYcZWJbMymxZGFB8TMZ5gJh_pDxj0SCSQiC0jENL0kJGZFscX3J6voerZqvN4DkEM5VyBJf1I5Yp-UzYyOOjf1mpGXtPhw3aplnBq2DNKfwyzRdK6TmbZiwTotPrHgLY4M9thDlkQGrXP6Cipzx_eg5FaebTPnspVyFsOWEBRnuE4g7MIN8Il7nNKblHOovbOdxdZMU0UsRRreaOLJCfk6PY4eXlBf1gWtpZh9WO9gRBR73U9ZpVY766AcNmyXmm23uUrqNMaExG6EII87TesPQvh0A07dxWkFKu4mt2EeQSliA7ucZyQpz5fp-hk_G2omnv-Sh3VSNOSVZofYNoDkug0=w1235-h577-no)



- Add  this transformation rule to your call routing table that handles calls  from Skype to SIP provider and move it all the way to the top to be the  first rule processed in the route.
  - Number/Name Transformation Table : Block Outbound Calls
  - Destination Type : Deny
  - Deny Q.850 Cause Code : 21 Call Rejected



![img](https://lh3.googleusercontent.com/uZqDeYRKbpaYZsoAEqgbL4XKnsVxNjETEfKL9uIpc9NTJMq1POSisemzIo52Bcs5dfa42P_F_DkEKA6XVDq52x1yjZ29Z8tTcTo8w4iWZVw4x2GNLBKzIWQnyvGiKOz87UVTANKw6-2wRTsCbFlG2cX7OdXAYMn_m8Q0q9pJze6GudAN32R4xeNmZohBaGaqXeXemwKO5Q1uSwppszWK37caQIA_1qzSbuUz5-RSoRbp9e1qR42XTkCfOhGmA1Yj7t6ykRkKOHrrRE0O0tD_v-2I0A2r7uE3qzQhR3pq0VnwV2JZwurujTMDTb2ofqi2QdlNveNHbuI94lr-acgG---zeUjI_Jhh6TqcbOn373DEDklULDsTDbpxXinFzcvy1quX0O40P8D4E25Zt3AutSWbk1HCOfcwYmJljkEzY_I6MFOwC1bF-uC0b6geviLQBQ7wtCUZbWFDdlEq4gTTsA_ROEOMqjYhcfedHrCDdHx0EbPICEdx2PNuOrjZgUO4qGJIn14sz5lVp9ZV8oFbEGz9o0eReN37th5n_JbjG77gmQ74om-rzsaeGUy5c9u_9_Z_MnKwaXlUDW2xzCGlADIJAgqZ5vZuT9AGr7nIu5QRK_NomU2gtc2tVaMqkLVUlEGs4sgBkyVvly8z7885iki0Fk2G0t06dz_4IjbN=w1031-h606-no)



- Apply these rules to all the necessary gateways in your environment based on all your internal routing rules.
- Ready to test, start capturing from your LX tool.
  - Place  a call from your client to any number in the list [ search for hotel  numbers ] or call your auto attendant and dial the number when you get  to the option of dial by extension.
  - In your LX tool, do an advanced search and look for the number called, in our case we see a successful 603 decline code.



![img](https://lh3.googleusercontent.com/hSf-zkiGrXYMH265zCp12btTk74encuUmeXs86W54NQnoCsEVG2_KE0SLMUxmGpVXguddQ-MKacnoDprYngcSuE3NI4ya9yDU5g5fBbWr3lJzCgd1rSRTdzlxkzBPCzjd8nyjT3WPbaf8ik4IpluOhT9k6QOiNq04q8VaZDz5Mq_fY8AUO5zaCQOanVzRptt89UbPGGptlm5fF00GeMt1qNSusF-JEtlQ6Z2r0RYNGT5R04q09l8eDX68UWj9p_k_8azSA81LW2J7jhjKA4_XzvXDZGl6E7wCfxDyr00D9TE6x3kI4h-ExbZPbR2VvJ-fiX6wzQyZzNVqFjelrmR-hwjvKXamuopBGUYJgzniM2qHkH1BVR9JQyhKt-BMYtCLPDUYQuVvNgUMj0oajpvPA0_Innqcbv7G3tVOcfCrJWO5SbDJj-G8_TqDZYIe7ioXYMbZmNSJ42bCmkMCQLeh3OO_feTlGw7WKW2lg1iYecXfsYMiSV_wPUsLk-z8SrpeiKl-Z-JC2Zx8-kuFQJmcEkSf_y80L1rw-LLyUnPl8zsiebJQSQMVGuIoYJXpq7rhQmxkPuDV5yo8vKwYUle4URuf8d5tBmHtmMyErdLy26Hj2WQlKGyC62AbY6RPQG-ZI4u3t8-_IDja4cajOH1PIDn-nvUeRnrHh7_0RHb=w1124-h295-no)



| Response | Code    | Definition    |
| -------- | ------- | ------------- |
| Q.850    | **21**  | Call Rejected |
| SIP      | **603** | Decline       |

If we look at that call, we get the proper response code.



![img](https://lh3.googleusercontent.com/lh2LTcYzMcicygeyMbL99HEX_S9vc3huzgyQWgAcL-EaxSF84p1n_rRSpbLTgohj4bHvfYvT6zBrSRT5pcHGHVaCKNBssru1hdo3Q2edHZ5H77v-Ra11w9lqU_uyGI49A6k-TOa41g_saDOwbP67vqAppza-q_WmGeUafs8-uU7vvoN9ljgPSl9ACyB9AznRiP8ZglCvldOoVXnubw4qShkAOQbxeyYmP67NwmLd77i-79G5viGCRdKEiKMlDLxq4h2sHIe5yqZ3U7v184LVhvBgvdygi0ihH-L56jbw2GhXoR3RAk4j0H5bYFLBEf5NfiI5v5wjzxv4RaKz8OkaUNCa-F9NJsVtadWN2zRmlZfVgtxQTHPEhSuluFtMEdYnJfn3_XL9uGwsK-gKOe9tCELAdMd6idKtBI5sTtWuq1Z8SBziaeBDem-g1MnC09PD5aJVxXb_tA_WwiyoHr0Kl5o2UT6csa7hjpDRzz-ApgLsh7OVAgdDi7V8THoJWBGc3v9fFIlU6IOA4N2Z4L7tlKb4Z0jrur8G7oBXCg8BlTSjM6VlQy4FUDujVX-cFB_NMbG5fpD4g75CKre65ezHz5G86vtcXNrCRcRdDt6IIOnS3s3RzNswy3NLuRAlBUXGfopDJnc6zPRgMRUXranyna22LSDb1-9rm6fqDZUK=w1151-h382-no)



We can also look into the log transcript and follow the call route



![img](https://lh3.googleusercontent.com/-iGwuDKdJr_U2Pda27Uizel2VZGYpzdpcGqsa6e3dE9c3KLqE9v0uI7WZRXz_d_uY3YVwQS4Oa5c7Ft0WpyFbnZOHRi2HTv4PeteNFOc9EcIkjPVcBKy0WQ-hzmWD-AMwoM6gKmLLnb7yTsdUOWOqSrFCk8y5RfSYmXDRj6yj-SqWSY6yVGUhoiEegdUsA0GVfVR_P6cC6_673jXDSaqJzx2A77Fl9KI6YVs59llY7KFDn-zMLReEDjGE1gD9jnRzlQAXbnIEPL-d993D7RqqfyMlxhRD5bYzNCprKpz6-fLChbQd0KzS7VDcSBq7QMYdK5fCZKEFGNW6kXODJBtZ3C0Ekk5fPEqvG9iL82rI65Eo4xlI1E5WRm0Y9GDMMDFmvA3hk0hJA4Ik0okfJjsBTzYXWe3NZm7frNiZudBR1G1er1pIJZEI3L8W-q1XEt52I4xQyBYh69Vo0dDSJdJeSCxiCyw65Ck1sxZq1JYTTjAWfIlHsCt45ElJ3JzGDoMWFb8aDXI-BP2f_ocjunRkBvUEFDzRYcd7s_f-Wf3nElSNJwch4U5ogFhUvndyMAbriXXL9Uwq5gk6x1V6GqHXZAebb-yFF_vyOuyXHoWWmvdu6MGw8NYaw-Wus9RH_160u07JC_8NE0RHK8rX7yl_K9S5FmLU-_rGDlZmH_I=w953-h326-no)






##  Notes

For  now, this solution addresses the issue but will be looking into  implementing other solutions and keep everything contained in the skype  environment, perhaps a dial plan and voice policy applied to the  exchange object is preferable for this specific scenario.

Stay  tuned for an update and feel free to suggest any other possible  solution if you have experienced the same in your environment.



## References



- [SIP Code Response @ Sonus](https://support.sonus.net/display/UXAPIDOC/SIP+Response+Codes+-+Reference)
- [Q.850 Code Response @ Sonus](https://support.sonus.net/display/UXAPIDOC/Q.850+Cause+Codes+-+Reference)
- [About Auto Attendant @ MS](https://technet.microsoft.com/en-us/library/cc526581.aspx)
- [Unified Messaging @ MS TechNet](https://technet.microsoft.com/en-us/library/cc526590.aspx)
