---
title: "Microsoft Teams PSTN Outbound Caller ID Mask with a Service Number or Resource Account Number ( Direct Routing DID )"
date: 2021-05-12
tags: [Teams Policy, PSTN]
excerpt: "Teams PSTN Outbound Caller ID Mask Policy"
categories: Teams, Voice
---

## Request

To mask outbound caller ID by location with the corresponding office number DID which is owned by their direct routing solution and assigned to an AutoAttendant Resource Account.

## Procedure

We are not going to cover in detail how to assign a Direct Routing DID to a Resource Account but high level steps:

- Create new Resource Account through Admin Portal or through Powershell ( AutoAttendant or CallQueue ); Autoattendant in our case
- Assign the proper license to the Resource Account
- Assign desired number to the Resource Account through powershell only


```powershell
Set-CsOnlineApplicationInstance -Identity ResourceAccountAA@domain.com -OnpremPhoneNumber +1XXXXXXXXXX
```


---

Now that we have covered how the AutoAttendant gets the desired main office number, we can start creating a new policy for masking every outbound call.

- Obtain Object ID of the AA Resource Account covered previously
- Create a new calling line identity policy and substitute with the Resource Account objectid

```powershell
$Id = (Get-CsOnlineApplicationInstance -Identity ResourceAccountAA@domain.com).objectid
New-CsCallingLineIdentity -Identity "OfficeCallerID" -CallingIDSubstitute Resource -EnableUserOverride $false -ResourceAccount $Id -companyname "Company Name"
```

## Assignment

We have a couple of options to do this :

- Option 1: Direct assignment to a user through powershell or in the Teams Admin Center - Users ; then editing the policies and assigning the new policy

![](images/CallerIDPolicyDirect.png)

- Option 2: Since the request is for users to have a different outbound number based on location tied to a different AutoAttendant (Repeat all the steps above to create another AA on a different location) we are going to assign policies to a security group that has membership based on location.

- Create a new security group in Azure AD or use an existent one that covers all the members in the desired location

![](images/AzureTeamsCallerID.png)

- Assign the policy to the group just created:
  - Grab the group id through the group properties in Azure AD or powershell
  - The rank is important for which policy takes precendence if the account is part of several group policies

```powershell
 New-CsGroupPolicyAssignment -GroupId xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -PolicyType CallingLineIdentity -PolicyName "OfficeCallerID" -rank 1
```
The policy now is assigned to a group and the hierarchy of assignment is direct->group->global

![](images/CallerIDPolicyGroup.png)

## Final Thoughts

This solution works great if the onboarding process takes care of adding new hires to the proper security group in AD based on their location and no need to worry about Teams' policies.

One scenario that we did not touch is to apply this to all company wide and while the previous steps work well there is a possibility to do it at the SBC gateway level by masking every source number for outbound routing or setting the global caller ID policy with a Microsoft service number and translating that number to company wide main number at the SBC.Possibly requires less maintenance and configuration but less control if the company is leveraging direct routing as a service with a third party provider.

What about e911 implications ?. According to Microsoft's documentation, all emergency calls will always send the user's telephone number (caller ID). When dialing 933, I can confirm that I'm hearing back my emergency location but I'm not using any third party solution. Always conduct your own tests and reach out accordingly if it's not the case for your solution.