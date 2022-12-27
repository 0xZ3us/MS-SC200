https://learn.microsoft.com/en-us/training/modules/connect-non-azure-machines-to-azure-defender/

# Introduction

Microsoft Defender for Cloud can protect hybrid workloads, including on-premise, Amazon Web Services (AWS), and Google Cloud Platform (GCP).

You're a Security Operations Analyst working at a company that is in the process of implementing cloud workload protection with Microsoft Defender for Cloud. You're responsible for protecting resources located on-premise, Amazon Web Services (AWS), and Google Cloud Platform (GCP). You decide to Azure Arc enable the servers to provide easier management of the non-Azure machines. Next, you protect the virtual machines with Defender for Cloud.

Learn how you can add Defender for Cloud capabilities to your hybrid environment.

# Protect non-Azure resources

Today, companies struggle to control and govern increasingly complex environments. These environments extend across data centers, multiple clouds, and edge. Each environment and cloud possesses its own set of disjointed management tools that you need to learn and operate.

In parallel, new DevOps and ITOps operational models are hard to implement, as existing tools fail to provide support for new cloud native patterns.

Azure Arc simplifies governance and management by delivering a consistent multi-cloud and on-premises management platform. Azure Arc enables you to:

-   Manage your entire environment, with a single pane of glass, by projecting your existing non-Azure, on-premises, or other-cloud resources into Azure Resource Manager.
-   Manage virtual machines, Kubernetes clusters, and databases as if they're running in Azure.
-   Use familiar Azure services and management capabilities, regardless of where they live.
-   Continue using traditional ITOps, while introducing DevOps practices to support new cloud native patterns in your environment.
-   Configure Custom Locations as an abstraction layer on top of Azure Arc-enabled Kubernetes cluster, cluster connect, and cluster extensions.

![Diagram of the Azure ARC Control Plane for resources.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-non-azure-machines-to-azure-defender/media/azure-arc-control-plane.png)

Today, Azure Arc allows you to manage the following resource types hosted outside of Azure:

-   Servers - both physical and virtual machines running Windows or Linux.
-   Kubernetes clusters - supporting multiple Kubernetes distributions.
-   Azure data services - Azure SQL Managed Instance and PostgreSQL Hyperscale services.
-   SQL Server - enroll instances from any location with SQL Server on Azure Arc-enabled servers.

# Connect non-Azure machines

Microsoft Defender for Cloud can monitor the security posture of your non-Azure computers, but first, you need to connect them to Azure.

You can connect your non-Azure computers in any of the following ways:

-   Using Azure Arc enabled servers (recommended)
    
-   From Defender for Cloud's pages in the Azure portal (Getting started and Inventory)
    

## Add non-Azure machines with Azure Arc

Azure Arc enabled servers is the preferred way of adding your non-Azure machines to Defender for Cloud. A machine with Azure Arc enabled servers becomes an Azure resource and appears in Defender for Cloud with recommendations like your other Azure resources. In addition, Azure Arc enabled servers provides enhanced capabilities such as the option to enable guest configuration policies on the machine, deploy the Log Analytics agent as an extension, simplify deployment with other Azure services, and more.

### What is Azure Arc enabled servers?

Azure Arc enabled servers allows you to manage your Windows and Linux machines hosted outside of Azure, on your corporate network, or other cloud providers, just like you manage native Azure virtual machines. When a hybrid machine is connected to Azure, it becomes a connected machine and is treated as a resource in Azure. Each connected machine has a Resource ID, is included in a resource group, and benefits from standard Azure constructs such as Azure Policy and applying tags. Service providers who manage a customer's on-premises infrastructure can manage their hybrid machines, just like they do today with native Azure resources, across multiple customer environments, using Azure Lighthouse with Azure Arc.

To deliver this experience with your hybrid machines hosted outside of Azure, the Azure Connected Machine agent needs to be installed on each machine that you plan on connecting to Azure. **This agent does not deliver any other functionality, and it doesn't replace the Azure Log Analytics agent**. The Log Analytics agent for Windows and Linux is required when you want to proactively monitor the OS and workloads running on the machine. You can then manage the machines using Automation runbooks, solutions like Update Management, or use other Azure services like Defender for Cloud.

## Add non-Azure machines from the Azure portal

You can start the process of adding a non-Azure server from two different locations in Defender for Cloud:

1.  From Defender for Cloud's menu, open the **Getting started** page.
2.  Select the **Get started** tab.
3.  Below Add non-Azure servers, select **Configure**.
4.  From Defender for Cloud's menu, open the Inventory page.
5.  Select the **+ Add non-Azure servers** button.

A list of your Log Analytics workspaces is shown. The list includes, if applicable, the default workspace created for you by Defender for Cloud when automatic provisioning was enabled. Select this workspace or another workspace you want to use.

