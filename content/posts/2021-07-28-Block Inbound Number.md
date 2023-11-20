---
title: "Teams Telephony - Block Inbound Number"
date: 2021-07-28
tags: [Teams, Telephony, SBC]
excerpt: "Teams Telephony - Block Inbound Number"
categories: Teams, Voice
---

## Request

To block an inbound (External PSTN) number.

## Pre-requisites

> If applicable
- Administrator access to the SBC
- Tenant Teams Administrator

## Procedure

### Audiocodes SBC


#### IP to IP Routing

The two key settings to determine is the **Source Username Pattern** ( number to be blocked ) and the **destination type** and set the **destination address**it to 0.0.0.0

![](images/ACIPtoIPRouting.png)

#### Classification

This option we have an actual action type to deny this number. Probably the one that will terminate the call faster without going first through all the routing and manipulation rules.

![](images/ACClassification.png)

#### Inbound Manipulation

This option works great if for some reason you want to translate and route this call to a security office or another number. Like the other two, we have control on source and destination depending on requirements.

![](images/ACManipulationRuleExample1.png)

The next example manipulates specific source and destination and sends it to a non existent number. It works but you can adpat it to your needs.

![](images/ACManipulationRuleExample2.png)

### Ribbon Edge SBC


#### Transformation and Call Routing Table

Before Protect Bad Actors was introduced, like in other SBCs, the easiest way is to have a table to normalize numbers and set the table precendece at the top to reject this call based on the source and destination signaling trunk

![](images/RibbonInboundTransformationTable.png)
![](images/RibbonInboundCallRoutingTable.png)

#### Protect Bad Actors

Ribbon introduced this feature in version 8.xx and above.


In order to add a new entry to the bad actors table, we need to leverage the SBC API. Ribbon recommends curl and has great documentation but if Powershell is your preference like mine, Posh-Ribbon is a fantastic module and kudos to the members of this script.
You can find this module here with usage and description

> <https://github.com/EgoManiac/Posh-Ribbon>

The schema for the rest API of this resource has three required fields. For our purposes of blocking a calling number, the precedence value is not applicable but required to complete successfully

![](images/RibbonBlockBadActorsSchema.png)

- Pre-requisites :
  - Create a REST account
  - Connect-UxGateway ( See script description and Ribbon documentation to enter your own credentials )
  - Identify the next available id ( In this case I did not have any entry so I start with 1). Use function Get-UxResoruce to determine the id list or look in the SBC table for Bad Actors under the system settings.

```powershell
New-UxResource -args "ActorType=0&ActorData=+1925xxxxxxx&Precedence=0" -resource ribbonprotectbadactors/1
```
Notice that there is a single string required and all values are separated by the character "&"

For additional entries and schemas, look into the ribbon documentation.

Now that we entered a new resource, we can see in the table that X number is being considered a bad actor. This in combination with the Country Level Setting determines the normalization of this number. In our case is set to United States to normalize this number.

![](images/RibbonBlockBadActors.png)

### Teams Tenant Block Inbound Number

This is very straight forward, you can block a single number or insert a regex pattern to block a did range of numbers.
Notice that this may take a few minutes to hours to work. In my experience, about two hours and the source will just get a busy tone when dialing any number in the tenant.

For exemptions to this pattern, please see documentation on **New-CsInboundExemptNumberPattern**



![](images/TeamsBlockInboundNumber.png)


If you are using Microsoft dial plans, then this is a quick and fast way to block a single number but it's not applicable to direct routing or DRAS. It would be great to have a global option to disable this on the client and not make it available by policy if this is your case. If I'm wrong and anyone validates that blocking a number still passes through ignoring the client blocked number table when using direct routing or DRAS, please feel free to shoot me a comment.
If that is your case, you have to reach out to your Teams Admin to enter this number at the tenant level.


![](images/TeamsClientBlockNumber.png)

## Final Thoughts

There are multiple ways to achieve the same result and depending on the requirements and need for scaling, one option will fit better. My preference would be to keep everything in one place and at the SBC level if applicable for management, scalability and troubleshooting efforts. An SBC solution is more robust and has more options for routing and manipulations.
If the environment is Direct Routing as a Service, the provider may have a unique or similar way to accomplish this. Requests and results may vary per provider but if you want to have control and not depend on the provider, then adding a new pattern at the tenant level will work just fine.

Regardless of choice, gather all requirements, test, capture traces and then implement to find out the actual user experience on source and destination end to end and make sure it will work the way designed, desired and can scale up for a team of admins to manage this feature. Never leave it to a single admin to know what is going on when blocking numbers.

There may be other ways to achieve the same result and other SBC vendors in the mix but these are the ones I have had a chance to play with.
