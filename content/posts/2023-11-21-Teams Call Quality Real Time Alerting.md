---
title: "Teams Call Quality Real Time Alerting for Premium and MTR Pro Licenses"
date: 2023-11-21
tags: [Teams, Monitor, Alert, MTR]
categories: [Teams, MTR]
---

## Introduction

A few things have changed since I wrote on Teams rules to monitor for offline devices. [Reference Article]({{< ref "/2021-06-23-Teams Device Monitoring and Alerting.md" >}})

In response to the growing importance of real-time call quality monitoring, a set of new rules has been introduced, but limited to accounts assigned with a premium license or MTR Pro License, a restriction that presents a challenge for many organizations. This limitation becomes evident, particularly concerning accounts linked with devices such as common area or shared devices. These specific devices lack inherent capabilities for real-time call quality monitoring without the addition of an extra premium license or assigning an MTR Pro license to a shared device which might be hard to justify. The justification for this necessity demands a thorough evaluation based on diverse and practical use cases and showcases gaps where the licensing framework might not be aligned with customer expectations, licensing complexity and budget.

**Update:** Initially, Microsoft offered this service exclusively to premium licenses. However, as of the time of writing, there has been a highly appreciated change. This license is now included as part of the MTR Pro License. It’s worth noting that the official Microsoft documentation, as well as TAC, have not yet been updated to reflect this change.

![](images/TAC_AlertRules_03.png)

---
## Setup & Activation

Configure either an individual alert or all the premium alerts:

- TAC > Notifications & Alerts > Rules

![](images/TAC_AlertRules_01.png)


Focusing in the Audio rule only:

- Configure all conditions, paremeters and values accordingly


![](images/TAC_AlertRules_02.png)
 

- Add users with a premium license or all your resource accounts assigned with the MTR Pro License
- Leave defaults for the channel alerts in a newly created Teams or specify an existing team channel for notifications
- Activate the alarm


![](images/TAC_AlertRules_04.png)


Alerts would look like this in your teams client

![](images/TAC_AlertRules_05.png)

---
For detailed technical documentation on how to set up and activate it, follow the official Microsoft documentation

- [Microsoft Learn - Real-time Telemetry Alerts](https://learn.microsoft.com/en-us/microsoftteams/alerts/teams-admin-alerts)

---

## Conclusions

### Considerations

The implementation of new monitoring rules serves a critical purpose in ensuring call quality during pivotal meetings for high-priority accounts. A few points to consider with the necessity of teams monitoring rules for call quality alerting:

1. **Proactive Issue Detection:** Monitoring call quality enables swift identification of potential issues before they disrupt crucial meetings. IT support or managed services receive alerts, allowing timely interventions to maintain uninterrupted communication. This is still a reactive process and might not prevent the issue but it gives technical context to an isolated or trendy issue.

2. **Enhanced User Experience:** Guaranteeing excellent call quality in high visibility accounts or conference rooms is pivotal for a positive user experience. It prevents disruptions, fostering productive discussions and decision-making.

3. **Trend Analysis and Improvement:** While not an immediate resolution for users facing call quality issues, monitoring helps in analyzing trends. It provides insights for system improvements, ensuring a better overall experience in the long term.

4. **Complexity in Prioritization:** Balancing the need for monitoring with the rising costs of running a business, like stacking license SKUs, adds complexity to decision-making. Effective resource allocation becomes crucial.

5. **License-based Optimization:** Expanding this feature beyond the Premium and MTR Pro license would highlight the benefit for accounts/devices with standard teams user license or shared device license emphasizes the tailored advantages this feature can offer.

6. **Business Impact:** Excellent call quality directly impacts business outcomes, securing deals, resolving issues promptly, and maintaining client satisfaction for high-priority accounts.

7. **Mitigating Risks:** In industries where communication is mission-critical, monitoring call quality becomes paramount to mitigate risks associated with miscommunications or technical glitches.


### Reasons Why Monitoring Feature Might Not Be Prioritized

1. **Cost Considerations:** Implementing the monitoring feature may come with additional expenses, especially if it requires stacking license SKUs. For businesses on a tight budget, the added cost might not justify its immediate adoption. Businesses may prioritize allocating their budget towards core functionalities or features that directly impact productivity or revenue generation. If the monitoring feature doesn't offer a significant enough value proposition, it might not make the cut in budget allocations.

2. **Comparative Service Offerings:** Other platforms might already include similar monitoring functionalities within their existing license models. For organizations already utilizing these platforms, investing in a separate monitoring feature might seem redundant. Competitors may be including monitoring call quality, without the need for separate add-ons. This integrated approach could be more appealing than investing in standalone monitoring tools.

4. **Support and Maintenance Costs:** Consideration of ongoing support and maintenance costs for the monitoring feature might deter adoption, especially if it requires dedicated resources for upkeep.


