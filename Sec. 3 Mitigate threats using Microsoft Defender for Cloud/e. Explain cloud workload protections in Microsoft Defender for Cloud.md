https://learn.microsoft.com/en-us/training/modules/understand-azure-defender-cloud-workload-protection/

# Introduction

Microsoft Defender for Cloud brings advanced intelligent protection for your Azure and hybrid resources and workloads. Enabling Defender for Cloud provides a range of extra security features.

You're the security operations team member working with the application and infrastructure teams designing the resource architecture for the new web application that uses containers and Azure SQL. You're responsible for ensuring the workloads are protected with Microsoft Defender for Cloud and provide options for non-protected workloads.

Learn about the protections and detections provided by Microsoft Defender for Cloud for each cloud workload.

# Understand Microsoft Defender for servers

Microsoft Defender for Servers provides threat detection and advanced defenses to your Windows and Linux machines whether they're running in Azure, AWS, GCP, or on-premises. To protect machines in hybrid and multicloud environments, Defender for Cloud uses Azure Arc.

Microsoft Defender for Servers is available in two plans:

-   **Microsoft Defender for Servers Plan 1** - deploys Microsoft Defender for Endpoint to your servers and provides these capabilities:
    
    -   Microsoft Defender for Endpoint licenses are charged per hour instead of per seat, lowering costs for protecting virtual machines only when they are in use.
    -   Microsoft Defender for Endpoint deploys automatically to all cloud workloads so that you know they're protected when they spin up.
    -   Alerts and vulnerability data from Microsoft Defender for Endpoint is shown in Microsoft Defender for Cloud
-   **Microsoft Defender for Servers Plan 2** (formerly Defender for Servers) - includes the benefits of Plan 1 and support for all of the other Microsoft Defender for Servers features.
    

To enable the Microsoft Defender for Servers plans:

Go to Environment settings and select your subscription.

If Microsoft Defender for Servers isn't enabled, set it to On. Plan 2 is selected by default.

If you want to change the Defender for Servers plan:

In the Plan/Pricing column, select Change plan. Select the plan that you want and select Confirm.

## Plan features

The following table describes what's included in each plan at a high level.

| Feature | Defender for Servers Plan 1 | Defender for Servers Plan 2  |
|---|---|---|
| Automatic onboarding for resources in Azure, AWS, GCP | Yes | Yes  |
| Microsoft threat and vulnerability management | Yes | Yes  |
| Flexibility to use Microsoft Defender for Cloud or Microsoft 365 Defender portal | Yes | Yes  |
| Integration of Microsoft Defender for Cloud and Microsoft Defender for Endpoint (alerts, software inventory, Vulnerability Assessment) | Yes | Yes  |
| Log-analytics (500 MB free) |  | Yes  |
| Vulnerability Assessment using Qualys |  | Yes  |
| Threat detections: OS level, network layer, control plane |  | Yes  |
| Adaptive application controls |  | Yes  |
| File integrity monitoring |  | Yes  |
| Just-in time VM access |  | Yes  |
| Adaptive network hardening |  | Yes |

## What are the benefits of Defender for Servers?

The threat detection and protection capabilities provided with Microsoft Defender for Servers include:

-   **Integrated license for Microsoft Defender for Endpoint** - Microsoft Defender for Servers includes Microsoft Defender for Endpoint. Together, they provide comprehensive endpoint detection and response (EDR) capabilities. When you enable Microsoft Defender for Servers, Defender for Cloud gets access to the Microsoft Defender for Endpoint data that is related to vulnerabilities, installed software, and alerts for your endpoints.
    
    When Defender for Endpoint detects a threat, it triggers an alert. The alert is shown in Defender for Cloud. From Defender for Cloud, you can also pivot to the Defender for Endpoint console, and perform a detailed investigation to uncover the scope of the attack.
    
-   **Vulnerability assessment tools for machines** - Microsoft Defender for Servers includes a choice of vulnerability discovery and management tools for your machines. From Defender for Cloud's settings pages, you can select the tools to deploy to your machines. The discovered vulnerabilities are shown in a security recommendation.
    
