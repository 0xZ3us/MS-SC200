# Introduction

Azure Active Directory (Azure AD) Identity Protection gives you advanced detection and remediation of identity-based risks to protect your Azure AD identities and applications.

You work for a retail organization that has its identities stored in Azure AD. There have been several recent incidents where identities were compromised. It's possible that sensitive customer information was exposed. You'd like to use Azure native services to protect your company from any future incidents. You've decided to use Identity Protection to protect your identity infrastructure.

In this module, you'll explore what Identity Protection is and how to use it. You'll detect risks by using risk policies. Then you'll investigate detected risks and remediate them.

By the end of this module, you'll know how to protect your organization's identities from identity-based risks by using Identity Protection.

## Learning objectives

In this module, you'll:

-   Describe the features of Azure AD Identity Protection.
-   Describe the investigation and remediation features of Azure AD Identity Protection.

# Azure AD Identity Protection overview

Azure Active Directory (Azure AD) Identity Protection helps you to automatically detect, remediate, and investigate identity-based risks for your organization.

The retail company you work for is conscious about its reputation. Compromised identities have previously enabled malicious users to obtain customer information fraudulently. These attacks have affected your organization's reputation, and ultimately its profitability. Your manager has asked you to investigate Identity Protection as a solution. You've been asked to report back on what the service does and how it's used.

In this unit, you'll learn what Identity Protection is and the risks involved in using it. You'll explore the different workflows you can use in Identity Protection to protect your identities.

## What is Azure Active Directory Identity Protection?

Identity Protection is a solution built into Azure AD that's designed to protect your identities through a three-part process.

