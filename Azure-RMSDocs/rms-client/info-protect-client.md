---
# required metadata

title: Installing the Azure Information Protection client | Azure Information Protection
description: Instructions to install the client that adds an Information Protection bar to your Office applications so that you can select classification labels for your documents and emails.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/05/2017
ms.topic: article
ms.prod:
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: eymanor
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Installing the Azure Information Protection client

>*Applies to: Azure Information Protection*

To classify documents and email messages by using Azure Information Protection, you must first install the Azure Information Protection client. This installation adds an Information Protection bar to your Office applications (Word, Excel, PowerPoint, Outlook) that displays the classification labels for your organization, in addition to a new **Protection** group on the **Home** tab (Word, Excel, PowerPoint), that has a button named **Protect**:

The following picture shows this Information Protection bar and the labels from the [default policy](../deploy-use/configure-policy-default.md):

![Azure Information Protection bar with default policy](../media/info-protect-bar-default.png)

Download the Azure Information Protection client from the [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). Currently, you can install the General Availability (GA) version, and the preview version. The preview version includes new functionality for evaluation purposes, and is subject to change. For more information, see the following blog post announcement: [Azure Information Protection December preview now available](https://blogs.technet.microsoft.com/enterprisemobility/2016/12/07/azure-information-protection-december-preview-now-available/)

Before you install the client, check that you have the required operating system versions and applications for the Azure Information Protection client: [Requirements for Azure Information Protection](../get-started/requirements-azure-rms.md). In addition, for the preview version of the client, computers running Windows 7 SP1 require [KB 2533623](https://support.microsoft.com/en-us/kb/2533623), which can be installed after the client is installed. If this update is required and not installed, you will be prompted to install it.


## To install the Azure Information Protection client manually

> [!NOTE]
> Installations that require local administrative permissions:
> 
> - The General Availability version
>     
> - The preview version with Office 2010
    
1. After you have [downloaded the client](https://www.microsoft.com/en-us/download/details.aspx?id=53018), run the executable, such as **AzInfoProtection.exe**, and follow the prompts to install the client.
    
    Select the option to install a **demo policy** if you cannot connect to Office 365 or Azure Active Directory, but want to see and experience the client side of Azure Information Protection by using a local policy for demonstration purposes. When your client connects to an Azure Information Protection service, this demo policy is replaced with your organization's Azure Information Protection policy.
    
    More information about what gets installed:

    - The General Availability version installs the Azure Information Protection bar for the Office applications. 
    
    - The latest preview version of the client installs the Azure Information Protection bar for the Office applications, right-click options for File Explorer, a viewer for protected files, and Windows PowerShell cmdlets to classify and protect files in bulk. 
        
        Note that you can install just the PowerShell module (RMSProtection) by specifying the parameter **PowerShellOnly=true**. For example: `AzInfoProtection_PREVIEW_1.3.98.0.exe  PowerShellOnly=true`

2. To complete the installation: 

    - If your computer runs Office 2010, restart your computer. 
        
        **If you installed the preview version of the client**: In addition to restarting your computer, open one of the Office applications that use the Azure Information Protection bar (for example, Word), and confirm any prompts to update the registry for this first-time use. [Service discovery](../rms-client/client-deployment-notes.md#rms-service-discovery) is used to populate the registry keys. 
    
    - For other versions of Office, restart any Office applications. 
        
        **If you installed the preview version of the client**: In addition to restarting any Office applications, also close and restart File Explorer.

## To install the Azure Information Protection client for users

You can script and automate the installation of the Azure Information Protection client by using command line options. To see the install options, run the executable with **/help**. For example: `AzInfoProtection.exe /help`

Example to silently install the General Availability version of the client: `AzInfoProtection.exe /quiet`

Example to silently install only the PowerShell module, with the preview client: `AzInfoProtection_PREVIEW_1.3.98.0.exe  PowerShellOnly=true /quiet`

If you are installing the preview version of the client on computers that run Office 2010, specify the **ServiceLocation** parameter if your users are not local administrators on their computers. See the next section for more information.

The General Availability version of the Azure Information Protection client is also included in the Microsoft Update catalog, so that you can install and update the client by using any software update service that uses the catalog. Preview versions of the client are not included in the Microsoft Update catalog.

### Preview version and Office 2010 only

For the preview version of the client and Office 2010, when you install the client for users, specify the ServiceLocation parameter and the URL for your Azure Rights Management service. This parameter and value creates and sets the following registry keys:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

Use the following procedure to identify the value to specify for the ServiceLocation parameter. 

#### To identify the value to specify for the ServiceLocation parameter

1. From a PowerShell session, first run [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice) and specify your administrator credentials to connect to the Azure Rights Management service. Then run [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration). 
 
    If you haven’t already installed the PowerShell module for the Azure Rights Management service, see [Installing Windows PowerShell for Azure Rights Management](../deploy-use/install-powershell.md).

2. From the output, identify the **LicensingIntranetDistributionPointUrl** value.

    For example: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. From the value, remove **/_wmcs/licensing** from this string. For example: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    The remaining string is the the value to specify for your ServiceLocation parameter.

Example to install the client silently for Office 2010 and Azure RMS: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


## To uninstall the Azure Information Protection client

You can use any of these options:

- Use Control Panel to uninstall a program: Click **Microsoft Azure Information Protection** > **Uninstall**

- Rerun the executable (for example, **AzInfoProtection.exe**), and from the **Modify Setup** page, click **Uninstall**. 

- Run the executable with **/uninstall**. For example: `AzInfoProtection.exe /uninstall`


## To verify installation, connection status, or report a problem

1. Open an Office application and on the **Home** tab, in the **Protection** group, click **Protect**, and then click **Help and feedback**.

2. In the **Microsoft Azure Information Protection** dialog box, note the following:

    - In the **client status** section: Use the **Version** value to verify that the installation was successful. In addition, you see when the client last connected to your organization's Azure Information Protection service and when the Azure Information Protection policy was last installed or updated. When the client connects to the service, it automatically downloads the latest policy if it finds changes from its current policy. If you have made policy changes after the displayed time, close and reopen the Office application.
    
        You also see your displayed user name that identifies the account that is used to authenticate you to Azure Information Protection. This user name must match an account that you use for Office 365 or Azure Active Directory and that belongs to a tenant that is configured for Azure Information Protection.

    - In the **Help and feedback** section: The **Tell me more link** by default, goes to the [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection) website but can be configured for a custom URL as one of the [policy settings](../deploy-use/configure-policy-settings.md) in the Azure Information Protection policy.
        
        Use the **Send feedback** link to automatically attach your client logs to an email message that can be sent to the Information Protection team to investigate a problem. 
    
        For diagnostic information and to reset the client, click **Run diagnostics**. When the diagnostics tests finish, click **Copy Results** to paste the information into an email that you can send to your help desk or Microsoft support. When the tests finish, you can also reset the client.
        
        More information about the **Reset** option:
        
        - You do not have to be a local administrator to use this option and this action is not logged in the Event Viewer. 
        
        - Unless files are locked, this action deletes all the files in **%localappdata%\Microsoft\MSIPC**, which is where client certificates and rights management templates are stored. It does not delete the Azure Information Protection policy, or the client log files, or sign out the user.
        
        - The following registry key and settings are deleted: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. If you configure settings for this registry key (for example, settings for redirection to your Azure Information Protection tenant because you are migrating from AD RMS and still have a Service Connection Point on your network), you must reconfigure the registry settings after you reset the client.
        
        - After you have reset the client, you must re-initialize the user environment (also known as "bootstrapping"), which will download certificates for the client and the latest templates. To do this, close all instances of Office and then restart an Office application. This action will also check that you have downloaded the latest Azure Information Protection policy. Do not run the diagnostics tests again until you have done this.


## Usage logging

**[ This feature requires the preview version of the client and is subject to change. ]**

For the preview version of the Azure Information Protection client, the client logs user activity to the local Windows **Applications and Services** event log, **Azure Information Protection**. The events include the following information:

- Date, client version, policy ID

- Signed in user name, computer name

- File name and location

- Action:

    - Set Label:  Information ID 101​
    
    - Set Label (lower):  Information ID 102​
    
    - Set Label (higher): Information ID 103​
    
    - Remove label: Information ID 104​
   
    - Recommended tip: Information 105​
    
    - Apply custom protection: Information ID 201​
    
    - Remove custom protection: Information ID 202​
    
    - Sign in (operational): Information ID 902​
    
    - Download policy (operational): Information ID 901
    
- Action source:
    
    - Manual ​
    
    - Recommended​
    
    - Automatic  ​
    
    - System (for sign in and download policy)
    
- Label before and after action ​
    
- Protection before and after action​
    
- User justification (when applicable)
    

## Keyboard shortcuts for the Azure Information Protection bar

To access the Azure Information Protection bar by using keyboard shortcuts, use the following key combination:

- Press **Ctrl** + **Shift** + **~** 

Then, use the Tab key to select the labels and other controls on the bar (the **Hide labels** icon and **Remove label** icon), and the Enter key to select them.


## File locations

Client files:	

- For 64-bit operating systems: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- For 32-bit operating systems: **\Program Files\Microsoft Azure Information Protection**

Client logs files and currently installed policy file:

- For 64-bit and 32-bit operating systems: **%localappdata%\Microsoft\MSIP**


## Next steps

To change the labels on the Information Protection bar, you must configure the Azure Information Protection policy. For more information, see [Configuring Azure Information Protection policy](../deploy-use/configure-policy.md).

For an example of how to customize the default policy, and see the resulting behavior in an Office application, try the [Quick start tutorial for Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

To check the release version information for the client, see the [Version release history](client-version-release-history.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]