-   **Microsoft threat and vulnerability management** - Discover vulnerabilities and misconfigurations in real time with Microsoft Defender for Endpoint, and without the need of other agents or periodic scans. Threat and vulnerability management prioritizes vulnerabilities according to the threat landscape, detections in your organization, sensitive information on vulnerable devices, and the business context.
    
-   **Vulnerability scanner powered by Qualys** - The Qualys scanner is one of the leading tools for real-time identification of vulnerabilities in your Azure and hybrid virtual machines. You don't need a Qualys license or even a Qualys account - everything's handled seamlessly inside Defender for Cloud.
    
-   **Just-in-time (JIT) virtual machine (VM) access** - Threat actors actively hunt accessible machines with open management ports, like RDP or SSH. All of your virtual machines are potential targets for an attack. When a VM is successfully compromised, it's used as the entry point to attack further resources within your environment.
    
    When you enable Microsoft Defender for Servers, you can use just-in-time VM access to lock down the inbound traffic to your VMs. Keeping remote access ports closed until needed reduces exposure to attacks and provides easy access to connect to VMs when needed.
    
-   **File integrity monitoring (FIM)** - File integrity monitoring (FIM), also known as change monitoring, examines files and registries of operating system, application software, and others for changes that might indicate an attack. A comparison method is used to determine if the current state of the file is different from the last scan of the file. You can use this comparison to determine if valid or suspicious modifications have been made to your files.
    
    When you enable Microsoft Defender for Servers, you can use FIM to validate the integrity of Windows files, your Windows registries, and Linux files.
    
-   **Adaptive application controls (AAC)** - Adaptive application controls are an intelligent and automated solution for defining allowlists of known-safe applications for your machines.
    
    After you enable and configure adaptive application controls, you get security alerts if any application runs other than the ones you defined as safe.
    
-   **Adaptive network hardening (ANH)** - Applying network security groups (NSG) to filter traffic to and from resources, improves your network security posture. However, there can still be some cases in which the actual traffic flowing through the NSG is a subset of the NSG rules defined. In these cases, further improving the security posture can be achieved by hardening the NSG rules, based on the actual traffic patterns.
    
    Adaptive network hardening provides recommendations to further harden the NSG rules. It uses a machine learning algorithm that factors in actual traffic, known trusted configuration, threat intelligence, and other indicators of compromise. ANH then provides recommendations to allow traffic only from specific IP and port tuples.
    
-   **Docker host hardening** - Microsoft Defender for Cloud identifies unmanaged containers hosted on IaaS Linux VMs, or other Linux machines running Docker containers. Defender for Cloud continuously assesses the configurations of these containers. It then compares them with the Center for Internet Security (CIS) Docker Benchmark. Defender for Cloud includes the entire ruleset of the CIS Docker Benchmark and alerts you if your containers don't satisfy any of the controls.
    
-   **Fileless attack detection** - Fileless attacks inject malicious payloads into memory to avoid detection by disk-based scanning techniques. The attacker’s payload then persists within the memory of compromised processes and performs a wide range of malicious activities.
    
    With fileless attack detection, automated memory forensic techniques identify fileless attack toolkits, techniques, and behaviors. This solution periodically scans your machine at runtime, and extracts insights directly from the memory of processes. Specific insights include the identification of:
    
    -   Well-known toolkits and crypto mining software
    -   Shellcode - a small piece of code typically used as the payload in the exploitation of a software vulnerability.
    -   Injected malicious executable in process memory
    
    Fileless attack detection generates detailed security alerts that include descriptions with process metadata such as network activity. These details accelerate alert triage, correlation, and downstream response time. This approach complements event-based EDR solutions, and provides increased detection coverage.
    
