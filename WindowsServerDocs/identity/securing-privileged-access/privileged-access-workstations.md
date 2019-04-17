---
title: "Станции с привилегированным доступом"
description: "Безопасность Windows Server"
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 93589778-3907-4410-8ed5-e7b6db406513
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 06/09/2016
ms.openlocfilehash: ce64974d771a11ef11257bceef1c3fde1797a7da
ms.sourcegitcommit: 3bf47cf4e25896725137d983d63b8041a53cb9a2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="privileged-access-workstations"></a>Станции с привилегированным доступом

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Privileged Access Workstations (PAWs) provide a dedicated operating system for sensitive tasks that is protected from Internet attacks and threat vectors. Separating these sensitive tasks and accounts from the daily use workstations and devices provides very strong protection from phishing attacks, application and OS vulnerabilities, various impersonation attacks, and credential theft attacks such as keystroke logging, [Pass-the-Hash](https://www.microsoft.com/en-us/download/details.aspx?id=36036), and [Pass-The-Ticket](https://download.microsoft.com/download/7/7/A/77ABC5BD-8320-41AF-863C-6ECFB10CB4B9/Mitigating%20Pass-the-Hash%20(PtH)%20Attacks%20and%20Other%20Credential%20Theft%20Techniques_English.pdf).

## <a name="architecture-overview"></a>Architecture Overview
The diagram below depicts a separate "channel" for administration (a highly sensitive task) that is created by maintaining separate dedicated administrative accounts and workstations.

![Diagram showing a separate "channel" for administration (a highly sensitive task) that is created by maintaining separate dedicated administrative accounts and workstations](../media/privileged-access-workstations/PAWFig1.JPG)

This architectural approach builds on the protections found in the Windows 10 [Credential Guard](https://technet.microsoft.com/en-us/library/mt483740%28v=vs.85%29.aspx) and [Device Guard](https://technet.microsoft.com/en-us/library/dn986865(v=vs.85).aspx) features and goes beyond those protections for sensitive accounts and tasks.

This methodology is appropriate for accounts with access to high value assets:

-   **Administrative Privileges** the PAWs provide increased security for high impact IT administrative roles and tasks. This architecture can be applied to administration of many types of systems including Active Directory Domains and Forests, Microsoft Azure Active Directory tenants, Office 365 tenants, Process Control Networks (PCN), Supervisory Control and Data Acquisition (SCADA) systems, Automated Teller Machines (ATMs), and Point of Sale (PoS) devices.

-   **High Sensitivity Information workers** the approach used in a PAW can also provide protection for highly sensitive information worker tasks and personnel such as those involving pre-announcement Merger and Acquisition activity, pre-release financial reports, organizational social media presence, executive communications, unpatented trade secrets, sensitive research, or other proprietary or sensitive data. This guidance does not discuss the configuration of these information worker scenarios in depth or include this scenario in the technical instructions.

    > [!NOTE]
    > Microsoft IT uses PAWs (internally referred to as "secure admin workstations", or SAWs) to manage secure access to internal high-value systems within Microsoft. This guidance has additional details below on PAW usage at Microsoft in the section "How Microsoft uses admin workstations". For more detailed information on this high value asset environment approach, please refer to the article, [Protecting high-value assets with secure admin workstations](https://msdn.microsoft.com/en-us/library/mt186538.aspx).

This document will describe why this practice is recommended for protecting high impact privileged accounts, what these PAW solutions look like for protecting administrative privileges, and how to quickly deploy a PAW solution for domain and cloud services administration.

This document provides detailed guidance for implementing several PAW configurations and includes detailed implementation instructions to get you started on protecting common high impact accounts:

-   **Phase 1 - Immediate Deployment for Active Directory Administrators** this provides a PAW quickly that can protect on premises domain and forest administration roles

-   **Phase 2 - Extend PAW to all administrators** this enables protection for administrators of cloud services like Office 365 and Azure, enterprise servers, enterprise applications, and workstations

-   **Phase 3 - Advanced PAW security** this discusses additional protections and considerations for PAW security

### <a name="why-a-dedicated-workstation"></a>Why a dedicated workstation?
The current threat environment for organizations is rife with sophisticated phishing and other internet attacks that create continuous risk of security compromise for internet exposed accounts and workstations.

This threat environment requires an organizations to adopt an "assume breach" security posture when designing protections for high value assets like administrative accounts and sensitive business assets. These high value assets need to be protected against both direct internet threats as well as attacks mounted from other workstations, servers, and devices in the environment.

![Figure showing the risk to managed assets if an attacker gains control of a user workstation where sensitive credentials are used](../media/privileged-access-workstations/PAWFig2.JPG)

This figure depicts risk to managed assets if an attacker gains control of a user workstation where sensitive credentials are used.

An attacker in control of an operating system has numerous ways in which to illicitly gain access to all activity on the workstation and impersonate the legitimate account. A variety of known and unknown attack techniques can be used to gain this level of access. The increasing volume and sophistication of cyberattacks have made it necessary to extend that separation concept to completely separate client operating systems for sensitive accounts. For more information on these types of attacks, please visit the [Pass The Hash web site](https://www.microsoft.com/pth) for informative white papers, videos and more.

The PAW approach is an extension of the well-established recommended practice to use separate admin and user accounts for administrative personnel. This practice uses an individually assigned administrative account that is completely separate from the user's standard user account. PAW builds on that account separation practice by providing a trustworthy workstation for those sensitive accounts.

> [!NOTE]
> Microsoft IT uses PAWs (internally referred to as "secure admin workstations", or SAWs) to manage secure access to internal high-value systems within Microsoft.  This guidance has additional details on PAW usage at Microsoft in the section "How Microsoft uses admin workstations"
>
> For more detailed information on this high value asset environment approach, please refer to the article [Protecting high-value assets with secure admin workstations](https://msdn.microsoft.com/en-us/library/mt186538.aspx).

This PAW guidance is intended to help you implement this capability for protecting high value accounts such as high-privileged IT administrators and high sensitivity business accounts. The guidance helps you:

-   Restrict exposure of credentials to only trusted hosts

-   Provide a high-security workstation to administrators so they can easily perform administrative tasks.

Restricting the sensitive accounts to using only hardened PAWs is a straightforward protection for these accounts that is both highly usable for administrators and very difficult for an adversary to defeat.

#### <a name="alternate-approaches---limitations-considerations-and-integration"></a>Alternate approaches - Limitations, considerations, and integration
This section contains information on how the security of alternate approaches compares to PAW and how to correctly integrate these approaches within a PAW architecture. All of these approaches carry significant risks when implemented in isolation, but can add value to a PAW implementation in some scenarios.

**Credential Guard and Microsoft Passport**

Introduced in Windows 10, [Credential Guard](https://technet.microsoft.com/en-us/library/mt483740%28v=vs.85%29.aspx) uses hardware and virtualization-based security to mitigate common credential theft attacks, such as Pass-the-Hash, by protecting the derived credentials. The private key for credentials used by [Microsoft Passport](http://aka.ms/passport) can be also be protected by Trusted Platform Module (TPM) hardware.

These are powerful mitigations, but workstations can still be vulnerable to certain attacks even if the credentials are protected by Credential Guard or Passport. Attacks can include abusing privileges and use of credentials directly from a compromised device, reusing previously stolen credentials prior to enabling Credential Guard, and abuse of management tools and weak application configurations on the workstation.

The PAW guidance in this section includes the use of many of these technologies for high sensitivity accounts and tasks.

**Administrative VM**

An administrative virtual machine (VM) is a dedicated operating system for administrative tasks hosted on a standard user desktop. While this approach is similar to PAW in providing a dedicated OS for administrative tasks, it has a fatal flaw in that the administrative VM is dependent on the standard user desktop for its security.

The diagram below depicts the ability of attackers to follow the control chain to the target object of interest with an Admin VM on a User Workstation and that it is difficult to create a path on the reverse configuration.

The PAW architecture does not allow for hosting an admin VM on a user workstation, but a user VM with a standard corporate image can be hosted on a PAW host to provide personnel with a single PC for all responsibilities.

![Diagram of the PAW architecture](../media/privileged-access-workstations/PAWFig9.JPG)

**Jump Server**

Administrative "Jump Server" architectures set up a small number administrative console servers and restrict personnel to using them for administrative tasks. This is typically based on remote desktop services, a 3rd-party presentation virtualization solution, or a Virtual Desktop Infrastructure (VDI) technology.

This approach is frequently proposed to mitigate risk to administration and does provide some security assurances, but the jump server approach by itself is vulnerable to certain attacks because it violates the ["clean source" principle](http://aka.ms/cleansource). Принцип чистоты источника надежности всех зависимых безопасности быть так надежно, как и защищаемого объекта.

![Figure showing a simple control relationship](../media/privileged-access-workstations/PAWFig3.JPG)

This figure depicts a simple control relationship. Любой субъект под управлением объекта является зависимостью безопасности этого объекта. If an adversary can control a security dependency of a target object (subject), they can control that object.

The administrative session on the jump server relies on the integrity of the local computer accessing it. If this computer is a user workstation subject to phishing attacks and other internet-based attack vectors, then the administrative session is also subject to those risks.

![Figure showing how attackers can follow an established control chain to the target object of interest](../media/privileged-access-workstations/PAWFig4.JPG)

The figure above depicts how attackers can follow an established control chain to the target object of interest.

While some advanced security controls like multi-factor authentication can increase the difficulty of an attacker taking over this administrative session from the user workstation, no security feature can fully protect against technical attacks when an attacker has administrative access of the source computer (e.g. injecting illicit commands into a legitimate session, hijacking legitimate processes, and so on.)

The default configuration in this PAW guidance installs administrative tools on the PAW, but a jump server architecture can also be added if required.

![Figure showing how reversing the control relationship and accessing user apps from an admin workstation gives the attacker no path to the targeted object](../media/privileged-access-workstations/PAWFig5.JPG)

This figure shows how reversing the control relationship and accessing user apps from an admin workstation gives the attacker no path to the targeted object. The user jump server is still exposed to risk so appropriate protective controls, detective controls, and response processes should still be applied for that internet-facing computer.

This configuration requires administrators to follow operational practices closely to ensure that they don't accidentally enter administrator credentials into the user session on their desktop.

![Figure showing how accessing an administrative jump server from a PAW adds no path for the attacker into the administrative assets](../media/privileged-access-workstations/PAWFig6.JPG)

This figure shows how accessing an administrative jump server from a PAW adds no path for the attacker into the administrative assets. A jump server with a PAW allows in this case you to consolidate the number of locations for monitoring administrative activity and distributing administrative applications and tools. This adds some design complexity, but can simplify security monitoring and software updates if a large number of accounts and workstations are used in your PAW implementation. The jump server would need to be built and configured to similar security standards as the PAW.

**Privilege Management Solutions**

Privileged Management solutions are applications that provide temporary access to discrete privileges or privileged accounts on demand. Privilege management solutions are an extremely valuable component of a complete strategy to secure privileged access and provide critically important visibility and accountability of administrative activity.

These solutions typically use a flexible workflow to grant access and many have additional security features and capabilities like service account password management and integration with administrative jump servers. There are many solutions on the market that provide privilege management capabilities, one of which is Microsoft Identity Manager (MIM) privileged access management (PAM).

Microsoft recommends using a PAW to access privilege management solutions. Access to these solutions should be granted only to PAWs. Microsoft does not recommend using these solutions as a substitute for a PAW because accessing privileges using these solutions from a potentially compromised user desktop violates the [clean source](http://aka.ms/cleansource) principle as depicted in the diagram below:

![Diagram showing how Microsoft does not recommend using these solutions as a substitute for a PAW because accessing privileges using these solutions from a potentially compromised user desktop violates the clean source principle](../media/privileged-access-workstations/PAWFig7.JPG)

Providing a PAW to access these solutions enables you to gain the security benefits of both PAW and the privilege management solution, as depicted in this diagram:

![Diagram showing how providing a PAW to access these solutions enables you to gain the security benefits of both PAW and the privilege management solution](../media/privileged-access-workstations/PAWFig8.JPG)

> [!NOTE]
> These systems should be classified at the highest tier of the privilege they manage and be protected at or above that level of security. These are commonly configured to manage Tier 0 solutions and Tier 0 assets and should be classified at Tier 0.
> For more information on the tier model, see [http://aka.ms/tiermodel](http://aka.ms/tiermodel) For more information on Tier 0 groups, see Tier 0 equivalency in [Securing Privileged Access Reference Material](../securing-privileged-access/securing-privileged-access-reference-material.md).

For more information on deploying Microsoft Identity Manager (MIM) privileged access management (PAM), see [http://aka.ms/mimpamdeploy](http://aka.ms/mimpamdeploy)

#### <a name="how-microsoft-is-using-admin-workstations"></a>How Microsoft is using admin workstations
Microsoft uses the PAW architectural approach both internally on our systems as well as with our customers. Microsoft uses administrative workstations internally in a number of capacities including administration of Microsoft IT infrastructure, Microsoft cloud fabric infrastructure development and operations, and other high value assets.

This guidance is directly based on the Privileged Access Workstation (PAW) reference architecture deployed by our cybersecurity professional services teams to protect customers against cybersecurity attacks. The administrative workstations are also a key element of the strongest protection for domain administration tasks, the Enhanced Security Administrative Environment (ESAE) administrative forest reference architecture.

For more details on the ESAE administrative forest, see [ESAE Administrative Forest Design Approach](http://aka.ms/ESAE) section in [Securing Privileged Access Reference Material](../securing-privileged-access/securing-privileged-access-reference-material.md).

For more information on engaging Microsoft services to deploy a PAW or ESAE for your environment, contact your Microsoft representative or visit [this page](https://www.microsoft.com/en-us/microsoftservices/campaigns/cybersecurity-protection.aspx).

### <a name="what-is-a-privileged-access-workstation-paw"></a>What is a Privileged Access Workstation (PAW)?
In simplest terms, a PAW is a hardened and locked down workstation designed to provide high security assurances for sensitive accounts and tasks.  PAWs are recommended for administration of identity systems, cloud services, and private cloud fabric as well as sensitive business functions.

> [!NOTE]
> The PAW architecture doesn't require a 1:1 mapping of accounts to workstations, though this is a common configuration. PAW creates a trusted workstation environment that can be used by one or more accounts.

In order to provide the greatest security, PAWs should always run the most up-to-date and secure operating system available: Microsoft strongly recommends Windows 10 Enterprise, which includes a number of additional security features not available in other editions (in particular, [Credential Guard](https://technet.microsoft.com/en-us/library/mt483740%28v=vs.85%29.aspx) and [Device Guard](https://technet.microsoft.com/en-us/library/dn986865(v=vs.85).aspx)).

> [!NOTE]
> Organizations without access to Windows 10 Enterprise can use Windows 10 Pro, which includes many of the critical foundational technologies for PAWs, including Trusted Boot, BitLocker, and Remote Desktop.  Education customers can use Windows 10 Education.  Windows 10 Home should not be used for a PAW.
>
> For a comparison matrix of the different editions of Windows 10, read [this article](https://www.microsoft.com/en-us/WindowsForBusiness/Compare).

The security controls in PAW are focused on mitigating the highest impact and most likely risks of compromise. These include mitigating attacks on the environment and mitigating risks that the PAW controls may degrade over time:

-   **Internet attacks** - Most attacks originate directly or indirectly from internet sources and use the internet for exfiltration and command and control (C2). Isolating the PAW from the open internet is a key element to ensuring the PAW is not compromised.

-   **Usability risk** - If a PAW is too difficult to use for daily tasks, administrators will be motivated to create workarounds to make their jobs easier. Frequently, these workarounds open the administrative workstation and accounts to significant security risks, so it's critical to involve and empower the PAW users to mitigate these usability issues securely. This is frequently accomplished by listening to their feedback, installing tools and scripts required to perform their jobs, and ensuring all administrative personnel are aware of why they need to use a PAW, what a PAW is, and how to use it correctly and successfully.

-   **Environment risks** - Because many other computers and accounts in the environment are exposed to internet risk directory or indirectly, a PAW must be protected against attacks from compromised assets in the production environment. This requires limiting the management tools and accounts that have access to the PAWs to the absolute minimum required to secure and monitor these specialized workstations.

-   **Supply chain tampering** - While it's impossible to remove all possible risks of tampering in the supply chain for hardware and software, taking a few key actions can mitigate critical attack vectors that are readily available to attackers. This includes validating the integrity of all installation media ([Clean Source Principle](http://aka.ms/cleansource)) and using a trusted and reputable supplier for hardware and software.

-   **Physical attacks** - Because PAWs can be physically mobile and used outside of physically secure facilities, they must be protected against attacks that leverage unauthorized physical access to the computer.

> [!NOTE]
> A PAW will not protect an environment from an adversary that has already gained administrative access over an Active Directory Forest.
> Because many existing implementations of Active Directory Domain Services have been operating for years at risk of credential theft, organizations should assume breach and consider the possibility that they may have an undetected compromise of domain or enterprise administrator credentials. An organization that suspects domain compromise should consider the use of professional incident response services.
>
> For more information on response and recovery guidance, see the "Respond to suspicious activity" and "Recover from a breach" sections of [Mitigating Pass-the-Hash and Other Credential Theft](https://www.microsoft.com/pth), version 2.
>
> Visit [Microsoft's Incident Response and Recovery services](https://www.microsoft.com/en-us/microsoftservices/campaigns/cybersecurity-protection.aspx) page for more information.

### <a name="paw-hardware-profiles"></a>PAW Hardware Profiles
Administrative personnel are also standard users too - they need not only a PAW, but also a standard user workstation to check email, browse the web, and access corporate line of business applications.  Ensuring that administrators can remain both productive and secure is essential to the success of any PAW deployment.  A secure solution that dramatically limits productivity will be abandoned by the users in favor of one that enhances productivity (even if it is done in an insecure manner).

In order to balance the need for security with the need for productivity, Microsoft recommends using one of these PAW hardware profiles:

-   **Dedicated hardware** - Separate dedicated devices for user tasks vs. administrative tasks

-   **Simultaneous Use** - Single device that can run user tasks and administrative tasks concurrently by taking advantage of OS or presentation virtualization.

Organizations may use only one profile or both. There are no interoperability concerns between the hardware profiles, and organizations have the flexibility to match the hardware profile to the specific need and situation of a given administrator.

> [!NOTE]
> It is critical that, in all of these scenarios, administrative personnel are issued a standard user account that is separate from designated administrative account(s). The administrative account(s) should only be used on the PAW administrative operating system.

This table summarizes the relative advantages and disadvantages of each hardware profile from the perspective of operational ease-of-use and productivity and security.  Both hardware approaches provide strong security for administrative accounts against credential theft and reuse.

|**Сценарий**|**Преимущества**|**Недостатки**|
|--------|---------|-----------|
|Dedicated hardware|-   Strong signal for sensitivity of tasks<br />-   Strongest security separation|-   Additional desk space<br />-   Additional weight (for remote work)<br />-   Hardware Cost|
|Simultaneous use|-   Lower hardware cost<br />-   Single device experience|-   Sharing single keyboard/mouse creates risk of inadvertent errors/risks|

This guidance contains the detailed instructions for the PAW configuration for the dedicated hardware approach. If you have requirements for the simultaneous use hardware profiles, you can adapt the instructions based on this guidance yourself or hire a professional services organization like Microsoft to assist with it.

**Dedicated Hardware**

In this scenario, a PAW is used for administration that is completely separate from the PC that is used for daily activities like email, document editing, and development work. All administrative tools and applications are installed on the PAW and all productivity applications are installed on the standard user workstation. The step by step instructions in this guidance are based on this hardware profile.

**Simultaneous Use - Adding a local user VM**

In this simultaneous use scenario, a single PC is used for both administration tasks and daily activities like email, document editing, and development work. In this configuration, the user operating system is available while disconnected (for editing documents and working on locally cached email), but requires hardware and support processes that can accommodate this disconnected state.

![Diagram showing single PC  in a simultaneous use scenario used for both administration tasks and daily activities like email, document editing, and development work](../media/privileged-access-workstations/PAWFig10.JPG)

The physical hardware runs two operating systems locally:

-   **Admin OS** - The physical host runs Windows 10 on the PAW host for Administrative tasks

-   **User OS** - A Windows 10 client Hyper-V virtual machine guest runs a corporate image

With Windows 10Hyper-V, a guest virtual machine (also running Windows 10) can have a rich user experience including sound, video, and Internet communications applications such as  Skype for Business.

In this configuration, daily work that does not require administrative privileges is done in the user OS virtual machine which has a regular corporate Windows 10 image and is not subject to restrictions applied to the PAW host. All administrative work is done on the Admin OS.

To configure this, follow the instructions in this guidance for the PAW host, add Client Hyper-V features, create a User VM, and then install a Windows 10 corporate image on the User VM.

Read [Client Hyper-V](https://technet.microsoft.com/en-us/library/hh857623.aspx) article for more information about this capability. Please note that the operating system in guest virtual machines will need to be licensed per [Microsoft product licensing](https://www.microsoft.com/en-us/Licensing/product-licensing/products.aspx), also described [here](https://www.microsoft.com/en-us/Licensing/learn-more/brief-windows-virtual-machine.aspx).

**Simultaneous Use - Adding RemoteApp, RDP, or a VDI**

In this simultaneous use scenario, a single PC is used for both administration tasks and daily activities like email, document editing and development work. In this configuration, the user operating systems are deployed and managed centrally (on the cloud or in your datacenter), but aren't available while disconnected.

![Figure showing a single PC in a simultaneous use scenario used for both administration tasks and daily activities like email, document editing and development work](../media/privileged-access-workstations/PAWFig11.JPG)

The physical hardware runs a single PAW operating system locally for administrative tasks and contacts a Microsoft or 3rd party remote desktop service for user applications such as email, document editing, and line of business applications.

In this configuration, daily work that does not require administrative privileges is done in the Remote OS(es) and applications which are not subject to restrictions applied to the PAW host. All administrative work is done on the Admin OS.

To configure this, follow the instructions in this guidance for the PAW host, allow network connectivity to the Remote Desktop services, and then add shortcuts to the PAW user's desktop to access the applications. The remote desktop services could be hosted in many ways including:

-   An existing Remote Desktop or VDI service (on-premises or in the cloud)

-   A new service you install on-premises or in the cloud

-   Azure RemoteApp using pre-configured Office 365 templates or your own installation images

For more information on Azure RemoteApp, visit [this page](https://www.remoteapp.windowsazure.com).

### <a name="paw-scenarios"></a>PAW Scenarios
This section contains guidance on which scenarios this PAW guidance should be applied to. In all scenarios, administrators should be trained to only use PAWs for performing support of remote systems. To encourage successful and secure usage, all PAW users should be also be encouraged to provide feedback to improve the PAW experience and this feedback should be reviewed carefully for integration with your PAW program.

In all scenarios, additional hardening in later phases and different hardware profiles in this guidance may be used to meet the usability or security requirements of the roles.

> [!NOTE]
> Note that this guidance explicitly differentiates between requiring access to specific services on the internet (such as Azure and Office 365 administrative portals) and the "Open Internet" of all hosts and services.

See the [Tier model page](http://aka.ms/tiermodel) for more information on the Tier designations.

|**Сценарии**|**Use PAW?**|**Scope and Security Considerations**|
|---------|--------|---------------------|
|Active Directory Admins - Tier 0|Да|A PAW built with Phase 1 guidance is sufficient for this role.<br /><br />-   An administrative forest can be added to provide the strongest protection for this scenario. For more information on the ESAE administrative forest, see [ESAE Administrative Forest Design Approach](http://aka.ms/esae)<br />-   A PAW can be used to managed multiple domains or multiple forests.<br />-   If Domain Controllers are hosted on an Infrastructure as a Service (IaaS) or on-premises virtualization solution, you should prioritize implementing PAWs for the administrators of those solutions|
|Admin of Azure IaaS and PaaS services - Tier 0 or Tier 1 (see Scope and Design Considerations)|Да|A PAW built using the guidance provided in Phase 2 is sufficient for this role.<br /><br />-   PAWs should be used for at least the Global administrator and Subscription Billing administrator. You should also use PAWs for delegated administrators of critical or sensitive servers.<br />-   PAWs should be used for managing the operating system and applications that provide Directory Synchronization and Identity Federation for cloud services such as [Azure AD Connect](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) and Active Directory Federation Services (ADFS).<br />-   The outbound network restrictions must allow connectivity only to authorized cloud services using the guidance in Phase 2. No open internet access should be allowed from PAWs.<br />-   EMET should be configured for all browsers used on the workstation **Note:**     A subscription is considered to be Tier 0 for a Forest if Domain Controllers or other Tier 0 hosts are in the subscription. A subscription is Tier 1 if no Tier 0 servers are hosted in Azure|
|Admin Office 365 Tenant <br />- Tier 1|Да|A PAW built using the guidance provided in Phase 2 is sufficient for this role.<br /><br />-   PAWs should be used for at least the Subscription Billing administrator, Global administrator, Exchange administrator, SharePoint administrator, and User management administrator roles. You should also strongly consider the use of PAWs for delegated administrators of highly critical or sensitive data.<br />-   EMET should be configured for all browsers used on the workstation<br />-   The outbound network restrictions must allow connectivity only to Microsoft services using the guidance in Phase 2. No open internet access should be allowed from PAWs.|
|Other IaaS or PaaS cloud service admin<br />- Tier 0 or Tier 1 (see Scope and Design Considerations)||A PAW built using the guidance provided in Phase 2 is sufficient for this role.<br /><br />-   PAWs should be used for any role that has administrative rights over cloud hosted VMs including the ability to install agents, export hard disk files, or access storage where hard drives with operating systems, sensitive data, or business critical data is stored.<br />-   The outbound network restrictions must allow connectivity only to Microsoft services using the guidance in Phase 2. No open internet access should be allowed from PAWs.<br />-   EMET should be configured for all browsers used on the workstation. **Note:** A subscription is Tier 0 for a Forest if Domain Controllers or other Tier 0 hosts are in the subscription. A subscription is Tier 1 if no Tier 0 servers are hosted in Azure.|
|Virtualization Administrators<br />- Tier 0 or Tier 1 (see Scope and Design Considerations)|Да|A PAW built using the guidance provided in Phase 2 is sufficient for this role.<br /><br />-   PAWs should be used for any role that has administrative rights over VMs including the ability to install agents, export virtual hard disk files, or access storage where hard drives with guest operating system information, sensitive data, or business critical data is stored. **Note:** A virtualization system (and its admins) are considered Tier 0 for a Forest if Domain Controllers or other Tier 0 hosts are in the subscription. A subscription is Tier 1 if no Tier 0 servers are hosted in the virtualization system.|
|Server Maintenance Admins<br />- Tier 1|Да|A PAW built using the guidance provided in Phase 2 is sufficient for this role.<br /><br />-   A PAW should be used for administrators that update, patch, and troubleshoot enterprise servers and apps running Windows server, Linux, and other operating systems.<br />-   Dedicated management tools may need to be added for PAWs to handle the larger scale of these admins.|
|User Workstation Admins <br />- Tier 2|Да|A PAW built using guidance provided in Phase 2 is sufficient for roles that have administrative rights on end user devices (such as helpdesk and deskside support roles).<br /><br />-   Additional applications may need to be installed on PAWs to enable ticket management and other support functions.<br />-   EMET should be configured for all browsers used on the workstation.<br />    Dedicated management tools may need to be added for PAWs to handle the larger scale of these admins.|
|SQL, SharePoint, or line of business (LOB) Admin<br />- Tier 1||A PAW built with Phase 2 guidance is sufficient for this role.<br /><br />-   Additional management tools may need to be installed on PAWs to allow administrators to manage applications without needing to connect to servers using Remote Desktop.|
|Users Managing Social Media Presence|Partially|A PAW built using the guidance provided in Phase 2 can be used as a starting point to provide security for these role.<br /><br />-   Protect and manage social media accounts using Azure Active Directory (AAD) for sharing, protecting, and tracking access to social media accounts.<br />    For more information on this capability read [this blog post](http://blogs.technet.com/b/ad/archive/2015/02/20/azure-ad-automated-password-roll-over-for-facebook-twitter-and-linkedin-now-in-preview.aspx).<br />-   The outbound network restrictions must allow connectivity to these services. This can be done by allowing open internet connections (much higher security risk that negates many PAW assurances) or by allowing only required DNS addresses for the service (may be challenging to obtain).|
|Standard Users|Нет|While many hardening steps can be used for standard users, PAW is designed to isolate accounts from the open internet access that most users require for job duties.|
|Guest VDI/Kiosk|Нет|While many hardening steps can be used for a kiosk system for guests, the PAW architecture is designed to provide higher security for high sensitivity accounts, not higher security for lower sensitivity accounts.|
|VIP User (Executive, Researcher, etc.)|Partially|A PAW built using guidance provided in Phase 2 can be used as a starting point to provide security for these roles<br /><br />-   This scenario is similar to a standard user desktop, but typically has a smaller, simpler, and well-known application profile. This scenario typically requires discovering and protecting sensitive data, services, and applications (which may or may not be installed on the desktops).<br />-   These roles typically require a high degree of security and very high degree of usability, which require design changes to meet user preferences.|
|Industrial control systems (e.g. SCADA, PCN, and DCS)|Partially|A PAW built using guidance provided in Phase 2 can be used as a starting point to provide security for these roles as most ICS consoles (including such common standards as SCADA and PCN) don't require browsing the open Internet and checking email.<br /><br />-   Applications used for controlling physical machinery would have to be integrated and tested for compatibility and protected appropriately|
|Embedded Operating System|Нет|While many hardening steps from PAW can be used for embedded operating systems, a custom solution would need to be developed for hardening in this scenario.|

> [!NOTE]
> **Combination scenarios** some personnel may have administrative responsibilities that span multiple scenarios.
> In these cases, the key rules to keep in mind are that the Tier model rules must be followed at all times. See the Tier model page for more information.

> [!NOTE]
> **Scaling the PAW Program** as your PAW program scales to encompass more admins and roles, you need to continue to ensure that you maintain adherence to the security standards and usability. This may require you to update your IT support structures or create new ones to resolve PAW specific challenges such as PAW onboarding process, incident management, configuration management, and gathering feedback to address usability challenges.  One example may be that your organization decides to enable work-from-home scenarios for administrators, which would necessitate a shift from desktop PAWs to laptop PAWs - a shift which may necessitate additional security considerations.  Another common example is to create or update training for new administrators - training which must now include content on the appropriate use of a PAW (including why its important and what a PAW is and isn't).  For more considerations which must be addressed as you scale your PAW program, see Phase 2 of the instructions.

This guidance contains the detailed instructions for the PAW configuration for the scenarios as noted above. If you have requirements for the other scenarios, you can adapt the instructions based on this guidance yourself or hire a professional services organization like Microsoft to assist with it.

For more information on engaging Microsoft services to design a PAW tailored for your environment, contact your Microsoft representative or visit [this page](https://www.microsoft.com/en-us/microsoftservices/campaigns/cybersecurity-protection.aspx).

### <a name="paw-installation-instructions"></a>PAW Installation instructions
Because the PAW must provide a secure and trusted source for administration, it's essential that the build process is secure and trusted.  This section will provide detailed instructions which will allow you to build your own PAW using general principles and concepts very similar to those used by Microsoft IT and Microsoft cloud engineering and service management organizations.

The instructions are divided into three phases which focus on putting the most critical mitigations in place quickly and then progressively increasing and expanding the usage of PAW for the enterprise.

-   Phase 1 - Immediate Deployment for Active Directory Administrators

-   Phase 2 - Extend PAW to all administrators

-   Phase 3 - Advanced PAW security

It is important to note that the phases should always be performed in order even if they are planned and implemented as part of the same overall project.

#### <a name="phase-1---immediate-deployment-for-active-directory-administrators"></a>Phase 1 - Immediate Deployment for Active Directory Administrators
Purpose: Provides a PAW quickly that can protect on-premises domain and forest administration roles.

Scope: Tier 0 Administrators including Enterprise Admins, Domain Admins (for all domains), and administrators of other authoritative identity systems.

Phase 1 focuses on the administrators who manage your on-premises Active Directory domain, which are critically important roles frequently targeted by attackers. These identity systems will work effectively for protecting these admins whether your Active Directory Domain Controllers (DCs) are hosted in on-premises datacenters, on Azure Infrastructure as a Service (IaaS), or another IaaS provider.

During this phase, you will create the secure administrative Active Directory organizational unit (OU) structure to host your privileged access workstation (PAW), as well as deploy the PAWs themselves.  This structure also includes the group policies and groups required to support the PAW.  You will create most of the structure using PowerShell scripts which are available at [TechNet Gallery](http://aka.ms/pawmedia).

The scripts will create the following OUs and Security Groups:

-   Organizational Units (OU)

    -   Six new top-level OUs:  Admin; Groups; Tier 1 Servers; Workstations; User Accounts; and Computer Quarantine.  Each top-level OU will contain a number of child OUs.

-   Группы

    -   Six new security-enabled global groups:  Tier 0 Replication Maintenance; Tier 1 Server Maintenance; Service Desk Operators; Workstation Maintenance; PAW Users; PAW Maintenance.

You will also create a number of group policy objects: PAW Configuration - Computer; PAW Configuration - User; RestrictedAdmin Required - Computer; PAW Outbound Restrictions; Restrict Workstation Logon; Restrict Server Logon.

Phase 1 includes the following steps:

1.  Complete the Prerequisites

    1.  **Ensure that all administrators use separate, individual accounts for administration and end user activities** (including email, Internet browsing, line-of-business applications, and other non-administrative activities).  Assigning an administrative account to each authorized personnel separate from their standard user account is fundamental to the PAW model, as only certain accounts will be permitted to log onto the PAW itself.

        > [!NOTE]
        > Each administrator should use his or her own account for administration.  Do not share an administrative account.

    2.  **Minimize the number of Tier 0 privileged administrators**.  Because each administrator must use a PAW, reducing the number of administrators reduces the number of PAWs required to support them and the associated costs. The lower count of administrators also results in lower exposure of these privileges and associated risks. While it is possible for administrators in one location to share a PAW, administrators in separate physical locations will require separate PAWs.

    3.  **Acquire hardware from a trusted supplier that meets all technical requirements**. Microsoft recommends acquiring hardware that meets the technical requirements in the article [Protect domain credentials with Credential Guard](https://technet.microsoft.com/en-us/library/mt483740%28v=vs.85%29.aspx).

        > [!NOTE]
        > PAW installed on hardware without these capabilities can provide significant protections, but advanced security features such as Credential Guard and Device Guard will not be available.  Credential Guard and Device Guard are not required for Phase 1 deployment, but are strongly recommended as part of Phase 3 (advanced hardening).

        Ensure that the hardware used for the PAW is sourced from a manufacturer and supplier whose security practices are trusted by the organization. This is an application of the clean source principle to supply chain security.

        > [!NOTE]
        > For more background on the importance of supply chain security, visit [this site](https://www.microsoft.com/security/cybersecurity/).

    4.  Acquire and validate the required Windows 10 Enterprise Edition and application software. Obtain the software required for PAW and validate it using the guidance in [Clean Source for installation media](http://aka.ms/cleansource).

        -   Windows 10 Enterprise Edition

        -   [Remote Server Administration Tools](https://www.microsoft.com/en-us/download/details.aspx?id=45520.) for Windows 10

        -   Windows 10 [Security Baselines](http://aka.ms/win10baselines)

        -   [Enhanced Mitigation Experience Toolkit (EMET)](https://www.microsoft.com/en-us/download/details.aspx?id=49166)

            > [!NOTE]
            > Microsoft publishes MD5 hashes for all operating systems and applications on MSDN, but not all software vendors provide similar documentation.  In those cases, other strategies will be required.  For additional information on validating software, please refer to [Clean Source](http://aka.ms/cleansource) for installation media.

    5.  **Ensure you have WSUS server available on the intranet**. You will need a WSUS server on the intranet to download and install updates for PAW. This WSUS server should be configured to automatically approve all security updates for Windows 10 or an administrative personnel should have responsibility and accountability to rapidly approve software updates.

        > [!NOTE]
        > For more information, see the "Automatically Approve Updates for Installation" section in the [Approving Updates guidance](https://technet.microsoft.com/en-us/library/cc708458(v=ws.10).aspx).

2.  Deploy the Admin OU Framework to host the PAWs

    1.  Download the PAW script library from [TechNet Gallery](http://aka.ms/PAWmedia)

        > [!NOTE]
        > Download all of the files and save them to the same directory, and run them in the order specified below.  Create-PAWGroups depends on the OU structure created by Create-PAWOUs, and Set-PAWOUDelegation depends on the groups created by Create-PAWGroups.
        > Do not modify any of the scripts or the comma-separated value (CSV) file.

    2.  **Run the Create-PAWOUs.ps1 script**.  This script will create the new organizational unit (OU) structure in Active Directory, and block GPO inheritance on the new OUs as appropriate.

    3.  **Run the Create-PAWGroups.ps1 script**.  This script will create the new global security groups in the appropriate OUs.

        > [!NOTE]
        > While this script will create the new security groups, it will not populate them automatically.

    4.  **Run the Set-PAWOUDelegation.ps1 script**.  This script will assign permissions to the new OUs to the appropriate groups.

3.  **Move Tier 0 accounts to the Admin\Tier 0\Accounts OU**. Move each account that is a member of the Domain Admin, Enterprise Admin, or Tier 0 equivalent groups (including nested membership) to this OU. If your organization has your own groups that are added to these groups, you should move these to the Admin\Tier 0\Groups OU.

    > [!NOTE]
    > For more information on which groups are Tier 0, see "Tier 0 Equivalency" in [Securing Privileged Access Reference Material](../securing-privileged-access/securing-privileged-access-reference-material.md).

4.  Add the appropriate members to the relevant groups

    1.  **PAW Users** - Add the Tier 0 administrators with Domain or Enterprise Admin groups that you identified in Step 1 of Phase 1.

    2.  **PAW Maintenance** - Add at least one account that will be used for PAW maintenance and troubleshooting tasks. The PAW Maintenance Account(s) will be used only rarely.

        > [!NOTE]
        > Do not add the same user account or group to both PAW Users and PAW Maintenance.  The PAW security model is based partly on the assumption that the PAW user account has privileged rights on managed systems or over the PAW itself, but not both.
        >
        > -   This is important for building good administrative practices and habits in Phase 1.
        > -   This is critically important for Phase 2 and beyond to prevent escalation of privilege through PAW as PAWs being to span Tiers.
        >
        > Ideally, no personnel are assigned to duties at multiple tiers to enforce the principle of segregation of duties, but Microsoft recognizes that many organizations may have limited staff (or other organizational requirements) that don't allow for this full segregation. In these cases, the same personnel may be assigned to both roles, but should not use the same account for these functions.

5.  **Create "PAW Configuration - Computer" group policy object (GPO) and link to the Tier 0 Devices OU** ("Devices" under Tier 0\Admin).  In this section, you will create a new "PAW Configuration - Computer" GPO which provide specific protections for these PAWs.

    > [!NOTE]
    > **Do not add these settings to the Default Domain Policy**.  Doing so will potentially impact operations on your entire Active Directory environment.  Only configure these settings in the newly-created GPOs described here, and only apply them to the PAW OU.

    1.  **PAW Maintenance Access** - this setting will set the membership of specific privileged groups on the PAWs to a specific set of users. Go to *Computer Configuration\Preferences\Control Panel Settings\Local Users* and Groups and follow the steps below:

        1.  Click **New** and click **Local Group**

        2.  Select the **Update** action, and select "Administrators (built-in)" (do not use the Browse button to select the domain group Administrators).

        3.  Select the **Delete all member users** and **Delete all member groups** check boxes

        4.  Add PAW Maintenance (pawmaint) and Administrator (again, do not use the Browse button to select Administrator).

            > [!NOTE]
            > Do not add the PAW Users group to the membership list for the local Administrators group.  To ensure that PAW Users cannot accidentally or deliberately modify the security settings of the PAW itself, they should not be members of the local Administrators groups.

            For more information on using Group Policy Preferences to modify group membership, please refer to the TechNet article [Configure a Local Group Item](https://technet.microsoft.com/en-us/library/cc732525.aspx).

    2.  **Restrict Local Group Membership** - this setting will ensure that the membership of local admin groups on the workstation is always empty

        1.  Go to Computer Configuration\Preferences\Control Panel Settings\Local Users and Groups and follow the steps below:

            1.  Click **New** and click **Local Group**

            2.  Select the **Update** action, and select "Backup Operators (built-in)" (do not use the Browse button to select the domain group Backup Operators).

            3.  Select the **Delete all member users** and **Delete all member groups** check boxes.

            4.  Do not add any members to the group.  Simply click **OK**.  By assigning an empty list, group policy will automatically remove all members and ensure a blank membership list each time group policy is refreshed.

        2.  Complete the above steps for the following additional groups:

            -   Криптографические операторы

            -   Hyper-V Administrators

            -   Операторы настройки сети

            -   Power Users

            -   Remote Desktop Users

            -   Replicators

        3.  PAW Logon Restrictions - this setting will limit the accounts which can log onto the PAW. Follow the steps below to configure this setting:

            1.  Go to Computer Configuration\Policies\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Allow log on locally.

            2.  Select Define these policy settings and add "PAW Users" and Administrators (again, do not use the Browse button to select Administrators).

        4.  **Block Inbound Network Traffic** - This setting will ensure that no unsolicited inbound network traffic is allowed to the PAW. Follow the steps below to configure this setting:

            1.  Go to Computer Configuration\Policies\Windows Settings\Security Settings\Windows Firewall with Advanced Security\Windows Firewall with Advanced Security and follow the steps below:

                1.  Right click on Windows Firewall with Advanced Security and select **Import policy**.

                2.  Click **Yes** to accept that this will overwrite any existing firewall policies.

                3.  Browse to PAWFirewall.wfw and select **Open**.

                4.  Нажмите кнопку **ОК**.

                    > [!NOTE]
                    > You may add addresses or subnets which must reach the PAW with unsolicited traffic at this point (e.g. security scanning or management software.
                    > The settings in the WFW file will enable the firewall in "Block - Default" mode for all firewall profiles, turn off rule merging and enable logging of both dropped and successful packets. These settings will block unsolicitied traffic while still allowing bidirectional communication on connections initiated from the PAW, prevent users with local administrative access from creating local firewall rules that would override the GPO settings and ensure that traffic in and out of the PAW is logged.
                    > **Opening up this firewall will expand the attack surface for the PAW and increase security risk. Before adding any addresses, consult the Managing and Operating PAW section in this guidance**.

        5.  **Configure Windows Update for WSUS** - follow the steps below to change the settings to configure Windows Update for the PAWs:

            1.  Go to Computer Configuration\Policies\Administrative Templates\Windows Components\Windows Updates and follow the steps below:

                1.  Enable the **Configure Automatic Updates policy**.

                2.  Выберите параметр **4 - автоматически загружать и устанавливать по заданному расписанию**.

                3.  Измените параметр **день установки по расписанию** для **0 — ежедневно** и параметр **запланированное время установки** с требованиями вашей организации.

                4.  Включите параметр **указать размещение службы обновлений Майкрософт в интрасети** политики, и укажите оба параметра URL-адреса сервера ESAE WSUS.

        6.  Установите связь «ПРИВИЛЕГИРОВАННЫМ конфигурации — компьютер» объект групповой Политики следующим образом:

            |Политики|Расположение связи|
            |-----|---------|
            |Настройка привилегированным ДОСТУПОМ — компьютер |Администратор\уровень 0\устройства|

6.  **Создайте «ПРИВИЛЕГИРОВАННЫМ конфигурация — пользователь» объект групповой политики (GPO) и свяжите Подразделения учетные записи уровня 0 («учетные записи» уровня 0\устройства)**.  В этом разделе вы создадите «ПРИВИЛЕГИРОВАННЫМ конфигурации — пользователь» групповой Политики, обеспечивающий защиту для этих привилегированным доступом.

    > [!NOTE]
    > Не добавляйте эти параметры в политику домена по умолчанию

    1.  **Блокировать Просмотр ресурсов Интернета** -, чтобы предотвратить случайный вход в Интернет, будет задан адрес прокси-сервера из петлевого адреса (127.0.0.1).

        1.  Выберите windows\реестр Configuration\Preferences\Windows. Щелкните правой кнопкой мыши реестра, выберите **New** \> **элемента реестра** и настройте следующие параметры:

            1.  Действие: замена

            2.  Куст: HKEY_CURRENT_USER

            3.  Путь к разделу: Программное Обеспечение\майкрософт\windows\текущая_версия\параметры браузера

            4.  Имя значения: ProxyEnable

                > [!NOTE]
                > Не устанавливайте флажок слева от имени значения по умолчанию.

            5.  Тип значения: REG_DWORD

            6.  Значение данных: 1

                1.  .  Щелкните вкладки "Общие" и выберите **удалить этот элемент, если он больше не применяется**.

                2.  На вкладке "Общие" выберите **нацеливание на уровне элемента** и нажмите кнопку **нацеливание**.

                3.  Нажмите кнопку **новый элемент** и выберите **группы безопасности**.

                4.  Выберите кнопку «...» и перейдите к группе пользователей с привилегированным ДОСТУПОМ.

                5.  Нажмите кнопку **новый элемент** и выберите **группы безопасности**.

                6.  Нажмите кнопку «...» и найдите **Администраторы облачных служб** группы.

                7.  Щелкните **Администраторы облачных служб** элемент и нажмите кнопку **параметры элемента**.

                8.  Выберите **не**.

                9. Нажмите кнопку **ОК** в окне определения цели.

            7.  Нажмите кнопку **ОК** чтобы завершить настройку групповой политики ProxyServer

        2.  Выберите windows\реестр Configuration\Preferences\Windows. Щелкните правой кнопкой мыши реестра, выберите **New** \> **элемента реестра** и настройте следующие параметры:

            -   Действие: замена

            -   Куст: HKEY_CURRENT_USER

            -   Путь к разделу: Программное Обеспечение\майкрософт\windows\текущая_версия\параметры браузера

            -   Имя значения: ProxyServer

                > [!NOTE]
                > Не устанавливайте флажок слева от имени значения по умолчанию.

            -   Тип значения: REG_SZ

            -   Значение данных: 127.0.0.1:80

                1.  Нажмите кнопку **распространенных** и выберите **удалить этот элемент, если он больше не применяется**.

                2.  На **распространенных** выберите **нацеливание на уровне элемента** и нажмите кнопку **нацеливание**.

                3.  Нажмите кнопку **новый элемент** и группы выберите безопасности.

                4.  Нажмите кнопку «...» и добавьте группу пользователей с привилегированным ДОСТУПОМ.

                5.  Нажмите кнопку **новый элемент** и группы выберите безопасности.

                6.  Нажмите кнопку «...» и найдите **Администраторы облачных служб** группы.

                7.  Щелкните **Администраторы облачных служб** элемент и нажмите кнопку **параметры элемента**.

                8.  Выберите **не**.

                9. Нажмите кнопку **ОК** в окне определения цели.

        3.  Нажмите кнопку **ОК** чтобы завершить настройку групповой политики ProxyServer

    2.  Выберите пользователя Конфигурация компьютера\Политики\Административные шаблоны\Компоненты Windows\Internet Explorer и включите параметры ниже. Эти параметры не администраторы переопределение параметров прокси-сервера вручную.

        1.  Включить **отключить изменение автоматической настройки** параметры.

        2.  Включить **запретить изменение параметров прокси-сервера**.

7.  **Ограничьте вход в узлы нижнего уровня администраторов**.  В этом разделе мы настроим групповые политики для предотвращения входа в узлы нижнего уровня привилегированных учетных записей администратора.

    1.  Создайте **ограничение входа в рабочую станцию** объекты групповой Политики — этот параметр ограничит уровня 0 и учетные записи администраторов уровня 1 на стандартные рабочие станции.  Этот объект групповой Политики должен быть связан с Подразделение верхнего уровня «Рабочих станций» и имеют следующие параметры.

        - (i) на компьютере Конфигурация компьютера\Политики\Параметры Windows\Параметры безопасности\Локальные политики\Назначение прав пользователя\отказать во входе в качестве пакетного задания, выберите **определить следующие параметры политики** и добавьте группы уровня 0 и 1 уровня:

            **Группы, чтобы добавить в параметры политики:**

            Администраторы предприятия

            Администраторы домена

            Администраторы схемы

            Домен\администраторы

            Операторы учетных записей

            Операторы резервного копирования

            Операторы печати

            Операторы сервера

            Контроллеры домена

            Read-Only Контроллеры домена

            Владельцы-создатели групповой политики

            Криптографические операторы

            > [!NOTE]
            > Примечание: Эквивалентность уровня 0 для получения дополнительных сведений см. встроенных группах уровня 0.

            Другие делегированные группы

            > [!NOTE]
            > Примечание: Любой группах с активным доступом уровня 0, разделе эквивалентность уровня 0 для получения дополнительных сведений.

            Администраторов уровня 1

            > [!NOTE]
            > Примечание: Эта группа создана ранее на этапе 1

        - (ii) на компьютере Конфигурация компьютера\Политики\Параметры Windows\Параметры безопасности\Локальные политики\Назначение прав пользователя\отказать во входе в качестве службы, выберите **определить следующие параметры политики** и добавьте группы уровня 0 и 1 уровня:

            **Группы, чтобы добавить в параметры политики:**

            Администраторы предприятия

            Администраторы домена

            Администраторы схемы

            Домен\администраторы

            Операторы учетных записей

            Операторы резервного копирования

            Операторы печати

            Операторы сервера

            Контроллеры домена

            Read-Only Контроллеры домена

            Владельцы-создатели групповой политики

            Криптографические операторы

            > [!NOTE]
            > Примечание: Эквивалентность уровня 0 для получения дополнительных сведений см. встроенных группах уровня 0.

            Другие делегированные группы

            > [!NOTE]
            > Примечание: Любой группах с активным доступом уровня 0, разделе эквивалентность уровня 0 для получения дополнительных сведений.

            Администраторы уровня 1

            > [!NOTE]
            > Примечание: Эта группа создана ранее на этапе 1

    2.  Создайте **ограничение входа на сервер** объекты групповой Политики — этот параметр ограничит учетные записи администраторов уровня 0 на серверах уровня 1.  Этот объект групповой Политики должен быть связан с Подразделение верхнего уровня «Серверы уровня 1» и имеют следующие параметры.

        -   (i) на компьютере Конфигурация компьютера\Политики\Параметры Windows\Параметры безопасности\Локальные политики\Назначение прав пользователя\отказать во входе в качестве пакетного задания, выберите **определить следующие параметры политики** и добавьте группы уровня 0:

            **Группы, чтобы добавить в параметры политики:**

            Администраторы предприятия

            Администраторы домена

            Администраторы схемы

            Домен\администраторы

            Операторы учетных записей

            Операторы резервного копирования

            Операторы печати

            Операторы сервера

            Контроллеры домена

            Read-Only Контроллеры домена

            Владельцы-создатели групповой политики

            Криптографические операторы

            > [!NOTE]
            > Примечание: Эквивалентность уровня 0 для получения дополнительных сведений см. встроенных группах уровня 0.

            Другие делегированные группы

            > [!NOTE]
            > Примечание: Любой группах с активным доступом уровня 0, разделе эквивалентность уровня 0 для получения дополнительных сведений.

        -   (ii) на компьютере Конфигурация компьютера\Политики\Параметры Windows\Параметры безопасности\Локальные политики\Назначение прав пользователя\отказать во входе в качестве службы, выберите **определить следующие параметры политики** и добавьте группы уровня 0:

            **Группы, чтобы добавить в параметры политики:**

            Администраторы предприятия

            Администраторы домена

            Администраторы схемы

            Домен\администраторы

            Операторы учетных записей

            Операторы резервного копирования

            Операторы печати

            Операторы сервера

            Контроллеры домена

            Read-Only Контроллеры домена

            Владельцы-создатели групповой политики

            Криптографические операторы

            > [!NOTE]
            > Примечание: Эквивалентность уровня 0 для получения дополнительных сведений см. встроенных группах уровня 0.

            Другие делегированные группы

            > [!NOTE]
            > Примечание: Любой группах с активным доступом уровня 0, разделе эквивалентность уровня 0 для получения дополнительных сведений.

        -   (iii) компьютера Конфигурация компьютера\Политики\Параметры Windows\Параметры безопасности\Локальные политики\Назначение прав пользователя\отказать во входе в систему локально, выберите **определить следующие параметры политики** и добавьте группы уровня 0:

            **Группы, чтобы добавить в параметры политики:**

            Администраторы предприятия

            Администраторы домена

            Администраторы схемы

            Операторы учетных записей

            Операторы резервного копирования

            Операторы печати

            Операторы сервера

            Контроллеры домена

            Read-Only Контроллеры домена

            Владельцы-создатели групповой политики

            Криптографические операторы

            > [!NOTE]
            > Примечание: Эквивалентность уровня 0 для получения дополнительных сведений см. встроенных группах уровня 0.

            Другие делегированные группы

            > [!NOTE]
            > Примечание: Любой группах с активным доступом уровня 0, разделе эквивалентность уровня 0 для получения дополнительных сведений.

8.  Развертывание вашей привилегированным доступом

    > [!NOTE]
    > Убедитесь, что рабочая СТАНЦИЯ не подключена к сети во время сборки операционной системы.

    1.  Установите Windows 10, чистый источник установочного носителя, полученный ранее.

        > [!NOTE]
        > Вы можете использовать Microsoft Deployment Toolkit (MDT) или другую систему автоматизированного развертывания образов для автоматизации развертывания привилегированным ДОСТУПОМ, но необходимо убедиться, что процесс построения совпадать с привилегированным ДОСТУПОМ. Злоумышленники ищут именно корпоративные образы и системы развертывания (включая образы ISO, пакеты развертывания, т. д.) качестве механизмов сохранения, не будут использовать существующие системы развертывания или образы.
        >
        > При автоматизации развертывания привилегированным ДОСТУПОМ, необходимо выполнить следующее:
        >
        > -   Создайте систему с помощью установочного носителя, проверенных на соответствие указаниям в [чистоты источника для установочных носителей](http://aka.ms/cleansource).
        > -   Убедитесь, что система автоматизированного развертывания отключена от сети во время сборки операционной системы.

    2.  Задайте уникальный сложный пароль для учетной записи локального администратора.  Не используйте пароль, использованный для любой другой учетной записи в среде.

        > [!NOTE]
        > Корпорация Майкрософт рекомендует использовать [локального администратора Password Solution (LAPS)](https://www.microsoft.com/en-us/download/details.aspx?id=46899) для управления паролями локальных администраторов для всех рабочих станций, включая привилегированным доступом.  При использовании LAPS, убедитесь, что вы предоставлять только те группы ПРИВИЛЕГИРОВАННЫМ доступом, обслуживание право на чтение паролей, управляемых LAPS для привилегированным доступом.

    3.  Установка удаленного средства администрирования сервера для Windows 10 с помощью чистый источник установочного носителя.

    4.  Установите Enhanced Mitigation Experience Toolkit (EMET) с помощью чистый источник установочного носителя.

        > [!NOTE]
        > Обратите внимание, что во время последнего обновления этого руководства набор средств EMET 5.5 находился на стадии бета-тестирования.  Так как это первая версия, поддерживаемая в Windows 10, она включена в независимо от его состояния бета-версии.  Если установка бета-версии программного обеспечения на привилегированным ДОСТУПОМ превышает допустимый уровень риска, этот шаг можно пропустить на данный момент.

    5.  Подключите привилегированным ДОСТУПОМ к сети.  Убедитесь, что привилегированным ДОСТУПОМ может подключиться хотя бы один контроллер домена (DC).

    6.  Используя учетную запись, которая является членом группы ПРИВИЛЕГИРОВАННЫМ доступом, обслуживание, выполните следующую команду PowerShell с привилегированным ДОСТУПОМ только что созданный Чтобы присоединить ее к домену в соответствующем Подразделении:

        `Add-Computer -DomainName Fabrikam -OUPath "OU=Devices,OU=Tier 0,OU=Admin,DC=fabrikam,DC=com"`

        Замените ссылки на *Fabrikam* именем своего домена соответствующим образом.  Если имя домена распространяется на несколько уровней (например child.fabrikam.com), добавьте дополнительные имена с «DC = «идентификатор в порядке, в котором они отображаются в полное доменное имя домена.

        > [!NOTE]
        > Если вы развернули [административный лес ESAE](http://aka.ms/esae) (для администраторов уровня 0 на этапе 1) или [Microsoft Identity Manager (MIM) сфере управления привилегированным доступом (PAM)](http://aka.ms/mimpamdeploy) (для администраторов уровня 1 и 2 на этапе 2), присоедините рабочую станцию с ПРИВИЛЕГИРОВАННЫМ к домену в этой среде, а не к рабочему домену.

    7.  Примените все критические и важные обновления Windows перед установкой любого другого программного обеспечения (включая средства администрирования, агенты и т. д.).

    8.  Настройте принудительное применение групповой политики.

        1.  Откройте командную строку с повышенными привилегиями и введите следующую команду:

            `Gpupdate /force /sync`

        2.  Перезагрузите компьютер

    9. **(Необязательно) **Установите дополнительные средства, необходимые для администраторов Active Directory. Установите любые средства и скрипты, необходимые для выполнения рабочих обязанностей. Убедитесь, что Оцените риск раскрытия учетных данных на целевых компьютерах с помощью любого инструмента, прежде чем добавлять его с привилегированным ДОСТУПОМ. Доступ к [на этой странице](http://aka.ms/logontypes) Чтобы получить дополнительные сведения об оценке средств администрирования и способов подключения для риска раскрытия учетных данных. Получите все установочные носители, используя рекомендации в [чистоты источника для установочных носителей](http://aka.ms/cleansource).

        > [!NOTE]
        > При использовании сервера перехода в качестве центрального расположения для этих средств можно с ними упрощается, даже если он не выполняет роль уровня безопасности.

    10. **(Необязательно) **Загрузить и установить программное обеспечение для удаленного доступа. Если администраторы будут использовать рабочую станцию с ПРИВИЛЕГИРОВАННЫМ удаленного администрирования, установите программное обеспечение удаленного доступа, следуя указаниям по безопасности от поставщика решения для удаленного доступа. Убедитесь, что получите все установочные носители в соответствии с указаниями в принципе чистоты источника для установочных носителей.

        > [!NOTE]
        > Тщательно продумайте все риски связанные с удаленным доступом через привилегированным ДОСТУПОМ.  Мобильных рабочая станция ПОМОГАЕТ реализовать множество важных сценариев, включая работу из дома, программное обеспечение для удаленного доступа может быть уязвимым к атакам и использоваться для нарушения безопасности привилегированным ДОСТУПОМ.

    11. Для проверки целостности системы привилегированным ДОСТУПОМ, настроены все соответствующие параметры в месте, как описано ниже:

        1.  Убедитесь, что с привилегированным ДОСТУПОМ применяются только групповые политики привилегированным доступом

            1.  Откройте командную строку с повышенными привилегиями и введите следующую команду:

                `Gpresult /scope computer /r`

            2.  Просмотрите полученный список и убедитесь, что только групповой политики, которые отображаются используются те, что вы создали выше.

        2.  Убедитесь, что нет дополнительные учетные записи пользователей являются членами привилегированных групп на привилегированным ДОСТУПОМ, как описано ниже:

            1.  Откройте **изменение локальных пользователей и групп** (lusrmgr.msc), выберите **группы**и убедитесь, что только члены локальной группы администраторов учетную запись локального администратора и ПРИВИЛЕГИРОВАННЫМ доступом, обслуживание глобальной группы безопасности.

                > [!NOTE]
                > Группу пользователей с привилегированным ДОСТУПОМ следует не является членом локальной группы администраторов.  Должны входить только учетную запись локального администратора и ПРИВИЛЕГИРОВАННЫМ доступом, обслуживание глобальной группы безопасности (и ПРИВИЛЕГИРОВАННЫМ не должна содержать пользователи членом Эта глобальная группа либо).

            2.  Также с помощью **изменение локальных пользователей и групп**, убедитесь, что следующие группы пусты:

                -   Операторы резервного копирования

                -   Криптографические операторы

                -   Hyper-V Administrators

                -   Операторы настройки сети

                -   Power Users

                -   Remote Desktop Users

                -   Replicators

    12. **(Необязательно) **Если ваша организация использует сведения о безопасности и событие решение для управления (SIEM), убедитесь, что рабочая СТАНЦИЯ [настроено перенаправление событий в систему с использованием перенаправления событий Windows (WEF)](http://blogs.technet.com/b/jepayne/archive/2015/11/24/monitoring-what-matters-windows-event-forwarding-for-everyone-even-if-you-already-have-a-siem.aspx) или будет зарегистрирована в решении, чтобы обеспечить SIEM активную передачу событий и сведений с привилегированным ДОСТУПОМ.  Сведения об этой операции зависят от решения SIEM.

        > [!NOTE]
        > Если решению SIEM требуется агент, выполняющийся в качестве системной или локальной учетной записи администрирования на привилегированным доступом, убедитесь, что решений Siem при управлении тот же уровень доверия, контроллеры домена и систем удостоверений.

    13. **(Необязательно) **Если для управления паролем учетной записи локального администратора на вашем привилегированным ДОСТУПОМ развернуто решение LAPS, убедитесь в успешной регистрации пароля.

        -   Используя учетную запись с разрешениями на чтение паролей, управляемых LAPS, откройте **Active Directory-пользователи и компьютеры** (dsa.msc).  Убедитесь, что включена дополнительные компоненты и щелкните правой кнопкой мыши соответствующий объект-компьютер.  Выберите вкладку "Редактор атрибутов" и убедитесь, что значения параметра mssvsadmpwd указан действующий пароль.

#### <a name="phase-2---extend-paw-to-all-administrators"></a>Этап 2 - расширить привилегированным ДОСТУПОМ всем администраторам
Область: Все пользователи с правами администратора на критически важные приложения и зависимости.  Это должен быть по крайней мере администраторов серверов приложений, работоспособности и безопасности, мониторинг решения, решений для виртуализации, системы хранения и сетевые устройства.

> [!NOTE]
> В указаниях на этом этапе предполагается, что этап 1 завершен полностью.  Не приступайте к выполнению этапа 2 пока не будут выполнены все действия, описанные на этапе 1.

Как только вы подтвердите, что все действия выполнены, выполните следующие действия, чтобы завершить этап 2.

1.  **(Рекомендуется) **Включить **RestrictedAdmin** режим — включите эту функцию на существующих серверах и рабочих станциях, а затем настройте принудительное использование этой функции. Эта функция требует, чтобы целевые серверы работать под управлением Windows Server 2008 R2 или более поздней версии и рабочие станции — под управлением Windows 7 или более поздней версии.

    1.  Включить **RestrictedAdmin** режиме на серверах и рабочих станциях, следуя указаниям на этой [страницы](http://aka.ms/rdpra).

        > [!NOTE]
        > Прежде чем включать эту функцию для серверах, подключенных к Интернету, следует учитывать риск злоумышленники могут пройти проверку подлинности на этих серверах с помощью хэша украденного пароля.

    2.  Создайте объект групповой политики «Требуется RestrictedAdmin — компьютер» (GPO). В этом разделе создается объект групповой Политики, который обеспечивает принудительное использование /RestrictedAdmin переключение для исходящих подключений удаленного рабочего стола и защиту учетных данных от кражи учетных данных в целевой системе

        -   Выберите Конфигурация компьютера\Политики\Административные шаблоны\система\передача учетных данных\ограничить делегирование учетных данных удаленным серверам и установите **включено**.

    3.  Ссылка **RestrictedAdmin** требуется - компьютере соответствующими уровня 1 и/или уровня 2 устройства, используя следующие параметры политики:

        Настройка привилегированным ДОСТУПОМ — компьютер

        -> Расположение связи: администратор\уровень 0\устройства (существующая)

        ПРИВИЛЕГИРОВАННЫМ конфигурации - пользователя

        -> Расположение связи: администратор\уровень 0\учетные записи

        Требуется RestrictedAdmin — компьютер

        -> администратор\уровень 1\устройства или -> администратор\уровень 2\устройства подразделения (оба являются обязательными)

        > [!NOTE]
        > Это необязательно для систем уровня 0 как они уже полный контроль над всеми ресурсами в среде.

2.  Переместите объекты уровня 1 в соответствующие подразделения.

    1.  Переместите группы уровня 1 для администратор\уровень 1\ГРУППЫ. Найдите все группы, которые предоставляют следующие административные права и переместите их в это Подразделение.

        -   Права локального администратора на несколько серверов

        -   Административный доступ к облачным службам

        -   Административный доступ к корпоративным приложениям.

    2.  Переместите учетные записи уровня 1 в Подразделение 1\Accounts администратор\уровень. Переместите каждую учетную запись, которая является членом этих групп уровня 1 (включая вложенные элементы) в это Подразделение.

3.  Add the appropriate members to the relevant groups

    -   **Администраторы уровня 1** -эта группа будет содержать администраторов уровня 1 разрешений на вход в узлы уровня 2. Добавьте все административные группы уровня 1 с правами администратора на серверы или службы Интернета.

        > [!NOTE]
        > Если администраторы управляют ресурсами на нескольких уровнях, необходимо создать отдельную учетную запись администратора каждого уровня.

4.  Включите Credential Guard, чтобы снизить риск кражи и повторного использования.  Credential Guard — это новая функция Windows 10, ограничивающий доступ приложений к учетным данным, предотвращая атак кражи учетных данных (включая Pass--Hash).  Credential Guard абсолютно прозрачно для пользователя и требует минимум времени и усилий.  Дополнительные сведения о Credential Guard, включая указания по развертыванию и требования к оборудованию, см. в статье [защиты учетных данных домена с помощью Credential Guard](https://technet.microsoft.com/en-us/library/mt483740%28v=vs.85%29.aspx).

    > [!NOTE]
    > Для настройки и использования Credential Guard, необходимо включить Device Guard.  Тем не менее вам не нужно настраивать другие средства защиты Device Guard для использования Credential Guard.

5.  **(Необязательно) **Включить подключение к облачным службам. Этот шаг позволяет настроить управление облачными службами, например Azure и Office 365 с соответствующим уровнем безопасности. Этот шаг также является обязательным для Microsoft Intune для управления привилегированным доступом.

    > [!NOTE]
    > Этот шаг можно пропустите, если нет подключения к облачным службам с помощью Intune необходим для администрирования облачных служб или управления.

    Эти шаги будут ограничить связь через Интернет для только с авторизованными облачными службами (но не доступа к Интернету) и добавлены средства защиты для браузеров и других приложений, которые будут обрабатывать содержимое из Интернета. Эти привилегированным доступом для администрирования никогда нельзя использовать для выполнения задач обычного пользователя, например обмен данными в Интернете и рабочие задания.

    Возможность подключения к сети с привилегированным ДОСТУПОМ служб выполните следующие действия:

    1.  Настройте привилегированным ДОСТУПОМ, чтобы разрешить только авторизованного назначения в Интернете.  При расширении развертывания привилегированным ДОСТУПОМ для обеспечения администрирования облака необходимо разрешить доступ к авторизованным службам и отфильтровать доступ из открытых ресурсов в Интернете, где легче риск атаки на администраторов.

        1.  Создание **Администраторы облачных служб** группы и добавьте все учетные записи, требующие доступа к облачным службам в Интернете.

        2.  Загрузите рабочую станцию с ПРИВИЛЕГИРОВАННЫМ *proxy.pac* файл из [коллекции TechNet](http://aka.ms/pawmedia) и опубликуйте его на внутреннем веб-сайте.

            > [!NOTE]
            > Вам потребуется обновить *proxy.pac* файл после загрузки, чтобы убедиться, что это последняя актуальная версия.  
            > Корпорация Майкрософт публикует все текущего Office 365 и Azure URL-адреса в офисе [центр поддержки](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US).
            >
            > Может потребоваться добавить другие допустимые назначения в Интернете, чтобы добавить в этот список для других поставщиков решений IaaS, но не добавляйте производительность, развлекательных, новостных или поисковых сайтов в этот список.
            >
            > Кроме того, может потребоваться настроить PAC-файл в соответствии с допустимым прокси-адрес для использования для этих адресов.

            > [!NOTE]
            > Можно также ограничить доступ с привилегированным ДОСТУПОМ, а также с помощью веб-прокси для всестороннюю защиты. Не рекомендуется использовать это само по себе без PAC-файл как только будет ограничивать доступ для рабочей станции с привилегированным при подключении к корпоративной сети.

            Данные инструкции предполагают, что вы используете Internet Explorer (или Microsoft Edge) для администрирования Office 365, Azure и других облачных служб. Корпорация Майкрософт рекомендует настроить аналогичные ограничения для всех сторонних браузеров, требуемых для администрирования. Веб-браузеры на рабочей станции с привилегированным должен использоваться только для администрирования облачных служб и никогда не для просмотра общих веб-страниц.

        3.  После настройки *proxy.pac* файл, обновите конфигурацию ПРИВИЛЕГИРОВАННЫМ - групповой Политики пользователя.

            1.  Выберите windows\реестр Configuration\Preferences\Windows. Щелкните правой кнопкой мыши реестра, выберите **New** \> **элемента реестра** и настройте следующие параметры:

                1.  Действие: замена

                2.  Куст реестра: CURRENT_USER HKEY_

                3.  Путь к разделу: Программное Обеспечение\майкрософт\windows\текущая_версия\параметры браузера

                4.  Имя значения: AutoConfigUrl

                    > [!NOTE]
                    > Не устанавливайте **по умолчанию** флажка слева от имени значения.

                5.  Тип значения: REG_SZ

                6.  Значение данных: Введите полный URL-адрес для *proxy.pac* файла, включая http:// и именем файла — например http://proxy.fabrikam.com/proxy.pac.  URL-адрес также может быть однокомпонентное URL-адрес — например, http://proxy/proxy.pac

                    > [!NOTE]
                    > PAC-файл также может размещаться на файловом ресурсе, с помощью синтаксиса file://server.fabrikan.com/share/proxy.pac, но для этого требуется разрешить использование протокола file://. В разделе «Примечание: File://-based прокси-сервера сценариев устаревшим» это [Общие сведения о конфигурации веб-прокси](http://blogs.msdn.com/b/ieinternals/archive/2013/10/11/web-proxy-configuration-and-ie11-changes.aspx) блог Дополнительные сведения о настройке требуемого значения регистра.

                7.  Нажмите кнопку **распространенных** и выберите **удалить этот элемент, если он больше не применяется**.

                8.  На **распространенных** выберите **нацеливание на уровне элемента** и нажмите кнопку **нацеливание**.

                9. Нажмите кнопку **новый элемент** и выберите **группы безопасности**.

                10. Нажмите кнопку «...» и найдите **Администраторы облачных служб** группы.

                11. Нажмите кнопку **новый элемент** и выберите **группы безопасности**.

                12. Нажмите кнопку «...» и найдите **ПРИВИЛЕГИРОВАННЫМ пользователям** группы.

                13. Щелкните **ПРИВИЛЕГИРОВАННЫМ пользователям** элемент и нажмите кнопку **параметры элемента**.

                14. Выберите **не**.

                15. Нажмите кнопку **ОК** в окне определения цели.

                16. Нажмите кнопку **ОК** для завершения **AutoConfigUrl** параметр групповой политики.

    2.  Примените базовые конфигурации безопасности Windows 10 и ссылку доступа к облачной службе базовые параметры безопасности для Windows и для облачной службы доступа (при необходимости) к соответствующим подразделениям, выполнив следующие действия:

        1.  Извлеките содержимое файла ZIP базовые параметры безопасности Windows 10.

        2.  Эти объекты, создает [Импорт политики](https://technet.microsoft.com/en-us/library/cc753786.aspx) параметры, и [ссылку](https://technet.microsoft.com/en-us/library/cc732979.aspx) в этой таблице. Привяжите политики к расположениям и убедитесь в том порядке, приведенном в таблице (приоритетные записи в таблице ниже следует применить позже):

            **Политики:**

            |||
            |-|-|
            |CM Windows 10 — безопасность домена|Н/д — не выполнять привязку сейчас|
            |SCM Windows 10 TH2 — компьютер|Администратор\уровень 0\устройства|
            ||Администратор\уровень 1\устройства|
            ||Администратор\уровень 2\устройства|
            |SCM Windows 10 TH2 — BitLocker|Администратор\уровень 0\устройства|
            ||Администратор\уровень 1\устройства|
            ||Администратор\уровень 2\устройства|
            |SCM Windows 10 — Credential Guard|Администратор\уровень 0\устройства|
            ||Администратор\уровень 1\устройства|
            ||Администратор\уровень 2\устройства|
            |SCM Internet Explorer — компьютер|Администратор\уровень 0\устройства|
            ||Администратор\уровень 1\устройства|
            ||Администратор\уровень 2\устройства|
            |Настройка привилегированным ДОСТУПОМ — компьютер|Администратор\уровень 0\устройства (существующая)|
            ||Администратор\уровень 1\устройства (новая связь)|
            ||Администратор\уровень 2\устройства (новая связь)|
            |Требуется RestrictedAdmin — компьютер|Администратор\уровень 0\устройства|
            ||Администратор\уровень 1\устройства|
            ||Администратор\уровень 2\устройства|
            |SCM Windows 10 — пользователь|Администратор\уровень 0\устройства|
            ||Администратор\уровень 1\устройства|
            ||Администратор\уровень 2\устройства|
            |SCM Internet Explorer — пользователь|Администратор\уровень 0\устройства|
            ||Администратор\уровень 1\устройства|
            ||Администратор\уровень 2\устройства|
            |ПРИВИЛЕГИРОВАННЫМ конфигурации - пользователя|Администратор\уровень 0\устройства (существующая)|
            ||Администратор\уровень 1\устройства (новая связь)|
            ||Администратор\уровень 2\устройства (новая связь)|

            > [!NOTE]
            > «SCM Windows 10 — безопасность домена» объект групповой Политики может быть привязан к домену независимо от привилегированным ДОСТУПОМ, но будет влиять на весь домен.

6.  **(Необязательно) **Установите дополнительные средства, необходимые для администраторов уровня 1. Установите любые средства и скрипты, необходимые для выполнения рабочих обязанностей. Убедитесь, что Оцените риск раскрытия учетных данных на целевых компьютерах с помощью любого инструмента, прежде чем добавлять его с привилегированным ДОСТУПОМ. Дополнительные сведения об оценке Администрирование и подключения посетите методы риска раскрытия учетных данных для [на этой странице](http://aka.ms/logontypes). Убедитесь, что получите все установочные носители в соответствии с указаниями в принципе чистоты источника для установочных носителей

7.  Определите и безопасно получите программное обеспечение и приложения, требуемые для администрирования.  Это аналогично заданию на этапе 1, но с более широкий диапазон из-за увеличения числа приложений, служб и систем защищаемых.

    > [!NOTE]
    > Обеспечьте защиту этих новых приложений (включая веб-браузеры) с помощью средств защиты, предоставляемых EMET.

    Примеры дополнительного программного обеспечения и приложений:

    -   Microsoft Azure PowerShell

    -   Office 365 PowerShell (также называется модуль Microsoft Online Services)

    -   Приложения или службы управления на базе консоли управления Майкрософт

    -   Пользовательское приложение (не MMC под управлением) или программного обеспечения службы управления

        > [!NOTE]
        > Многие приложения теперь осуществляется исключительно через веб-браузеры, включая множество облачных служб.  Хотя это уменьшает число приложений, которые должны быть установлены на привилегированным ДОСТУПОМ, он также создает риск возникновения проблем с взаимодействием браузера.  Может потребоваться развернуть сторонних веб-браузер в конкретных экземплярах привилегированным ДОСТУПОМ для администрирования определенных служб.  При развертывании дополнительных веб-браузеров, убедитесь, выполните все принципы чистоты источника и обеспечьте их безопасность в соответствии с рекомендациями по обеспечению безопасности поставщика.

8.  **(Необязательно) **Загрузите и установите все требуемые агенты управления.

    > [!NOTE]
    > При выборе установки дополнительных агентов управления (мониторинга, безопасности, управление конфигурациями, т. д.), важно обеспечить соответствие систем управления являются доверенными на том же уровне, контроллеры домена и систем удостоверений. Дополнительные рекомендации см. Управление и обновление PAWs.

9. Оцените инфраструктуру, чтобы определить системы, требующие дополнительных средств защиты, предоставляемых с привилегированным ДОСТУПОМ.  Убедитесь, что вы знаете точно, какие системы должны быть защищены.  Ответьте на важные вопросы о ресурсах, таких как:

    -   Где находятся целевые системы, которыми нужно управлять?  Они собраны в одном месте, или подключены к одной четко заданной подсети?

    -   Сколько вас есть систем?

    -   Эти системы зависят от других систем (виртуализация, хранилище, т. д.), и если да, каким образом осуществляется управление этими системами?  Как критически важных системах, предоставляемых этими зависимостей и каковы дополнительные риски связанные с такой зависимостью?

    -   Насколько важны управляемые службы, и каков ожидаемый ущерб в случае компрометации этих служб?

        > [!NOTE]
        > Оцените облачные службы в ходе этой оценки - злоумышленники первую очередь атакуют незащищенные облачные развертывания и при этом крайне важно администрировании этих служб безопасно при администрировании локальных критически важных приложений.

        Использовать в ходе этой оценки определите конкретные системы, требующие дополнительной защиты, а затем Расширьте программу привилегированным ДОСТУПОМ на администраторов этих систем.  Стандартные примеры систем, получающих преимущества при администрировании с привилегированным ДОСТУПОМ администрировании включают SQL Server (локально и SQL Azure), приложения для отдела кадров и финансовые программного обеспечения.

        > [!NOTE]
        > Если ресурсом осуществляется в системе Windows, им можно управлять с привилегированным ДОСТУПОМ, даже если приложение выполняется в операционной системе, отличной от Windows, или на базе сторонней облачной платформы.  Например подписке Amazon Web Services владельцу следует только использовать привилегированным ДОСТУПОМ для управления учетной записью.

10. Разработка запросов и распространения способ развертывания привилегированным доступом в масштабе организации.  В зависимости от количества привилегированным доступом, развертываемых на этапе 2 может потребоваться автоматизировать этот процесс.

    -   Рассмотрите возможность разработки формирования запросов и процесс утверждения для администраторов при получении привилегированным ДОСТУПОМ.  Этот процесс может помочь стандартизировать развертывание, обеспечить Ведение учета устройств привилегированным ДОСТУПОМ и выявить недостающие элементы в развертывании с привилегированным ДОСТУПОМ.

    -   Как упоминалось ранее, это решение развертывания необходимо отделить от существующих методов автоматизации (которых может быть нарушена) и должно соответствовать принципам, описанным на этапе 1.

        > [!NOTE]
        > Любой системе, управляющей ресурсами, должно осуществляться на том уровне доверия же или более поздней версии.

11. Просмотрите и при необходимости разверните дополнительные профили оборудования привилегированным ДОСТУПОМ.  Профиль оборудования, выбранный для развертывания на этапе 1 может не подходить для всех администраторов.  Просмотрите профили оборудования и при необходимости выберите дополнительные профили оборудования привилегированным ДОСТУПОМ в соответствии с требованиями администраторов.  Например, профиль выделенного оборудования (отдельные привилегированным ДОСТУПОМ и ежедневного использования рабочих станций) может не подходить для путешествующего администратора — в этом случае вы можете развернуть профиль одновременного использования (привилегированным ДОСТУПОМ с виртуальной Машиной пользователя) для этого администратора.

12. Учтите требования к языку, эксплуатации, обмену данными и обучению, сопровождающие Расширенное развертывание привилегированным ДОСТУПОМ.   Таком существенном изменении модели администрирования конечно понадобится управления изменениями в некоторой степени и очень важно для построения, в проект развертывания.  Необходимо учесть по крайней мере следующее:

    -   Как сообщить изменения старший заручиться их поддержкой?  Любой проект без поддержки руководства, скорее всего, сбой или по крайней мере его реализации возникнут трудности финансированием и принятием широким кругом людей.

    -   Как будет задокументирован новый процесс для администраторов  Эти изменения должны регистрироваться и передать не только существующим администраторам (которым потребуется изменить свои привычки и осуществлять управление ресурсами), но и новым администраторам (получившие должность штатного или внештатного организации).  Очень важно, что документации понятно и полные сведения ее важности угроз, привилегированным ДОСТУПОМ роль в обеспечении защиты администраторов и правильном использовании.

        > [!NOTE]
        > Это особенно важно для ролей с высокой текучестью кадров, включая, помимо прочего, сотрудников службы технической поддержки.

    -   Как будет обеспечиваться соответствие в новом процессе?  Хотя модель привилегированным ДОСТУПОМ включает множество технических элементов, предотвращающих раскрытие привилегированных учетных данных, они не смогут обеспечить абсолютную защиту всех возможных экспозиции исключительно с помощью технические средства защиты.  Например несмотря на то, что невозможно предотвратить успешный вход в компьютер пользователя с использованием привилегированных учетных данных администратора, даже попытка такого входа подвергает учетные данные для вредоносных программ, установленных на этом компьютере пользователя.  Поэтому важно объяснить не только преимущества модели привилегированным ДОСТУПОМ, но и риск при несоответствии требованиям.  Это следует быть дополнены аудита и создание предупреждений для быстрого обнаружения и устранения раскрытия учетных данных.

#### <a name="phase-3-extend-and-enhance-protection"></a>Этап 3: Расширение и улучшение защиты
Область: Эти средства безопасности позволяют усовершенствовать системы, созданные на этапе 1. при основные защита усиливается за счет расширенных возможностей, включая многофакторную идентификацию и правила доступа к сети.

> [!NOTE]
> Этот этап можно выполнить в любое время после завершения этапа 1.  Он не зависит от завершения этапа 2 и таким образом можно выполнено до одновременных или после этапа 2.

Выполните следующие действия, чтобы настроить на этом этапе.

1.  Включите многофакторную идентификацию для привилегированных учетных записей.  Многофакторная Идентификация повышает безопасность учетной записи, поскольку требует от пользователя предоставления учетные данные и физический маркер.  Многофакторной идентификации эффективно дополняет политики проверки подлинности, но он не зависит от политики проверки подлинности для развертывания (и, аналогично, политики проверки подлинности не требовать многофакторную проверку подлинности).  Корпорация Майкрософт рекомендует использовать одну из этих форм многофакторной проверки подлинности:

    -   **Смарт-карт**: смарт-карт — это защищенное от несанкционированного вмешательства и мобильные физическое устройство, обеспечивающее вторую проверку во время входа в Windows.  Требование карты для входа в систему, можно снизить риск повторного удаленного украденных учетных данных.  Дополнительные сведения о входе смарт-карт в Windows, см. в статье [Общие сведения о смарт-карт](https://technet.microsoft.com/en-us/library/hh831433.aspx).

    -   **Виртуальная смарт-карта**: виртуальная смарт-карта обеспечивает тот же уровень безопасности как физические смарт-карта с того, ее можно привязать к определенному оборудованию.  Дополнительные сведения о развертывании и требованиях к оборудованию см. в статьях [Общие сведения о виртуальных смарт-карт](https://technet.microsoft.com/en-us/library/dn593708.aspx) и [начало работы с виртуальными смарт-картами: пошаговое руководство](https://technet.microsoft.com/en-us/library/dn579260.aspx).

    -   **Microsoft Passport**: Microsoft Passport позволяет пользователям выполнить проверку подлинности для учетной записи Майкрософт, учетной записи Active Directory, учетной записи Microsoft Azure Active Directory (Azure AD) или сторонней службы, который поддерживает проверку подлинности Fast ID Online (FIDO). После начальной двухэтапной проверки во время регистрации в Microsoft Passport на устройстве пользователя настраивается Microsoft Passport и пользователь устанавливает жест, который может быть Windows Hello или PIN-код. Учетные данные Microsoft Passport — это пара асимметричных ключей, которые можно сгенерировать в изолированных средах доверенных платформенных модулей (TPM).
        Дополнительные сведения о Microsoft Passport см [сведениями о Microsoft Passport](https://technet.microsoft.com/en-us/library/dn985839%28v=vs.85%29.aspx) статьи.

    -   **Многофакторная Идентификация Azure**: многофакторной проверки подлинности Azure (MFA) обеспечивает безопасность второго фактора проверки, а также улучшенную защиту за счет мониторинга и на основе машинного обучения анализа.  Azure MFA можно защиту не только администраторов Azure, но многих других решений, включая веб-приложения, Azure Active Directory и локальные решения, например удаленный доступ и удаленный рабочий стол.  Дополнительные сведения о многофакторной проверки подлинности Azure см. в статье [многофакторной проверки подлинности](https://azure.microsoft.com/en-us/services/multi-factor-authentication).

2.  **Добавьте надежные приложения с помощью Device Guard и/или AppLocker**.  Ограничивая возможность запуска ненадежного или неподписанного кода для запуска на привилегированным ДОСТУПОМ, еще больше снижаете вероятность действий злоумышленников и компрометации.  В Windows предусмотрено два основных компонента для управления приложениями:

    -   **AppLocker**: AppLocker помогает администраторам контролировать, какие приложения можно запускать в определенной системе.  AppLocker можно централизованно управлять с помощью групповой политики и применить к определенным пользователям или группам (для целевых приложений пользователей рабочих привилегированным доступом).  Дополнительные сведения об AppLocker см. в статье TechNet [Обзор AppLocker](https://technet.microsoft.com/library/hh831440.aspx).

    -   **Device Guard**: новая функция Device Guard обеспечивает расширенное аппаратное управление приложениями которого, в отличие от AppLocker, невозможно переопределить на затронутом устройстве.  Как и AppLocker Device Guard можно управлять с помощью групповой политики и предназначен для конкретных пользователей.  Дополнительные сведения об ограничении использования приложений с помощью Device Guard см. в статье TechNet [руководство по развертыванию Device Guard](https://technet.microsoft.com/en-us/library/mt463091(v=vs.85).aspx).

3.  **Использование защищенных пользователей, политик проверки подлинности и приемники команд проверки подлинности для дополнительной защиты привилегированных учетных записей**.  Члены группы защищенных пользователей распространяются Дополнительные политики безопасности которые позволяют защитить учетные данные хранятся в агенте локальной системы безопасности (LSA) и значительно снизить риск кражи учетных данных и повторного использования.  Политики проверки подлинности и приемники команд управляют доступом привилегированных пользователей можно получить доступ к ресурсам в домене.  Вместе эти средства защиты значительно повышают уровень безопасности учетных записей привилегированных пользователей.  Дополнительные сведения об этих возможностях см. в веб-статье [Настройка защищенных учетных записей](https://technet.microsoft.com/en-us/library/dn518179.aspx).

    > [!NOTE]
    > Эти средства защиты предназначены для дополнения, а не замены существующих средств безопасности на этапе 1.  Администраторы по-прежнему должны использовать отдельные учетные записи для администрирования и общих задач.

### <a name="managing-and-updating-paws"></a>Управление и обновление привилегированным доступом
Привилегированным доступом должен быть защиты от вредоносных программ и обновлений программного обеспечения должны применяться для обеспечения целостности рабочих станций быстро.

Управление дополнительной настройки, мониторинга операций и управление безопасностью можно также использовать с привилегированным доступом, но их интеграцию следует тщательно продумать, так как каждая возможность для управления появились риску нарушения привилегированным ДОСТУПОМ с помощью инструмента. Целесообразность для внедрения расширенных возможностей для управления зависит от нескольких факторов:

-   Состояние безопасности и методики, предоставляемые возможностью для управления (включая методы обновления программного обеспечения для средства, административные роли и учетные записи в этих ролей, операционных систем расположен или управляется через средство и все зависимости оборудования или программного обеспечения, средства)

-   Частота и количество развертываний программного обеспечения и обновлений на вашей привилегированным доступом

-   Требования к подробным сведениям запасах и конфигурации

-   Требования к мониторингу безопасности

-   Стандарты организации и другие факторы, зависящие от организации

Принцип чистоты источника всех средств, используемых для управления и отслеживания привилегированным доступом должен быть доверенным, или был выше уровень привилегированным доступом. Как правило управление этими средствами должно осуществляется из привилегированным ДОСТУПОМ для обеспечения независимости безопасности с более низким привилегий рабочих станций.

В этой таблице перечислены различные подходы, которые могут использоваться для управления и мониторинга привилегированным доступом:

|Подход|Рекомендации|
|------|---------|
|По умолчанию в привилегированным ДОСТУПОМ<br /><br />— Windows Server Update Services<br />— Защитник Windows|— Без дополнительных затрат<br />— Выполняет базовые требуемые функции обеспечения безопасности<br />— Указания приведены в этом руководстве|
|Управление с помощью [Intune](https://technet.microsoft.com/en-us/library/jj676587.aspx)|<ul><li>Обеспечивает видимость облачной и управление<br /><br /><ul><li>Развертывание программного обеспечения</li><li>Управление обновлениями программного обеспечения</li><li>Управление политикой брандмауэра Windows</li><li>Защита от вредоносных программ</li><li>Удаленный помощник</li><li>Управление лицензиями на программное обеспечение.</li></ul></li><li>Инфраструктура сервера не требуется</li><li>Требует выполнения действий «Разрешить подключения к облачным службам» на этапе 2</li><li>Если компьютер привилегированным ДОСТУПОМ не присоединен к домену, требуется применить базовые конфигурации SCM к локальным образам, используя средства, предоставляемые при скачивании базовой безопасности.</li></ul>|
|Новые экземпляры System Center для управления привилегированным доступом|— Обеспечивает видимость и управление настройки, развертывания программного обеспечения и обновления для системы безопасности<br />— Требует отдельной инфраструктуры сервера, привязывая ее защиту к уровню рабочей станции с привилегированным и обучения привилегированных сотрудников|
|Управление привилегированным доступом с существующими инструментами управления|— Подвергает значительному риску компрометации привилегированным доступом, если существующей инфраструктуры управления повышен до уровня безопасности рабочей станции с привилегированным **Примечание:** Майкрософт будет обычно не рекомендует использовать этот подход Если в организация нет особых причин для его. Наш опыт показывает – это обычно очень высокая стоимость переноса всех этих средств (и их зависимостей безопасности) до уровня безопасности привилегированным доступом.<br />— Большинство из этих средств обеспечивают видимость и управление настройки, развертывания программного обеспечения и обновления для системы безопасности|
|Сканирование системы безопасности или средства мониторинга, требующие административного доступа|Включает любое средство, устанавливающее агент или требующее учетной записи с правами локального администратора.<br /><br />— Требует, предоставляемого средством безопасности до уровня привилегированным доступом.<br />— Может потребоваться снизить уровень безопасности привилегированным доступом для поддержки функциональных возможностей средства (Открытие портов, установка Java или других по промежуточного слоя, т. д.), создание компромисс решение безопасности,|
|Сведения и событий управления безопасностью (SIEM)|<ul><li>Если SIEM не требует агента:<br /><br /><ul><li>Доступ к события на рабочей станции с привилегированным доступом без прав администратора с помощью учетной записи в **читатели журнала событий** группы</li><li>Может потребоваться открыть сетевые порты, чтобы разрешить передачу входящего трафика с серверов SIEM</li></ul></li><li>Если для SIEM требуется агент, см. другие строке **сканирование системы безопасности или средства мониторинга, требующие административного доступа**.</li></ul>|
|Перенаправление событий Windows|— Обеспечивает метод без агента перенаправления событий системы безопасности с привилегированным доступом во внешние сборщики или SIEM<br />-Возможность доступа к событиям на рабочих станциях с привилегированным доступом без прав администратора<br />— Не требуется открывать сетевые порты, чтобы разрешить передачу входящего трафика с серверов SIEM|

#### <a name="operating-paws"></a>Операционной привилегированным доступом
Решение привилегированным ДОСТУПОМ осуществляется согласно стандартам в [рабочие стандарты](http://aka.ms/securitystandards) на основе принципа чистоты источника.

## <a name="related-topics"></a>Связанные разделы
[Применение служб кибербезопасности Майкрософт](https://www.microsoft.com/en-us/microsoftservices/campaigns/cybersecurity-protection.aspx)

[Представление о Premier: решении Pass--Hash и других видов кражи учетных данных](https://channel9.msdn.com/Blogs/Taste-of-Premier/Taste-of-Premier-How-to-Mitigate-Pass-the-Hash-and-Other-Forms-of-Credential-Theft)

[Microsoft Advanced Threat Analytics](http://aka.ms/ata)

[Защита извлеченных учетных данных домена с помощью Credential Guard](https://technet.microsoft.com/en-us/library/mt483740%28v=vs.85%29.aspx)

[Общие сведения о Guard устройств](https://technet.microsoft.com/en-us/library/dn986865(v=vs.85).aspx)

[Защита ценных ресурсов с рабочих станций безопасного администрирования](https://msdn.microsoft.com/en-us/library/mt186538.aspx)

[Режим изолированного пользователя в Windows 10 с Dave Probert (Channel 9)](https://channel9.msdn.com/Blogs/Seth-Juarez/Isolated-User-Mode-in-Windows-10-with-Dave-Probert)

[Изолированные процессы пользовательского режима и функций в Windows 10 с игре Габриэль (Channel 9)](http://channel9.msdn.com/Blogs/Seth-Juarez/Isolated-User-Mode-Processes-and-Features-in-Windows-10-with-Logan-Gabriel)

[Дополнительные процессы и функции в режиме изолированного пользователя Windows 10 с Dave Probert (Channel 9)](https://channel9.msdn.com/Blogs/Seth-Juarez/More-on-Processes-and-Features-in-Windows-10-Isolated-User-Mode-with-Dave-Probert)

[Устранения риска кражи учетных данных с помощью режима изолированного пользователя Windows 10 (Channel 9)](https://channel9.msdn.com/Blogs/Seth-Juarez/Mitigating-Credential-Theft-using-the-Windows-10-Isolated-User-Mode)

[Включение проверки Strict KDC в Windows Kerberos](https://www.microsoft.com/en-us/download/details.aspx?id=6382)

[Новые возможности проверки подлинности Kerberos для Windows Server 2012](https://technet.microsoft.com/library/hh831747.aspx)

[Контроль механизма проверки подлинности для AD DS в Windows Server 2008 R2: пошаговое руководство](https://technet.microsoft.com/library/dd378897(v=ws.10).aspx)

[Доверенный платформенный модуль](C:\sd\docs\p_ent_keep_secure\p_ent_keep_secure\trusted_platform_module_technology_overview.xml)
