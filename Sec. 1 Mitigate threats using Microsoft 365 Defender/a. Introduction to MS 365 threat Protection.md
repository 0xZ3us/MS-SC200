# Introduction

Microsoft 365 Defender is an integrated threat protection suite with solutions that detect malicious activity across email, endpoints, applications, and identity. These solutions provide a complete attack chain compromise story that enables a complete understanding of the threat. And, enables you to remediate and protect your organization from future attacks.

In the sample attack chain graphic below, see the attacker activity visible to each Microsoft 365 Defender product.

![Diagram of Microsoft 365 Defender tools to Defend across attack chains.](https://learn.microsoft.com/en-us/training/wwl-sci/introduction-microsoft-365-threat-protection/media/defend-across-attack-chains.png)

You're a Security Operations Analyst working at a company that is implementing Microsoft 365 Defender solutions. You need to understand how Extended Detection and Response (XDR) combines signals from:

-   endpoints
-   identity
-   email
-   applications

to detect and mitigate threats.

The following are examples of detection and mitigation use cases.

# Explore Extended Detection & Response (XDR) response use cases

## Detection of Threat

This scenario depicts a case where Microsoft Defender for Endpoint detects a malicious payload (which could come from any source, including personal email or a USB drive).

![Diagram the Detection of a Compromised endpoint.](https://learn.microsoft.com/en-us/training/wwl-sci/introduction-microsoft-365-threat-protection/media/compromised-endpoint.png)

The victim receives a malicious email on personal email account (not protected by Microsoft Defender for Office 365 (MDO) or a USB drive and opens the attachment. Once the attachment opens, the malware infects the computer. The user is unaware that an attack has taken place. But Microsoft Defender for Endpoints (MDE) detects this attack, raises an alert to security operations, and provides details about the threat to the Security team. Disable user access from device while infected - MDE communicates to Intune that risk level on this endpoint has changed. Intune marks the account in Azure Active Directory as noncompliant with organizations policy, and Conditional Access blocks user access based on that.

### Remediation

MDE remediates threat – either via automated remediation, security analyst approval of automated remediation, or analyst manual investigation of threat.  
MDE also remediates this threat across your enterprise and across our Microsoft MDE customers by adding information on this attack to Microsoft Threat Intelligence system

### Share Intelligence and Restore Access

Restore Access – Once the infected devices have been remediated, MDE signals Intune to change the device risk status and Azure AD Conditional Access then allows access to enterprise resources (more on the next slide). Remediate Threat Variants in MDO and others – The threat signals in Microsoft Threat intelligence are used by Microsoft tools securing other parts of your organization’s attack surface. MDO and Microsoft Defender for Cloud use the signals to detect and remediate threats in email, office collaboration, Azure, and more.

## from the previous graphic when the user’s device was still compromised.

![Diagram of steps to Suspend access during compromise.](https://learn.microsoft.com/en-us/training/wwl-sci/introduction-microsoft-365-threat-protection/media/suspend-access-compromise.png)

### Access Restricted

Conditional Access knows about device risk because Microsoft Defender for Endpoint (MDE) notified Intune, which then updated the compliance status of the device in Azure AD.

During this time, the user is restricted from accessing corporate resources. This applies to all new resource requests and will block any current access to resources that support continuous access evaluation (CAE)  
People will still be able to do general internet productivity and research (YouTube, Wikipedia, and anything else that doesn’t require corporate authentication, but won’t have access to corporate resources.

### Access Restored

Once the threat has been remediated and cleaned up, MDE triggers Intune to update Azure AD and Conditional Access restores the user’s access to corporate resources.

This mitigates risk to the organization by ensuring attackers who may be in control of these devices can't access corporate resources, while minimizing the impact on user productivity to minimize disruption of business processes.

# Understand Microsoft 365 Defender in a Security Operations Center (SOC)

The following graphic provides an overview of how Microsoft 365 Defender and Microsoft Sentinel are integrated in a Modern Security Operations Center (SOC).

![Diagram that shows the layers and technologies of Security Operations.](https://learn.microsoft.com/en-us/training/wwl-sci/introduction-microsoft-365-threat-protection/media/security-operations.png)

## Security Operations Model - Functions and Tools.

While the assignment of responsibilities to individual people and teams will vary based on organization size and other factors, security operations are composed of several distinct functions. Each function/team has a primary focus area and also must collaborate closely with other functions and outside teams to be effective. This diagram depicts the full model with fully staffed teams. In smaller organizations, these functions are often combined into a single role or team, performed by IT Operations (for technical roles), or are performed as a temporary function by leadership/delegates (for incident management)

 Note

We primarily refer to the analysts by the team name, not the Tier numbers as these teams each have unique specialized skills, they are not a literal ranking/hierarchical of value.

![Diagram that shows the Security Operations Model with functions and tools.](https://learn.microsoft.com/en-us/training/wwl-sci/introduction-microsoft-365-threat-protection/media/security-operations-model.png)

### Triage and Automation

We'll start with handling reactive alerts – which begins with:

-   **Automation** – Near real-time resolution of known incident types with automation. These are well-defined attacks that the organization has seen many times.
    
-   **Triage (aka Tier 1)** –Triage analysts focus on rapid remediation of a high volume of well-known incident types that still require (quick) human judgment. These are often tasked with approving automated remediation workflows and identifying anything anomalous or interesting that warrant escalation or consultation with investigation (Tier 2) teams.
    
    Key learnings for Triage and Automation:
    
    -   **90% true positive** - We recommend setting a quality standard of 90% true positive for any alert feeds that will require an analyst to respond so analysts aren’t required to respond to a high volume of false alarms.
    -   **Alert Ratio** – In Microsoft’s experience from our Cyber Defense Operation Center, XDR alerts produce most of the high-quality alerts, with the remainders coming from user reported issues, classic log query based alerts, and other sources
    -   **Automation** is a key enabler for triage teams as it helps empower these analysts and reduce the burden of manual effort (for example, provide automated investigation and then prompt them for a human review before approving the remediation sequence that was automatically built for this incident).
    -   **Tool Integration** - One of the most powerful time saving technologies that improved time to remediation in Microsoft’s CDOC is the integration of XDR tools together into Microsoft 365 Defender so analysts have a single console for endpoint, email, identity, and more. This integration enables analysts to rapidly discover and clean up attacker phishing emails, malware, and compromised accounts before they can do significant damage.
    -   **Focus** - These teams can't maintain their high speed of resolution for all types of technologies and scenarios, so they keep their focus narrow on a few technical areas and/or scenarios. Most often this is on user productivity, like email, endpoint AV alerts (versus EDR that goes into investigations), and first response for user reports.

### Investigation and Incident Management (Tier 2)

This team serves as escalation point for issues from Triage (Tier 1), and directly monitors alerts that indicate a more sophisticated attacker that trigger behavioral alerts, special case alerts related to business-critical assets, and monitoring for ongoing attack campaigns. Proactively, this team also periodically reviews the Triage team alert queue and may proactively hunt using XDR tools in their spare time.

This team provides deeper investigation into a lower volume of more complex attacks, often multi-stage attacks conducted by human attack operators. This team pilots new/unfamiliar alert types to document processes for Triage team and automation, often including alerts generated by Microsoft Defender for Cloud on cloud hosted apps, VMs, containers and Kubernetes, SQL databases, etc.

**Incident Management** – This team takes on the non-technical aspects of managing incidents including coordination with other teams like communications, legal, leadership, and other business stakeholders.

### Hunt and Incident Management (Tier 3)

This is a multi-disciplinary team focused on identifying attackers that may have slipped through the reactive detections and handling major business-impacting events.

-   **Hunt** – This team proactively hunts for undetected threats, assists with escalations and advanced forensics for reactive investigations, and refines alerts/automation. These teams operate in more of a hypothesis-driven model than a reactive alert model and are also where red/purple teams connect with security operations.

### How It Comes Together

To give you an idea of how this works, let’s follow a common incident lifecycle

1.  **Triage (Tier 1)** analyst claims a malware alert from the queue and investigates (for example, with Microsoft 365 Defender console)
2.  While most Triage cases are rapidly remediated and closed, this time the analyst observes that malware may require more involved/advanced remediation (for example, device isolation and cleanup). Triage escalates the case to the Investigation analyst (Tier 2), who takes lead for investigation. The Triage team has option to stay involved and learn more (Investigation team may use Microsoft Sentinel or another SIEM for broader context)
3.  **Investigation** verifies investigation conclusions (or digs further into it) and proceeds with remediation, closes case.
4.  Later, **Hunt (Tier 3)** may notice this case while reviewing closed incidents to scan for commonalities or anomalies worth digging into:
    -   Detections that may be eligible for auto-remediation
    -   Multiple similar incidents that may have a common root cause
    -   Other potential process/tool/alert improvements In one case, Tier 3 reviewed the case and found that the user had fallen for a tech scam. This detection was then flagged as a potentially higher priority alert because the scammers had managed to get admin level access on the endpoint. A higher risk exposure.

### Threat intelligence

**Threat Intelligence teams** provide context and insights to support all other functions (using a threat intelligence platform (TIP) in larger organizations). This could include many different facets including

-   Reactive technical research for active incidents
-   Proactive technical research into attacker groups, attack trends, high profile attacks, emerging techniques, etc.
-   Strategic analysis, research, and insights to inform business and technical processes and priorities.
-   And more

# Investigate security incident in Microsoft 365 Defender

The following cloud guide demonstrates Microsoft 365 Defender and Microsoft Sentinel working together to investigate a security incident in a hybrid environment.

[Launch Investigate Security Incident](https://mslearn.cloudguides.com/guides/Investigate%20security%20incidents%20in%20a%20hybrid%20environment%20with%20Azure%20Sentinel)

## Knowledge Check

1. Which Microsoft 365 Defender solution can detect an Active Directory Domain compromise? 

[X] Microsoft Defender for Identity
	Correct. Domain compromise is detected with Microsoft Defender for Identity

Microsoft Defender for Endpoint

Microsoft Defender for Office 365

2. Which Microsoft 365 Defender solution can detect a phishing email? 

Microsoft Defender for Identity

Microsoft Defender for Endpoint

[X] Microsoft Defender for Office 365
	Correct. Phishing email is detected by Microsoft Defender for Office 365

3. Which Microsoft 365 Defender solution can detect a malware installation? 

Microsoft Defender for Identity

[X] Microsoft Defender for Endpoint
	Correct. Malware installation is detected by Microsoft Defender for Endpoint

Microsoft Defender for Office 365