-   **Linux auditd alerts and Log Analytics agent integration (Linux only)** - The auditd system consists of a kernel-level subsystem, which is responsible for monitoring system calls. It filters them by a specified rule set, and writes messages for them to a socket. Defender for Cloud integrates functionalities from the auditd package within the Log Analytics agent. This integration enables collection of auditd events in all supported Linux distributions, without any prerequisites.
    
    Log Analytics agent for Linux collects auditd records and enriches and aggregates them into events. Defender for Cloud continuously adds new analytics that use Linux signals to detect malicious behaviors on cloud and on-premises Linux machines. Similar to Windows capabilities, these analytics include tests that check for suspicious processes, dubious sign-in attempts, kernel module loading, and other activities. These activities can indicate a machine is either under attack or has been breached.
    

## How does Defender for Servers collect data?

For Windows, Microsoft Defender for Cloud integrates with Azure services to monitor and protect your Windows-based machines. Defender for Cloud presents the alerts and remediation suggestions from all of these services in an easy-to-use format.

For Linux, Defender for Cloud collects audit records from Linux machines by using auditd, one of the most common Linux auditing frameworks.

For hybrid and multicloud scenarios, Defender for Cloud integrates with Azure Arc to ensure these non-Azure machines are seen as Azure resources.

# Understand Microsoft Defender for App Service

Azure App Service is a fully managed platform for building and hosting your web apps and APIs without worrying about having to manage the infrastructure. It provides management, monitoring, and operational insights to meet enterprise-grade performance, security, and compliance requirements. For more information, see [Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/overview).

Microsoft Defender for App Service uses the scale of the cloud to identify attacks targeting applications running over App Service. Attackers probe web applications to find and exploit weaknesses. Before being routed to specific environments, requests to applications running in Azure go through several gateways, where they're inspected and logged. This data is then used to identify exploits and attackers and learn new patterns that will be used later.

By using the visibility that Azure has as a cloud provider, Defender for Cloud analyzes App Service internal logs to identify attack methodology on multiple targets. For example, methodology includes widespread scanning and distributed attacks. This type of attack typically comes from a small subset of IPs and shows patterns of crawling to similar endpoints on multiple hosts. The attacks are searching for a vulnerable page or plugin and can't be identified from the standpoint of a single host.

## What does Microsoft Defender for App Service protect?

With the App Service plan enabled, Defender for Cloud assesses the resources covered by your App Service plan and generates security recommendations based on its findings. Defender for Cloud protects the VM instance in which your App Service is running and the management interface. It also monitors requests and responses sent to and from your apps running in App Service.

If you're running a Windows-based App Service plan, Defender for Cloud also has access to the underlying sandboxes and VMs. Together with the log data mentioned above, the infrastructure can tell the story, from a new attack circulating in the wild to compromises in customer machines. Therefore, even if Defender for Cloud is deployed after a web app has been exploited, it might be able to detect ongoing attacks.

## Protect your Azure App Service web apps and APIs

To protect your Azure App Service plan with Microsoft Defender for App Service:

-   Ensure you have a supported App Service plan that is associated with dedicated machines. Supported plans are listed [here](https://learn.microsoft.com/en-us/azure/app-service/overview-hosting-plans).
    
-   Enable Defender for Cloud on your subscription (you can optionally enable only the Defender for App Service plan).
    

Defender for Cloud is natively integrated with App Service, eliminating the need for deployment and onboarding - the integration is transparent.

# Understand Microsoft Defender for Storage

Microsoft Defender for Storage is an Azure-native layer of security intelligence that detects unusual and potentially harmful attempts to access or exploit your storage accounts. It utilizes the advanced capabilities of security AI and Microsoft Threat Intelligence to provide contextual security alerts and recommendations.

Security alerts are triggered when anomalies in activity occur. The Security alerts are integrated with Defender for Cloud and sent via email to subscription administrators with details of suspicious activity and recommendations on how to investigate and remediate threats.

## What are the benefits of Microsoft Defender for Storage?

Microsoft Defender for Storage provides:

-   **Azure-native security** - With one-click enablement, Defender for Storage protects data stored in Azure Blob, Azure Files, and Data Lakes. As an Azure-native service, Defender for Storage provides centralized security across all data assets managed by Azure and is integrated with other security services such as Microsoft Sentinel.
    
-   **Rich detection suite** - Powered by Microsoft Threat Intelligence, the detections in Defender for Storage cover the top storage threats such as anonymous access, compromised credentials, social engineering, privilege abuse, and malicious content.
    
-   **Response at scale** - Defender for Cloud's automation tools make it easier to prevent and respond to identified threats. Learn more in Automate responses to Defender for Cloud triggers.
    

![Screenshot of Microsoft Defender for Storage threat response.](https://learn.microsoft.com/en-us/training/wwl-sci/understand-azure-defender-cloud-workload-protection/media/defender-for-storage-overview.png)

## What kind of alerts does Microsoft Defender for Storage provide?

Security alerts are triggered when there's:

-   **Suspicious access patterns** - such as successful access from a Tor exit node or from an IP considered suspicious by Microsoft Threat Intelligence
    
-   **Suspicious activities** - such as anomalous data extraction or unusual change of access permissions
    
-   **Uploads of malicious content** - such as potential malware files (based on hash reputation analysis) or hosting of phishing content
    

Alerts include details of the incident that triggered them, and recommendations on how to investigate and remediate threats. Alerts can be exported to Azure Sentinel or any other third-party SIEM or any other external tool.

## What is hash reputation analysis for malware?

To determine whether an uploaded file is suspicious, Defender for Storage uses hash reputation analysis supported by Microsoft Threat Intelligence. The threat protection tools don’t scan the uploaded files. Rather they examine the storage logs and compare the hashes of newly uploaded files with the hashes of known viruses, trojans, spyware, and ransomware.

When a file is suspected of containing malware, Security Center displays an alert and can optionally email the storage owner for approval to delete the suspicious file. To set up this automatic removal of files containing malware indicated by hash reputation analysis, deploy a workflow automation to trigger on alerts containing "Potential malware uploaded to a storage account”.

# Understand Microsoft Defender for SQL

Microsoft Defender for Cloud database security, allows you to protect your entire database estate, by detecting common attacks, supporting enablement, and threat response for the most popular database types in Azure.

The types of protected databases are:

-   Azure SQL Databases
-   SQL servers on machines
-   Open-source relational databases (OSS RDB)
-   Azure Cosmos DB Database provides protection to engines, and data types, with different attack surface, and security risks. Security detections are made for the specific attack surface of each DB type.

Defender for Cloud’s database protection detects unusual and potentially harmful attempts to access, or exploit your databases. Advanced threat detection capabilities and Microsoft Threat Intelligence data are used to provide contextual security alerts. Those alerts include steps to mitigate the detected threats, and prevent future attacks.

You can enable database protection on your subscription, or exclude specific database resource types.

Microsoft Defender for SQL includes two plans that extend Defender for Cloud's data security package to secure your databases and their data wherever they're located.

## What does Microsoft Defender SQL protect?

Microsoft Defender for SQL comprises two separate Microsoft Defender plans:

-   **Defender for Azure SQL database servers** protects:
    
    -   Azure SQL Database
        
    -   Azure SQL Managed Instance
        
    -   Dedicated SQL pool in Azure Synapse
        
-   **Microsoft Defender for SQL servers on machines** extends the protections for your Azure-native SQL Servers to fully support hybrid environments and protect SQL servers (all supported version) hosted in Azure, other cloud environments, and even on-premises machines:
    
    -   SQL Server on Virtual Machines
        
    -   On-premises SQL servers:
        
        -   Azure Arc enabled SQL Server (preview)
            
        -   SQL Server running on Windows machines without Azure Arc
            

## What are the benefits of Microsoft Defender for SQL?

These two plans include functionality for identifying and mitigating potential database vulnerabilities and detecting anomalous activities that could indicate threats to your databases:

-   Vulnerability assessment - The scanning service to discover, track, and help you remediate potential database vulnerabilities. Assessment scans provide an overview of your SQL machines' security state and details of any security findings.
    
-   Advanced threat protection - The detection service that continuously monitors your SQL servers for threats such as SQL injection, brute-force attacks, and privilege abuse. This service provides action-oriented security alerts in Defender for Cloud with details of the suspicious activity, guidance on how to mitigate the threats and options for continuing your investigations with Microsoft Sentinel.
    

### What kind of alerts does Defender for SQL provide?

Threat intelligence enriched security alerts are triggered when there's:

-   **Potential SQL injection attacks** - including vulnerabilities detected when applications generate a faulty SQL statement in the database
    
-   **Anomalous database access and query patterns** - for example, an abnormally high number of failed sign-in attempts with different credentials (a brute force attempt)
    
-   **Suspicious database activity** - for example, a legitimate user accessing a SQL Server from a breached computer that communicated with a crypto-mining C&C server
    

Alerts include details of the incident that triggered them, and recommendations on how to investigate and remediate threats.

## What are the benefits of Microsoft Defender for open-source relational databases

This Defender for Cloud plan brings threat protections for the following open-source relational databases:

-   Azure Database for PostgreSQL
-   Azure Database for MySQL
-   Azure Database for MariaDB

When you enable this plan, Microsoft Defender for Cloud will provide alerts when it detects anomalous database access and query patterns and suspicious database activities.

![Screenshot of the alert screen with open-source database alerts.](https://learn.microsoft.com/en-us/training/wwl-sci/understand-azure-defender-cloud-workload-protection/media/defender-alerts.png)

### Microsoft Defender alerts for open-source relational databases

Threat intelligence enriched security alerts are triggered when there are:

-   **Anomalous database access and query patterns** For example, an abnormally high number of failed sign-in attempts with different credentials (a brute force attempt)
-   **Suspicious database activities** For example, a legitimate user accessing an SQL Server from a breached computer that communicated with a crypto-mining C&C server
-   **Brute-force attacks** With the ability to separate simple brute force from brute force on a valid user or a successful brute force.

## What are the benefits of Microsoft Defender for Azure Cosmos DB

Microsoft Defender for Azure Cosmos DB detects potential SQL injections, known bad actors based on Microsoft Threat Intelligence, suspicious access patterns, and potential exploitation of your database through compromised identities, or malicious insiders.

You can enable protection for all your databases (recommended), or enable Microsoft Defender for Azure Cosmos DB at either the subscription level, or the resource level.

Defender for Azure Cosmos DB continually analyzes the telemetry stream generated by the Azure Cosmos DB service. When potentially malicious activities are detected, security alerts are generated. These alerts are displayed in Defender for Cloud together with the details of the suspicious activity along with the relevant investigation steps, remediation actions, and security recommendations.

Defender for Azure Cosmos DB doesn't access the Azure Cosmos DB account data, and doesn't have any effect on its performance.

### Microsoft Defender alerts for Microsoft Defender for Azure Cosmos DB

Threat intelligence enriched security alerts are triggered when there are:

-   **Potential SQL injection attacks:** Due to the structure and capabilities of Azure Cosmos DB queries, many known SQL injection attacks can’t work in Azure Cosmos DB. However, there are some variations of SQL injections that can succeed and may result in exfiltrating data from your Azure Cosmos DB accounts. Defender for Azure Cosmos DB detects both successful and failed attempts, and helps you harden your environment to prevent these threats.
    
-   **Anomalous database access patterns:** For example, access from a TOR exit node, known suspicious IP addresses, unusual applications, and unusual locations.
    
-   **Suspicious database activity:** For example, suspicious key-listing patterns that resemble known malicious lateral movement techniques and suspicious data extraction patterns.

# Understand Microsoft Defender for open-source databases

Microsoft Defender for Cloud detects anomalous activities indicating unusual and potentially harmful attempts to access or exploit databases. The plan makes it simple to address potential threats to databases without the need to be a security expert or manage advanced security monitoring systems.

This Defender for Cloud plan brings threat protections for the following open-source relational databases:

-   Azure Database for PostgreSQL
-   Azure Database for MySQL
-   Azure Database for MariaDB

When you enable this plan, Microsoft Defender for Cloud will provide alerts when it detects anomalous database access and query patterns and suspicious database activities.

![Screenshot of alert screen with open-source database alerts.](https://learn.microsoft.com/en-us/training/wwl-sci/understand-azure-defender-cloud-workload-protection/media/defender-alerts.png)

### Microsoft Defender alerts for open-source relational databases

Threat intelligence enriched security alerts are triggered when there are:

-   **Anomalous database access and query patterns** For example, an abnormally high number of failed sign-in attempts with different credentials (a brute force attempt)
-   **Suspicious database activities** For example, a legitimate user accessing an SQL Server from a breached computer that communicated with a crypto-mining C&C server
-   **Brute-force attacks** With the ability to separate simple brute force from brute force on a valid user or a successful brute force.

# Understand Microsoft Defender for Key Vault

Azure Key Vault is a cloud service that safeguards encryption keys and secrets like certificates, connection strings, and passwords.

Enable Microsoft Defender for Key Vault for Azure-native, advanced threat protection for Azure Key Vault, providing an extra layer of security intelligence.

## What are the benefits of Microsoft Defender for Key Vault?

Microsoft Defender for Cloud detects unusual and potentially harmful attempts to access or exploit Key Vault accounts. This layer of protection allows you to address threats without being a security expert and without the need to manage third-party security monitoring systems.

When anomalous activities occur, Defender for Cloud shows alerts and optionally sends them via email to relevant members of your organization. These alerts include the details of the suspicious activity and recommendations on how to investigate and remediate threats.

## Microsoft Defender for Key Vault alerts

When you get an alert from Defender for Key Vault, we recommend investigating and responding to the alert as described in Respond to Defender for Key Vault. Defender for Key Vault protects applications and credentials. So even if you're familiar with the application or user that triggered the alert, it's important to check the situation surrounding every alert.

The alerts appear on Key Vault's Security page, the Defender for Cloud dashboard.

# Understand Microsoft Defender for Resource Manager

Azure Resource Manager is the deployment and management service for Azure. It provides a management layer that enables you to create, update, and delete resources in your Azure account. You use management features, like access control, locks, and tags, to secure and organize your resources after deployment.

The cloud management layer is a crucial service connected to all your cloud resources. Because of this integration, it's also a potential target for attackers. So, we recommend security operations teams monitor the resource management layer closely.

Microsoft Defender for Resource Manager automatically monitors the resource management operations in your organization. Whether they're performed through the Azure portal, Azure REST APIs, Azure CLI, or other Azure programmatic clients Defender for Cloud runs advanced security analytics to detect threats and alert you about suspicious activity.

## What are the benefits of Microsoft Defender for Resource Manager?

Defender for Resource Manager protects against issues including:

-   **Suspicious resource management operations**, such as operations from suspicious IP addresses, disabling antimalware and suspicious scripts running in VM extensions
    
-   **Use of exploitation toolkits** like Microburst or PowerZure
    
-   **Lateral movement** from the Azure management layer to the Azure resources data plane
    

## How to investigate alerts from Microsoft Defender for Resource Manager

Security alerts from Defender for Resource Manager are based on threats detected by monitoring Azure Resource Manager operations. Defender for Cloud uses internal log sources of Azure Resource Manager and Azure Activity log, a platform sign-in Azure that provides insight into subscription-level events.

To investigate security alerts from Defender for Resource Manager:

1.  Open Azure Activity log.
    
2.  Filter the events to:
    
    -   The subscription mentioned in the alert
        
    -   The timeframe of the detected activity
        
    -   The related user account (if relevant)
        
3.  Look for suspicious activities.

# Understand Microsoft Defender for DNS

Azure DNS is a hosting service for DNS domains that provides name resolution by using Microsoft Azure infrastructure. By hosting your domains in Azure, you can manage your DNS records by using the same credentials, APIs, tools, and billing as your other Azure services.

Microsoft Defender for DNS provides an extra layer of protection for your cloud resources by:

-   Continuously monitoring all DNS queries from your Azure resources
    
-   Running advanced security analytics to alert you about suspicious activity
    

## What are the benefits of Microsoft Defender for DNS?

Defender for DNS protects against issues including:

-   Data exfiltration from your Azure resources using DNS tunneling
    
-   Malware communicating with C&C server
    
-   Communication with malicious domains as phishing and crypto mining
    
-   DNS attacks - communication with malicious DNS resolvers

# Understand Microsoft Defender for Containers

Microsoft Defender for Containers is the cloud-native solution for securing your containers.

## Defender for Containers features

-   **Environment hardening** - Defender for Containers protects your Kubernetes clusters whether they're running on Azure Kubernetes Service, Kubernetes on-premises / IaaS, or Amazon EKS. By continuously assessing clusters, Defender for Containers provides visibility into misconfigurations and guidelines to help mitigate identified threats.
    
-   **Vulnerability assessment** - Vulnerability assessment and management tools for images stored in ACR registries and running in Azure Kubernetes Service.
    
-   **Run-time threat protection for nodes and clusters** - Threat protection for clusters and Linux nodes generates security alerts for suspicious activities.
    

## Architecture

The architecture of the elements needed for the full range of protections provided by Defender for Containers, varies depending on where your Kubernetes clusters are hosted.

Defender for Containers protects your clusters whether they're running in:

-   **Azure Kubernetes Service (AKS)** - Microsoft's managed service for developing, deploying, and managing containerized applications.
    
-   **Amazon Elastic Kubernetes Service (EKS)** in a connected Amazon Web Services (AWS) account - Amazon's managed service for running Kubernetes on AWS without needing to install, operate, and maintain your own Kubernetes control plane or nodes.
    
-   **An unmanaged Kubernetes distribution (using Azure Arc-enabled Kubernetes)** - Cloud Native Computing Foundation (CNCF) certified Kubernetes clusters hosted on-premises or on IaaS.
    

Defender for Cloud continuously assesses the configurations of your clusters and compares them with the initiatives applied to your subscriptions. When it finds misconfigurations, Defender for Cloud generates security recommendations. Use Defender for Cloud's recommendations page to view recommendations and remediate issues.

For Kubernetes clusters on EKS, you'll need to connect your AWS account to Microsoft Defender for Cloud via the environment settings page (as described in Connect your AWS accounts to Microsoft Defender for Cloud). Then ensure you've enabled the CSPM plan.

### Environment hardening

To receive a bundle of recommendations to protect the workloads of your Kubernetes containers, install the Azure Policy for Kubernetes. By default, auto provisioning is enabled when you enable Defender for Containers.

With the add-on on your AKS cluster, every request to the Kubernetes API server will be monitored against the predefined set of best practices before being persisted to the cluster. You can then configure to enforce the best practices and mandate them for future workloads.

For example, you can mandate that privileged containers shouldn't be created, and any future requests to do so will be blocked.

### View vulnerabilities for running images

Defender for Containers expands on the registry scanning features of the Defender for container registries plan by introducing the preview feature of run-time visibility of vulnerabilities powered by the Defender profile, or an extension.

The new recommendation, "running container images should have vulnerability findings resolved", only shows vulnerabilities for running images. The recommendation relies on the Defender security profile, or extension to discover which images are currently running. This recommendation groups running images that have vulnerabilities, and provides details about the issues discovered, and how to remediate them. The Defender profile, or extension is used to gain visibility into vulnerable containers that are active.

This recommendation shows running images, and their vulnerabilities based on ACR images. Images that are deployed from a non ACR registry, won't be scanned, and will appear under the Not applicable tab.

### Run-time protection for Kubernetes nodes and clusters

Defender for Cloud provides real-time threat protection for your containerized environments and generates alerts for suspicious activities. You can use this information to quickly remediate security issues and improve the security of your containers.

Threat protection at the cluster level is provided by the Defender profile and analysis of the Kubernetes audit logs. Examples of events at this level include exposed Kubernetes dashboards, creation of high-privileged roles, and the creation of sensitive mounts.

In addition, our threat detection goes beyond the Kubernetes management layer. Defender for Containers includes host-level threat detection with over 60 Kubernetes-aware analytics, AI, and anomaly detections based on your runtime workload. Our global team of security researchers constantly monitor the threat landscape. They add container-specific alerts and vulnerabilities as they're discovered. Together, this solution monitors the growing attack surface of multi-cloud Kubernetes deployments and tracks the MITRE ATT&CK® matrix for Containers. A framework that was developed by the Center for Threat-Informed Defense in close partnership with Microsoft and other partners.

# Understand Microsoft Defender additional protections

## Threat protection for Azure network layer

Microsoft Defender for Cloud network-layer analytics is based on sample IPFIX data, which are packet headers collected by Azure core routers. Based on this data feed, Defender for Cloud uses machine learning models to identify and flag malicious traffic activities. Defender for Cloud also uses the Microsoft Threat Intelligence database to enrich IP addresses.

Some network configurations restrict Defender for Cloud from generating alerts on suspicious network activity. For Defender for Cloud to generate network alerts, ensure that:

-   Your virtual machine has a public IP address (or is on a load balancer with a public IP address).
    
-   Your virtual machine's network egress traffic isn't blocked by an external IDS solution.
    

## Threat protection for Azure Cosmos DB (Preview)

The Azure Cosmos DB alerts are generated by unusual and potentially harmful attempts to access or exploit Azure Cosmos DB accounts.

## Display Azure WAF alerts in Microsoft Defender for Cloud

Azure Application Gateway offers a web application firewall (WAF) that provides centralized protection of your web applications from common exploits and vulnerabilities. Web applications are increasingly targeted by malicious attacks that exploit commonly known vulnerabilities. The Application Gateway WAF is based on Core Rule Set 3.0 or 2.2.9 from the Open Web Application Security Project. The WAF is updated automatically to protect against new vulnerabilities.

If you have a license for Azure WAF, your WAF alerts are streamed to Defender for Cloud with no extra configuration needed.

## Display Azure DDoS Protection alerts in Microsoft Defender for Cloud

Distributed denial of service (DDoS) attacks are known to be easy to execute. They've become a great security concern, particularly if you're moving your applications to the cloud. A DDoS attack attempts to exhaust an application's resources, making the application unavailable to legitimate users. DDoS attacks can target any endpoint that can be reached through the internet. To defend against DDoS attacks, purchase a license for Azure DDoS Protection and ensure you're following application design best practices. DDoS Protection provides different service tiers.

## Display Azure Microsoft Defender for Cloud recommendations in Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps is a Cloud Access Security Broker (CASB) that supports various deployment modes including log collection, API connectors, and reverse proxy. It provides rich visibility, control over data travel, and sophisticated analytics to identify and combat cyberthreats across all your Microsoft and third-party cloud services.

If you've enabled Microsoft Defender for Cloud Apps, and selected the integration from within Microsoft Defender for Cloud's settings, your hardening recommendations from Microsoft Defender for Cloud will appear in Defender for Cloud Apps with no extra configuration needed.

# Knowledge check

1. What is a protection provided by Microsoft Defender for DNS?

[X] Malware communicating with C&C server

Correct. Command and Control detection over DNS is detected.

Malware encrypting data on a Device

Malware enumerating user on a Device

2. Microsoft Defender for Containers does which of the following?

Environmental hardening, Vulnerability assessment, and endpoint management

Environmental hardening, User risk management, and Run-time threat protection

[X] Environmental hardening, Vulnerability assessment, and Run-time threat protection

Correct. It performs all three of these services.

3. Which feature of Microsoft Defender for Servers examines files and registries of the operating system, application software, and others for changes that might indicate an attack?

Adaptive application controls

Adaptive network hardening

[X] File integrity monitoring

Correct. File integrity monitoring examines files.

# Summary and resources

You learned how Microsoft Defender for Cloud brings advanced, intelligent protection for your Azure and hybrid resources and workloads. Enabling Microsoft Defender for Cloud brings a range of extra security features.

You should now be able to:

-   Explain which workloads are protected by Microsoft Defender for Cloud
-   Describe the benefits of the protections offered by Microsoft Defender Cloud
-   Explain how Microsoft Defender for Cloud protections function

## Learn more

You can learn more by reviewing the following.

[Become an Microsoft Defender for Cloud Ninja (microsoft.com)](https://techcommunity.microsoft.com/t5/azure-security-center/become-an-azure-security-center-ninja/ba-p/1608761)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)