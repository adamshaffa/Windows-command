---
title: Features removed or no longer developed starting with Windows Server 2019
description: Learn about the features and functionalities removed or no longer developed starting with Windows Server 2019.
ms.topic: conceptual
author: robinharwood
ms.author: roharwoo
manager: femila
ms.date: 11/25/2022
---

# Features removed or no longer developed starting with Windows Server 2019

Each release of Windows Server adds new features and functionality; we also occasionally remove features and functionality, usually because we've added a better option. Here are the details about the features and functionalities that we removed in Windows Server 2019.

> [!TIP]
>
> - You can get early access to Windows Server builds by joining the [Windows Insider program](https://insider.windows.com) - this is a great way to test feature changes.

**The list is subject to change and might not include every affected feature or functionality.**

## Features we've removed in this release

We're removing the following features and functionalities from the installed product image in Windows Server 2019. Applications or code that depend on these features won't function in this release unless you use an alternate method.

| Feature | Explanation |
|--|--|
| Business Scanning, also called Distributed Scan Management (DSM) | We're removing this secure scanning and scanner management capability - there are no devices that support this feature. |
| Print components - now optional component for Server Core installations | In previous releases of Windows Server, the print components were **disabled** by default in the Server Core installation option. We changed that in Windows Server 2016, enabling them by default. In Windows Server 2019, those print components are once again disabled by default for Server Core. If you need to enable the print components, you can do so by running the `Install-WindowsFeature Print-Server` cmdlet. |
| [Remote Desktop Connection Broker and Remote Desktop Virtualization Host](../remote/remote-desktop-services/desktop-hosting-service.md) in a Server Core installation | Most Remote Desktop Services deployments have these roles co-located with the Remote Desktop Session Host (RDSH), which requires Server with Desktop Experience. To be consistent with RDSH, we're changing these roles to also require Server with Desktop Experience. These RDS roles are no longer available for use in a [Server Core installation](../administration/server-core/what-is-server-core.md). If you need to [deploy these roles as part of your Remote Desktop infrastructure](../remote/remote-desktop-services/rds-deploy-infrastructure.md), you can [install them on Windows Server with Desktop Experience](../get-started/getting-started-with-server-with-desktop-experience.md). <br/><br/>These roles are also included in the Desktop Experience installation option of Windows Server 2019. |
| [RemoteFX 3D Video Adapter (vGPU)](../virtualization/hyper-v/deploy/deploy-graphics-devices-using-remotefx-vgpu.md) | We're developing new graphics acceleration options for virtualized environments. You can also use [Discrete Device Assignment (DDA)](../virtualization/hyper-v/plan/plan-for-deploying-devices-using-discrete-device-assignment.md) as an alternative. |
| Nano Server installation option | Nano Server isn't available as an installable host operating system. Instead, Nano Server is available as a container operating system. To learn more about Nano Server as a container, see [Windows Container Base Images](/virtualization/windowscontainers/manage-containers/container-base-images). |
| Server Message Block (SMB) version 1 | Starting with this release, Server Message Block (SMB) version 1 is no longer installed by default. For details, see [SMBv1 isn't installed by default in Windows 10 version 1709, Windows Server version 1709 and later versions](../storage/file-server/Troubleshoot/smbv1-not-installed-by-default-in-windows.md) |
| [File Replication Service](https://support.microsoft.com/help/4025991/windows-server-version-1709-no-longer-supports-frs) | File Replication Services, introduced in Windows Server 2003 R2, has been replaced by DFS Replication. You need to [migrate any domain controllers that use FRS for the sysvol folder to DFS Replication](https://techcommunity.microsoft.com/t5/storage-at-microsoft/streamlined-migration-of-frs-to-dfsr-sysvol/ba-p/425405). |
| Hyper-V Network Virtualization (HNV) | [Network Virtualization](../networking/sdn/technologies/hyper-v-network-virtualization/whats-new-hyperv-network-virtualization-windows-server.md) is now included in Windows Server as part of the [Software Defined Networking](/azure-stack/hci/concepts/software-defined-networking) (SDN) solution. The SDN solution also includes the Network Controller, Software Load Balancing, User-Defined Routing, and Access Control Lists. |

## Features we're no longer developing

We're no longer actively developing these features and may remove them from a future update. Some features have been replaced with other features or functionality, while others are now available from different sources.

| Feature | Explanation |
|--|--|
| Key Storage Drive in Hyper-V | We're no longer working on the Key Storage Drive feature in Hyper-V. If you're using generation 1 virtual machines (VMs), check out [Generation 1 VM Virtualization Security](../virtualization/hyper-v/learn-more/generation-1-virtual-machine-security-settings-for-hyper-v.md) for information about options going forward. If you're creating new VMs, use Generation 2 virtual machines with TPM devices for a more secure solution. |
| Trusted Platform Module (TPM) management console|The information previously available in the TPM management console is now available on the [**Device security**](/windows/security/threat-protection/windows-defender-security-center/wdsc-device-security) page in the [Windows Defender Security Center](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center). |
| Host Guardian Service Active Directory attestation mode | We're no longer developing Host Guardian Service Active Directory attestation mode, instead we've added a new attestation mode, [host key attestation](../security/guarded-fabric-shielded-vm/guarded-fabric-create-host-key.md). Host key attestation is simpler and equally as compatible as Active Directory based attestation.  This new mode provides equivalent functionality with a setup experience, simpler management and fewer infrastructure dependencies than the Active Directory attestation. Host key attestation has no extra hardware requirements beyond what Active Directory attestation required, so all existing systems will remain compatible with the new mode. For more information, see [Deploy guarded hosts](../security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts.md) for more information about your attestation options. |
| OneSync service | The OneSync service synchronizes data for the Mail, Calendar, and People apps. We've added a sync engine to the Outlook app that provides the same synchronization. |
| Remote Differential Compression API support | Remote Differential Compression API support enabled synchronizing data with a remote source using compression technologies, which minimized the amount of data sent across the network. |
| WFP lightweight filter switch extension | The WFP lightweight filter switch extension enables developers to build [simple network packet filtering extensions for the Hyper-V virtual switch](/windows-hardware/drivers/network/using-virtual-switch-filtering). You can achieve the same functionality by creating a full filtering extension. As such, we'll be removing this extension in the future. |
| IIS 6 Management compatibility | Specific features being considered for replacement are:<p><li>IIS 6 Metabase Compatibility (Web-Metabase)</li><li>IIS 6 Management Console (Web-Lgcy-Mgmt-Console)</li><li>IIS 6 Scripting Tools (Web-Lgcy-Scripting)</li><li>IIS 6 WMI Compatibility (Web-WMI)</li></p><p>IIS 6 Metabase Compatibility acts as an emulation layer between IIS 6-based metabase scripts and the file-based configuration used by IIS 7 or newer versions. You should start migrating management scripts to target IIS file-based configuration directly, by using tools such as the Microsoft.Web.Administration namespace.</p><p>You should also start migration from IIS 6.0 or earlier versions, and move to the latest version of IIS, which is always available in the most recent release of Windows Server. </p>|
| IIS Digest Authentication | This authentication method is planned for replacement. Instead, you should start using other authentication methods such as Client Certificate Mapping (see [Configuring One-to-One Client Certificate Mappings](/iis/manage/configuring-security/configuring-one-to-one-client-certificate-mappings)) or Windows Authentication (see [Application Settings](/iis-administration/configuration/appsettings.json)). |
| Internet Storage Name Service (iSNS) | The Server Message Block (SMB) feature offers essentially the same functionality with more features. See [Server Message Block Overview](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) for background information on this feature. |
| RSA/AES Encryption for IIS | This encryption method is being considered for replacement because the superior Cryptography API: Next Generation (CNG) method is already available. To learn more about CNG encryption, see [About CNG](/windows/win32/seccng/about-cng). |
| Windows PowerShell 2.0 | This early version of Windows PowerShell has been superseded by several more recent versions. For the best features and performance, migrate to Windows PowerShell 5.0 or later. See [PowerShell Documentation](/powershell/index?view=powershell-5.1&preserve-view=true) for plenty of information. |
| IPv4/6 Transition Technologies (6to4, ISATAP, and Direct Tunnels)|6to4 has been disabled by default since Windows 10, version 1607 (the Anniversary Update), ISATAP has been disabled by default since Windows 10, version 1703 (the Creators Update), and Direct Tunnels has always been disabled by default. Use native IPv6 support instead. |
| [MultiPoint Services](../remote/multipoint-services/multipoint-services.md)|We're no longer developing the MultiPoint Services role as part of Windows Server. MultiPoint Connector services are available through [Feature on Demand](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities) for both Windows Server and Windows 10. You can use [Remote Desktop Services](../remote/remote-desktop-services/welcome-to-rds.md), in particular the Remote Desktop Services Session Host, to provide RDP connectivity. |
| [Offline symbol packages](/windows-hardware/drivers/debugger/debugger-download-symbols) (Debug symbol MSIs)|We're no longer making the symbol packages available as a downloadable MSI. Instead, the [Microsoft Symbol Server is moving to be an Azure-based symbol store](/archive/blogs/windbg/update-on-microsofts-symbol-server). If you need the Windows symbols, connect to the Microsoft Symbol Server to cache your symbols locally or use a manifest file with SymChk.exe on a computer with internet access. |
| [Software Restriction Policies](../identity/software-restriction-policies/software-restriction-policies.md) in Group Policy | Instead of using the Software Restriction Policies through Group Policy, you can use [AppLocker](/windows/security/threat-protection/applocker/applocker-overview) or [Windows Defender Application Control](/windows/security/threat-protection/windows-defender-application-control). You can use AppLocker and Windows Defender Application Control to manage which apps users can access and what code can run in the kernel. |
| Storage Spaces in a Shared configuration using a SAS fabric|Deploy [Storage Spaces Direct](/azure-stack/hci/concepts/storage-spaces-direct-overview) instead. Storage Spaces Direct supports the use of HLK-certified SAS enclosures, but in a non-shared configuration, as described in the [Storage Spaces Direct hardware requirements](../storage/storage-spaces/storage-spaces-direct-hardware-requirements.md). |
| Windows Server Essentials Experience|We're no longer developing the Essentials Experience role for the Windows Server Standard or Windows Server Datacenter SKUs. If you need an easy-to-use server solution for small-to-medium businesses, check out our new [Microsoft 365 for business](https://www.microsoft.com/microsoft-365/business) solution, or use [Windows Server 2016 Essentials](/windows-server-essentials/get-started/get-started). |