You can add computers to an existing workspace or create a new workspace. Optionally, to create a new workspace, select **Create new workspace**.

From the list of workspaces, select **Add Servers** for the relevant workspace. The Agents management page appears.

From here, choose the relevant procedure below depending on the type of machines you're onboarding:

-   Onboard your Azure Stack VMs
    
-   Onboard your Linux machines
    
-   Onboard your Windows machines
    

### Onboard your Azure Stack VMs

To add Azure Stack VMs, you need the information on the Agents management page and to configure the Azure Monitor, Update and Configuration Management virtual machine extension on the virtual machines running on your Azure Stack.

1.  From the Agents management page, copy the Workspace ID and Primary Key into Notepad.
    
2.  Log into your Azure Stack portal and open the Virtual machines page.
    
3.  Select the virtual machine that you want to protect with Defender for Cloud.
    
4.  Select Extensions. The list of virtual machine extensions installed on this virtual machine is shown.
    
5.  Select the **Add** tab. The New Resource menu shows the list of available virtual machine extensions.
    
6.  Select the Azure Monitor, Update and Configuration Management extension and select **Create**. The Install extension configuration page opens.
    
7.  On the Install extension configuration page, paste the Workspace ID and Workspace Key (Primary Key) that you copied into Notepad in the previous step.
    
8.  When you complete the configuration, select **OK**. The extension's status will show as _Provisioning Succeeded_. It might take up to one hour for the virtual machine to appear in Defender for Cloud.
    

### Onboard your Linux machines

To add Linux machines, you need the WGET command from the Agents management page.

1.  From the Agents management page, copy the WGET command into Notepad. Save this file to a location that is accessible from your Linux computer.
    
2.  On your Linux computer, open the file with the WGET command. Select the entire content and copy and paste it into a terminal console.
    
3.  When the installation completes, you can validate that the _omsagent_ is installed by running the [pgrep] command. The command will return the omsagent PID. The logs for the Agent can be found at: /var/opt/microsoft/omsagent/workspace id/log/ It might take up to 30 minutes for the new Linux machine to appear in Defender for Cloud.
    

### Onboard your Windows machines

To add Windows machines, you need to read the information on the Agents management page and to download the appropriate agent file (32/64-bit).

1.  Select the Download Windows Agent link applicable to your computer processor type to download the setup file.
    
2.  From the Agents management page, copy the Workspace ID and Primary Key into Notepad.
    
3.  Copy the downloaded setup file to the target computer and run it.
    
4.  Follow the installation wizard (Next, I Agree, Next, Next).
    
5.  On the Azure Log Analytics page, paste the Workspace ID and Workspace Key (Primary Key) that you copied into Notepad.
    
6.  If the computer should report to a Log Analytics workspace in Azure Government cloud, select **Azure US Government** from the Azure Cloud dropdown list.
    
7.  If the computer needs to communicate through a proxy server to the Log Analytics service, select **Advanced** and provide the proxy server's URL and port number.
    
8.  When you've entered all of the configuration settings, select **Next**.
    
9.  From the Ready to Install page, review the settings to be applied and select **Install**.
    
10.  On the Configuration completed successfully page, select **Finish**.
    

When complete, the Microsoft Monitoring agent appears in Control Panel. You can review your configuration there and verify that the agent is connected.

# Connect your AWS accounts

Onboarding your AWS account into Microsoft Defender for Cloud, integrates AWS Security Hub and Defender for Cloud. Defender for Cloud thus provides visibility and protection across both of these cloud environments to provide:

-   Automatic agent provisioning (Defender for Cloud uses Azure Arc to deploy the Log Analytics agent to your AWS instances)
    
-   Policy management
    
-   Vulnerability management
    
-   Embedded Endpoint Detection and Response (EDR)
    
-   Detection of security misconfigurations
    
-   A single view showing Defender for Cloud recommendations and AWS Security Hub findings
    
-   Incorporation of your AWS resources into Defender for Cloud's secure score calculations
    
-   Regulatory compliance assessments of your AWS resources
    

In the screenshot below, you can see AWS accounts displayed in Security Center's overview dashboard.

![Screenshot of the A W S account overview settings.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-non-azure-machines-to-azure-defender/media/aws-account-overview.png)

## Follow the steps below to create your AWS cloud connector.

### Set up AWS Security Hub:

To view security recommendations for multiple regions, repeat the following steps for each relevant region. If you're using an AWS master account, repeat the following three steps to configure the master account and all connected member accounts across all relevant regions

1.  Enable AWS Config.
    
2.  Enable AWS Security Hub.
    
3.  Verify that there's data flowing to the Security Hub.
    

When you first enable Security Hub, it might take several hours for data to be available.

### Set up authentication for Security Center in AWS

There are two ways to allow Defender for Cloud to authenticate to AWS:

-   Create an IAM role for Defender for Cloud - This is the most secure method and is recommended
    
-   AWS user for Defender for Cloud - A less secure option if you don't have IAM enabled
    

Create an IAM role for Defender for Cloud:

From your Amazon Web Services console, under Security, Identity & Compliance, select IAM.

1.  Select **Roles** and Create role.
    
2.  Select **Another AWS account**.
    
3.  Enter the following details:
    
    -   Account ID - enter the Microsoft Account ID (158177204117) as shown in the AWS connector page in Security Center.
        
    -   Require External ID - should be selected
        
    -   External ID - enter the subscription ID as shown in the AWS connector page in Security Center
        
4.  Select **Next**.
    
5.  In the Attach permission policies section, select the following policies:
    
    -   SecurityAudit
        
    -   AmazonSSMAutomationRole
        
    -   AWSSecurityHubReadOnlyAccess
        
6.  Optionally add tags. Adding Tags to the user doesn't affect the connection.
    
7.  Select **Next**.
    
8.  In The Roles list, choose the role you created
    
9.  Save the Amazon Resource Name (ARN) for later.
    

### Configure the SSM Agent

AWS Systems Manager is required for automating tasks across your AWS resources. If your EC2 instances don't have the SSM Agent, follow the relevant instructions from Amazon:

### Complete Azure Arc prerequisites

Make sure the appropriate Azure resources providers are registered:

-   Microsoft.HybridCompute
    
-   Microsoft.GuestConfiguration
    

Create a Service Principal for onboarding at scale. As an Owner on the subscription you want to use for the onboarding, create a service principal for Azure Arc onboarding as described in Create a Service Principal for onboarding at scale.

### Connect AWS to Defender for Cloud

From Defender for Cloud's menu, select Security solutions and then select Multi cloud connectors.

Select Add AWS account.

Configure the options in the AWS authentication tab:

1.  Enter a Display name for the connector.
    
2.  Confirm that the subscription is correct. It's the subscription that will include the connector and AWS Security Hub recommendations.
    
3.  Depending on the authentication option, you chose in Step 2. Set up authentication for Security Center in AWS:
    
    -   Select Assume Role and paste the ARN from Create an IAM role for Security Center. Pasting the ARN file in the relevant field of the AWS connection wizard in the Azure portal
    
    or
    
    -   Select Credentials and paste the access key and secret key from the .csv file you saved in Create an AWS user for Security Center.
4.  Select **Next**.
    
5.  Configure the options in the Azure Arc Configuration tab:
    
    -   Defender for Cloud discovers the EC2 instances in the connected AWS account and uses SSM to onboard them to Azure Arc.
        
    -   Select the Resource Group and Azure Region that the discovered AWS EC2s will be onboarded to in the selected subscription.
        
    -   Enter the Service Principal ID and Service Principal Client Secret for Azure Arc as described here Create a Service Principal for onboarding at scale
        
    -   If the machine connects to the internet via a proxy server, specify the proxy server IP address or the name and port number that the machine uses to communicate with the proxy server. Enter the value in the format http://<proxyURL>:<proxyport>
        
6.  Select **Review + create**.
    
7.  Review the summary information
    
8.  The Tags sections will list all Azure Tags that will be automatically created for each onboarded EC2 with its own relevant details to easily recognize it in Azure.
    

### Confirmation

After the connector is successfully created and AWS Security Hub has been configured properly:

-   Defender for Cloud scans the environment for AWS EC2 instances, onboarding them to Azure Arc, enabling it to install the Log Analytics agent and providing threat protection and security recommendations.
    
-   The ASC service scans for new AWS EC2 instances every 6 hours and onboards them according to the configuration.
    
-   The AWS CIS standard will be shown in the Defender for Cloud's regulatory compliance dashboard.
    
-   If Security Hub policy is enabled, recommendations will appear in the Defender for Cloud portal and the regulatory compliance dashboard 5-10 minutes after onboard completes.

# Connect GCP accounts

Onboarding your GCP account into Microsoft Defender for Cloud, integrates GCP Security Command and Defender for Cloud. Defender for Cloud thus provides visibility and protection across both of these cloud environments to provide:

-   Detection of security misconfigurations
    
-   A single view showing Defender for Cloud recommendations and GCP Security Command Center findings
    
-   Incorporation of your GCP resources into Defender for Cloud's secure score calculations
    
-   Integration of GCP Security Command Center recommendations based on the CIS standard into the Defender for Cloud's regulatory compliance dashboard
    

In the screenshot below, you can see GCP projects displayed in Defender for Cloud's overview dashboard.