![Diagram of the Identity Protection overview.](https://learn.microsoft.com/en-us/training/modules/protect-identities-with-aad-idp/media/2-identity-protection-overview.svg)

Your company's specialist expertise is in retail, not in identity protection. It wants to continue to focus on its areas of strength, but still ensure that it's protected against identity risks. Your organization can use Identity Protection to automate the detection, investigation, and remediation of risks related to users' identities without hiring expensive security experts.

## What are risks?

Risks can be described as suspicious activity and actions by users when they sign in, or when they take actions after signing in. That's why risks are categorized in two ways: as user risks and sign-in risks.

### User risk

A user risk is caused when a user's identity or account is compromised. User risks can include:

| Risk | Description  |
|---|---|
| Unusual behavior | The account showed unusual activity or the patterns of usage are similar to those patterns that Microsoft systems and experts have identified as attacks.  |
| Leaked credentials | The user's credentials could have been leaked. For example, Microsoft might have found a list of leaked credentials on the dark web, which could affect your user accounts. |

### Sign-in risk

Here, Identity Protection scrutinizes each authentication request to judge whether it was authorized by the owner of the identity. Sign-in risks can include:

| Risk | Description  |
|---|---|
| Unfamiliar sign-in properties | Identity Protection remembers and learns a particular user's sign-in history. For example, when a sign-in occurs from a location that's unusual for the user, a risk detection is triggered.  |
| Atypical travel | For example, when two or more sign-ins occur from distant locations in an unrealistically short time period, a risk detection is raised.  |
| Malware-linked IP address | For example, if the IP address where the sign-in originates is known to have been in contact with an active bot server, a risk detection is raised.  |
| Anonymous IP address | For example, a sign-in originates from an anonymous IP address. Because these details can be used by attackers to hide their real IP address or location, a risk detection is raised. |


## Azure Active Directory Identity Protection workflow

There are two different ways to detect and handle identity risks: self-remediation workflow and administrator remediation workflow.

-   **Self-remediation workflow**
    
    Identity Protection uses risk policies to automatically respond to detected threats for you. You can configure a risk policy to decide how you want Identity Protection to respond to a particular type of risk. You'll then choose the action the user is asked to complete. The action could be a self-service password reset or multifactor authentication enforcement. Using policies in this way helps save time and gives you peace of mind.
    
    ![Diagram of automated remediation.](https://learn.microsoft.com/en-us/training/modules/protect-identities-with-aad-idp/media/2-identity-protection-flow.svg)
    
    In this workflow, the administrator first configures the risk policies that then monitor for identity risks. When a risk is detected, the policies enforce measures to remediate it. A policy might, for example, prompt a user to reset their password in response to a risk detected. The user then resets their password, and the risk is remediated.
    
-   **Administrator remediation workflow**
    
    You can also have admins decide how a risk should be remediated when it's been detected by your risk policies. This type of remediation workflow helps you make more tailored decisions. The admin understands the context in which the risks were detected.
    
    ![Diagram of admin remediation.](https://learn.microsoft.com/en-us/training/modules/protect-identities-with-aad-idp/media/2-admin-remediation.svg)
    
    In this workflow, the admin configures risk policies. The policies then monitor for identity risks. The admin is notified of risks in a report. The admin views the detailed report and takes appropriate action to remediate the risks. For example, the admin might decide a sign-in is safe, and accept the risk.

## Check your knowledge

1. How do you protect against identity-based risks by using Azure AD Identity Protection?
Configure an investigation policy and then remediate.
Configure a report, remediate, and then configure a policy.
[X] Configure a policy, investigate by using a report, and remediate.
	Correct. Use your risk policy to help you investigate and remediate threats.

2. You want to analyze risks that describe authentication requests for sign-ins that probably weren't authorized by users. Which type of risks will you analyze?
User risk
[X] Sign-in risk
	Correct. Azure AD Identity Protection scrutinizes each authentication request to judge whether it was authorized by the owner of the identity.
Authentication risk


# Detect risks with Azure AD Identity Protection policies

Risk policies make it possible for your organization to respond more appropriately to identity risk.

Previously, your retail company's IT team didn't have security skills in-house and had to hire external contractors to protect identities. Your manager wants to avoid the same situation going forward. Your company needs to be able to respond to threats in a controlled and more cost-effective manner without weakening security.

You've been asked to investigate how identity risks are detected in Azure AD Identity Protection. You've been asked to look into risk policies and how to use them.

In this unit, you'll investigate what risk policies are. You'll also learn what each type of risk policy is used for, and how to configure and enable them. Then, you'll see what the user experience is like for each risk policy type.

## What is a risk policy?

You can configure a risk policy to decide how you want Identity Protection to respond to a particular type of risk. Do you want to block or allow access? Do you want to make users go through additional authentication before you allow access? Risk policies help you respond to risks rapidly. Your company can leverage risk policies, and avoid hiring external contractors to handle identity-based risks.

Different risk policies are available based on the type of identity risk. You can use a sign-in risk policy or a user risk policy.

## Sign-in risk policy

A sign-in risk policy scrutinizes every sign-in and gives it a risk score. This score indicates the probability that the sign-in was attempted by the person whose credentials are used. You can decide which level of risk is acceptable by choosing a threshold of low, medium, or high. Based on the risk level, you'll choose whether to allow access, automatically block, or allow access only after additional requirements are met. For example, users might be asked to go through multifactor authentication to remediate detected risks that are considered to be at the medium level. Users could be blocked entirely if the risk is considered high.

You'll use a form to configure a sign-in risk policy in the Azure portal. You can specify settings such as:

-   The users this policy should target
-   The conditions that must be met, such as how high a score triggers the policy
-   How you want to respond

Make sure users are already registered for Azure AD Multi-Factor Authentication before you apply this policy.

![Screenshot of a sign-in risk policy.](https://learn.microsoft.com/en-us/training/modules/protect-identities-with-aad-idp/media/3-signin-risk-policy.png)

After a sign-in risk is identified, the user is asked to take action to remediate the risk. They're told what triggered the risk and what they need to provide to resolve the issue. For example, the user might see this notification:

![Screenshot of a sign-in risk user notification.](https://learn.microsoft.com/en-us/training/modules/protect-identities-with-aad-idp/media/3-signin-risk-identified.png)

## User risk policy

Here, Identity Protection learns the user's normal behavioral patterns. Identity Protection then uses this knowledge to calculate the likely risk that the user's identity was compromised. Based on this risk, the admin can decide whether to allow access, block it, or allow access only after additional requirements are met. The user could, for example, be asked to change their password by using self-service password reset before they're allowed access.

You'll use a form to configure a user risk policy in the Azure portal. You can specify settings such as the users this policy should target, the conditions that must be met, and how you'll respond. Make sure users are already registered for self-service password reset before you apply this policy.

![Screenshot of a user risk policy.](https://learn.microsoft.com/en-us/training/modules/protect-identities-with-aad-idp/media/3-user-risk-policy.png)

After a user risk is identified, the user is asked to take action to remediate that risk. They're told what triggered the risk and what they need to provide to resolve the issue. For example, the user might see this notification:

![Screenshot of a user risk notification.](https://learn.microsoft.com/en-us/training/modules/protect-identities-with-aad-idp/media/3-user-risk-identified.png)

## Multifactor authentication (MFA) registration policy

Multifactor authentication (MFA) adds a second layer of protection to your users' identities. With multifactor authentication, the user has to go through an additional verification step after they successfully provide their username and password.

You can use an MFA registration policy to make sure all users are registered for MFA from the first time they use their account. You also configure this policy so you can enforce sign-in risk policies. This way, you let users self-remediate after a sign-in risk is detected.

You'll fill in a form to configure an MFA registration policy by using the Azure portal. You'll need to provide details about which users the policy targets, and whether it should be enabled or disabled.

![Screenshot of an MFA registration policy.](https://learn.microsoft.com/en-us/training/modules/protect-identities-with-aad-idp/media/3-mfa-registration-policy.png)

After you configure an MFA registration policy, the user is asked to register when they sign in. The user sees this notification.

![Screenshot of an MFA registration notification.](https://learn.microsoft.com/en-us/training/modules/protect-identities-with-aad-idp/media/3-identity-protection-experience-more-info-mfa.png)

Users must complete the registration within 14 days, but they can choose to skip signing in during that period. After 14 days, they'll have to complete registration before they're allowed to sign in again.

# Investigate and remediate risks detected by Azure AD Identity Protection

Investigations help you understand how you can improve your identity security posture, make it possible for you to respond to risks better, and help you avoid risks in the future.

In your retail company, you've configured Azure AD Identity Protection policies and risks are being detected. Your manager has asked you to investigate and remediate all the risks detected and share a report with the project manager. The team will use it to understand the company's identity-based risks better.

In this unit, you'll learn how to investigate risks by using reports. You'll see how to remediate different types of risks and deal with any user accounts that might be blocked.

## Investigate risks

Identity Protection provides reports you can use to investigate identity-based risks detected for your organization's users. These reports come in different types. Each kind of report gives the admin information about certain risks. The admin can then take specific actions to address those risks.

| Report | Information included | Actions the admin can take | Period covered  |
|---|---|---|---|
| Risky sign-ins | Location details, device details, sign-ins confirmed as safe, or with dismissed or remediated risks. | Confirm that sign-ins are safe or confirm that they're compromised. | Last 30 days  |
| Risky users | Lists of users at risk and users with dismissed or remediated risks. User history of risky sign-ins. | Reset user passwords, dismiss user risk, block user sign-ins, and confirm user accounts as compromised. | Not applicable |

You can use these reports to investigate risks detected by Identity Protection. The reports help you understand how to better prevent risks and improve your security stance for identities.

You can also access _risk detection type reports_, which combine information about risky user detections and sign-in detections. Use these reports to see how different risk types are related and take appropriate action.

You can view and download all reports from the Azure portal.

![Screenshot of a risky sign-ins report in the Azure portal.](https://learn.microsoft.com/en-us/training/modules/protect-identities-with-aad-idp/media/5-identity-protection-risky-sign-ins-report.png)

## Remediate risks

When your investigation is complete, you'll want to remediate the risks if you're not already using risk policies to automatically deal with them. Always address detected risks quickly.

There are different ways to remediate risks. The methods you use depend on your organization's needs.

| Remediation method | Description  |
|---|---|
| Self-remediation | If you configure risk policies, you can let users self-remediate. When Identity Protection has detected a risk, users either reset their password or go through multifactor authentication to unblock themselves. After self-remediation, these detected risks are considered closed. In your risk policies, the lower the acceptable risk level that triggers the policy, the more users will be affected. In general, we recommend that you set the threshold for user risk policies at high, and set sign-in risk policies to medium and above.  |
| Reset passwords manually | For some organizations, automated password reset might not be an option. In this case, the admin can manually enforce password resets. For example, the admin can generate a temporary password and advise the user. The user can then change their password.  |
| Dismiss user risk detections | Sometimes, password reset isn't possible. For example, perhaps the affected user account was deleted. In this case, you can dismiss the risk detections for this user. If you choose to dismiss user risk detections, all associated risk detections for the user are closed.  |
| Close individual detections | All detected risks contribute to an overall risk score for a user. This risk score represents the probability that a user account is compromised. The admin can also choose to close individual risk detections and lower the overall risk of a user's account. For example, the admin can determine from a user that a particular risk detection is no longer needed and dismiss it. The overall risk that a user account was compromised is lowered. |

### Unblock users

User accounts can be blocked by risk policies or manually by the admin after an investigation. How these user accounts are unblocked depends on the type of risk that caused the blockage:

-   **Accounts blocked because of sign-in risk**
    
    An account blocked because of sign-in risk can be unblocked by excluding the user from the policy. The account might be unblocked if the admin asks the user to sign in from a familiar location or device. Sometimes, sign-ins are blocked from unfamiliar locations or devices. There might be an alert for suspicious behavior based on what's known about the user account's sign-in patterns. The policy can also be disabled if the admin found issues with it.
    
-   **Accounts blocked because of user risk**
    
    An account might be blocked if the user was flagged because of possible risky behavior. The admin can reset the password for the user to unblock the account. To remove the block, the admin might dismiss the activity identified as risky or exclude the user from the policy. If the policy is causing problems for many users, the admin can completely disable the policy.
    
## Check your knowledge

1. Which report would you review to find devices that were identified as part of a detected risk?
[X] Risky sign-in report
	Correct. Information like device details and location details is included in risky sign-in reports.
Risky user report
Risky registration report

2. You want to use a risky sign-in report to find information on risky sign-ins for the past 29 days. How can you access this report?
[X] You can access and download the report from the Azure portal.
	Correct. The report data is retained for 30 days.
You can't access the report from the portal because the data isn't retained any longer.
You can't access the report from the portal, but only if you downloaded it in the first 30 days.

# Summary

You were asked to prevent your company's identities from being compromised again and ensure that identities are protected in the future. This is a common problem for retail companies such as yours, which must guard their reputation for trustworthiness and conform with data protection legislation.

You used Azure Active Directory Identity Protection to protect your organization's identities by detecting, investigating, and remediating risks.

Without Identity Protection, your organization's identities wouldn't be protected and could have been compromised again. Your company can now use Identity Protection to protect its identities and help prevent negative reputation and financial loss.

## Learn more

To learn more about Azure Active Directory Identity Protection, see these articles:

-   [What is Azure Active Directory Identity Protection?](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection)
-   [Azure Active Directory Identity Protection - Security overview](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/concept-identity-protection-security-overview)
-   [What is risk?](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/concept-identity-protection-risks)

