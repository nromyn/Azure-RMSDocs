---
# required metadata

title: Configuring applications for the Azure Rights Management service | Azure Information Protection
description: Instructions for admins to configure applications and services to support the Azure Rights Management protection service for Azure Information Protection. For example, Office applications such as Word 2013 and Word 2010, and services such as Exchange Online (transport rules, data loss prevention, do not forward, and message encryption) and SharePoint Online (protected libraries). 
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: article
ms.prod:
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configuring applications for Azure Rights Management

>*Applies to: Azure Information Protection, Office 365*

> [!NOTE]
> This information is for IT administrators and consultants who have deployed Azure Information Protection. If you are looking for user help and information about how to use the Rights Management functionality for a specific application or how to open a file that is rights-protected, use the help and guidance that accompanies your application.
>
> For example, for Office applications, click the Help icon and enter search terms such as **Rights Management** or **IRM**. For the RMS sharing application for Windows, see the [Rights Management sharing application user guide](../rms-client/sharing-app-user-guide.md).

After you have deployed Azure Information Protection for your organization, use the following information to configure applications and services to support the Azure Rights Management service from Azure Information Protection. These include Office applications such as Word 2013 and Word 2010, and services such as Exchange Online (transport rules, data loss prevention, do not forward, and message encryption) and SharePoint Online (protected libraries). For information about how these applications and services support Rights Management, see [How applications support the Azure Rights Management service](../understand-explore/applications-support.md).

> [!IMPORTANT]
> For information about supported versions and other requirements, see [Requirements for Azure Rights Management](../get-started/requirements-azure-rms.md).

-   [Office 365: Configuration for clients and online services](configure-office365.md)

    -   [Exchange Online: IRM Configuration](configure-office365.md#exchange-online-irm-configuration)

    -   [SharePoint Online and OneDrive for Business: IRM Configuration](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)

- [Office applications: Configuration for clients](configure-office-apps.md)

	-   [Office 2016 and Office 2013](configure-office-apps.md#office-2016-and-office-2013)

	-   [Office 2010](configure-office-apps.md#office-2010)

-   [Rights Management sharing application: Installation and configuration for clients](configure-sharing-app.md)

    -   [The RMS sharing application for Windows: Installation and configuration](configure-sharing-app.md#the-rms-sharing-application-for-windows-installation-and-configuration)

    -   [The RMS sharing application for mobile platforms: Installation and management](configure-sharing-app.md#the-rms-sharing-application-for-mobile-platforms-installation-and-management)


To configure on-premises servers such as Exchange Server and SharePoint Server, see [Deploying the Azure Rights Management connector](deploy-rms-connector.md).

> [!TIP]
> For high-level examples and screenshots of applications configured to use the Azure Rights Management service, see [Azure RMS in action: What administrators and users see](../understand-explore/what-admins-users-see.md).


In addition to these applications and services, there are other applications that support the Rights Management APIs. This category includes line-of-business applications that are written in-house by using the Rights Management SDK, and applications from software vendors that are written by using the Rights Management SDK. For these applications, follow the instructions that are provided with the application.

## Next steps
After you’ve configured your applications to support the Azure Rights Management service, use the [Azure Information Protection deployment roadmap](../plan-design/deployment-roadmap.md) to check whether there are other configuration steps that you might want to do before you roll out Azure Information Protection to users and administrators. If not, you might find the following operational information useful:

- [Verifying the Azure Rights Management service](verify.md)

- [Helping users to protect files by using the Azure Rights Management service](help-users.md)

- [Logging and analyzing the Azure Rights Management service](log-analyze-usage.md)

- [Operations for your Azure Information Protection tenant key](operations-tenant-key.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