![Screenshot of the G C P project overview settings.](https://learn.microsoft.com/en-us/training/wwl-sci/connect-non-azure-machines-to-azure-defender/media/gcp-account-overview.png)

## Follow the steps below to create your GCP cloud connector.

### Set up GCP Security Command Center with Security Health Analytics

For all the GCP projects in your organization, you must also:

-   Set up GCP Security Command Center using these instructions from the GCP documentation.
    
-   Enable Security Health Analytics using these instructions from the GCP documentation.
    
-   Verify that there's data flowing to the Security Command Center.
    

The instructions for connecting your GCP environment for security configuration follow Google's recommendations for consuming security configuration recommendations. The integration uses Google Security Command Center and will consume more resources that might impact your billing.

When you first enable Security Health Analytics, it might take several hours for data to be available.

### Enable GCP Security Command Center API

1.  From Google's Cloud Console API Library, select the project you want to connect to Azure Security Center.
    
2.  In the API Library, find and select **Security Command Center API**.
    
3.  On the API's page, select **ENABLE**.
    

### Create a dedicated service account for the security configuration integration

1.  In the GCP Console, select the project you want to connect to Security Center.
    
2.  In the Navigation menu, Under IAM & admin options, select **Service accounts**.
    
3.  Select **CREATE SERVICE ACCOUNT**.
    
4.  Enter an account name, and select **Create**.
    
5.  Specify the Role as Security Center Admin Viewer, and select **Continue**.
    
6.  The Grant users access to this service account section is optional. Select **Done**.
    
7.  Copy the Email value of the created service account, and save it for later use.
    
8.  In the Navigation menu, Under IAM & admin options, select **IAM**
    
9.  Switch to organization level.
    
10.  Select **ADD**.
    
11.  In the New members field, paste the Email value you copied earlier.
    
12.  Specify the Role as **Security Center Admin Viewer** and then select **Save**.
    

### Create a private key for the dedicated service account

Switch to project level.

1.  In the Navigation menu, Under IAM & admin options, select **Service accounts**.
    
2.  Open the dedicated service account and select **Edit**.
    
3.  In the Keys section, select **ADD KEY** and then **Create new key**.
    
4.  In the Create private key screen, select **JSON**, and then select **CREATE**.
    
5.  Save this JSON file for later use.
    

### Connect GCP to Defender for Cloud

1.  From Defender for Cloud's menu, select **Cloud connectors**.
    
2.  Select **add GCP account**.
    
3.  On the onboarding page, do the following and then select Next.
    
4.  Validate the chosen subscription.
    
5.  In the Display name field, enter a display name for the connector.
    
6.  In the Organization ID field, enter your organization's ID.
    
7.  In the Private key file box, browse to the JSON file you downloaded in the previous step. Create a private key for the dedicated service account.
    

### Confirmation

When the connector is successfully created and GCP Security Command Center has been configured properly:

-   The GCP CIS standard will be shown in the Defender for Cloud's regulatory compliance dashboard.
    
-   Security recommendations for your GCP resources will appear in the Security Center portal and the regulatory compliance dashboard 5-10 minutes after onboard completes:
    

![Screenshot of the G C P resources in recommendations](https://learn.microsoft.com/en-us/training/wwl-sci/connect-non-azure-machines-to-azure-defender/media/gcp-resources-recommendations.png)

# Knowledge check

1. Which is an option to connect your non-Azure computers?

Windows Store

[X] Using Azure Arc enabled servers

Correct. Using Azure Arc enabled servers is an option to connect.

From an Excel spreadsheet

2. Which resource can Microsoft Defender for Cloud protect in a hybrid environment?

Word Documents

[X] SQL Databases

Correct. SQL Databases can be protected by Microsoft Defender for Cloud.

Cosmos DB

3. Which Cloud provider has a Cloud connector in Security Center?

IBM Cloud

[X] GCP

Correct. GCP has a cloud connector.

Oracle

# Summary and resources

You should have learned how Microsoft Defender for Cloud can protect hybrid workloads, including on-premise, Amazon Web Services (AWS), and Google Cloud Platform (GCP).

You should now be able to:

-   Connect non-Azure machines to Microsoft Defender for Cloud
-   Connect AWS accounts to Microsoft Defender for Cloud
-   Connect GCP accounts to Microsoft Defender for Cloud

## Learn more

You can learn more by reviewing the following.

[Become an Microsoft Defender for Cloud Ninja (microsoft.com)](https://techcommunity.microsoft.com/t5/azure-security-center/become-an-azure-security-center-ninja/ba-p/1608761)

[Microsoft Tech Community Security Webinars](https://techcommunity.microsoft.com/t5/microsoft-security-and/security-community-webinars/ba-p/927888)

[Installing and Configuring SSM Agent on Windows Instances](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-install-ssm-win.html)

[Installing and Configuring SSM Agent on Amazon EC2 Linux Instances](https://docs.aws.amazon.com/systems-manager/latest/userguide/sysman-install-ssm-agent.html)