---
title: Ролей, служб ролей и компонентов не в Server Core контейнеры — Windows Server версии 1803
description: Дополнительные сведения о роли и компоненты, которые мы удалили из образа контейнера основных серверных компонентов для Windows Server.
ms.prod: windows-server-threshold
ms.mktglfcycl: manage
ms.sitesec: library
author: lizap
ms.localizationpriority: medium
ms.date: 05/07/2018
ms.openlocfilehash: 0ad574a04ba7ecd235f1825bd25c247a1565edf6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873785"
---
# <a name="roles-role-services-and-features-not-in-server-core-containers---windows-server-version-1803"></a>Ролей, служб ролей и компонентов не в Server Core контейнеры — Windows Server версии 1803

> Относится к: Windows Server версии 1803

В Windows Server версии 1803, мы улучшили [уменьшить общий размер образа контейнера основных серверных компонентов **1.58 ГБ**](https://blogs.technet.microsoft.com/virtualization/2018/01/22/a-smaller-windows-server-core-container-with-better-application-compatibility/). Мы проделали это можно путем оптимизации архитектуры и удаляя параметры не требуются в [контейнера Server Core](https://docs.microsoft.com/virtualization/windowscontainers/about/). Некоторые были вещи, которые не работают в контейнерах, некоторые были ролей и компонентов, которые никто не использует. 

> [!IMPORTANT]
> Мы удалили из Server Core **контейнера** изображений, не [основных серверных компонентов, сам](server-core-roles-and-services.md). 

Ниже приведен полный список функций и ролей, удаляются из контейнера образа основных серверных компонентов:

<div style='font-size:9.0pt'>

<br>ADCertificateServicesRole
<br>AuthManager
<br>Служебные программы BitLocker
<br>BitLocker
<br>BITS
<br>Отправка BITSExtensions
<br>CCFFilter
<br>CertificateEnrollmentPolicyServer
<br>CertificateEnrollmentServer
<br>CertificateServices
<br>ClientForNFS инфраструктуры
<br>Контейнеры
<br>CoreFileServer
<br>Средства для LLDP DataCenterBridging
<br>DataCenterBridging
<br>Core дедупликации
<br>DeviceHealthAttestationService
<br>DFSN-сервер
<br>DFSR-инфраструктуры — ServerEdition
<br>DirectoryServices-ADAM
<br>DirectoryServices-DomainController
<br>Дисковый ввод-вывод QoS
<br>EnhancedStorage
<br>FailoverCluster-AdminPak
<br>FailoverCluster-AutomationServer
<br>FailoverCluster-CmdInterface
<br>FailoverCluster-FullServer
<br>FailoverCluster-PowerShell
<br>Файловые службы
<br>FileServerVSSAgent
<br>FRS-инфраструктуры
<br>Службы FSRM-инфраструктуры
<br>Инфраструктура FSRM
<br>HardenedFabricEncryptionTask
<br>HostGuardian
<br>HostGuardianService-Package
<br>IdentityServer SecurityTokenService
<br>IPAMClientFeature
<br>IPAMServerFeature
<br>iSCSITargetServer с помощью PowerShell
<br>iSCSITargetServer
<br>iSCSITargetStorageProviders
<br>iSNS_Service
<br>Лицензирование
<br>LightweightServer
<br>Microsoft Hyper-V-Management клиентов
<br>Microsoft-Hyper-V — автономный режим
<br>Microsoft-Hyper-V-Online
<br>Microsoft-Hyper-V
<br>Microsoft-Windows-FCI-клиента Package
<br>Microsoft-Windows-GroupPolicy-ServerAdminTools обновление
<br>Microsoft-Windows-Subsystem-Linux
<br>MSRDC инфраструктуры
<br>MultipathIo
<br>NetworkController
<br>NetworkControllerTools
<br>NetworkDeviceEnrollmentServices
<br>NetworkLoadBalancingFullServer
<br>NetworkVirtualization
<br>OnlineRevocationServices
<br>P2P-PnrpOnly
<br>PeerDist
<br>Печать клиента графического пользовательского интерфейса
<br>Печать LPDPrintService
<br>Печать Server-Foundation функции
<br>Роли для сервера печати
<br>QWAVE
<br>RasRoutingProtocols
<br>Службы удаленной рабочего стола
<br>Удаленного доступа
<br>RemoteAccessMgmtTools
<br>RemoteAccessPowerShell
<br>RemoteAccessServer
<br>ResumeKeyFilter
<br>RightsManagementServices роли
<br>RightsManagementServices
<br>Федерация службы управления правами
<br>Пользовательский Интерфейс SBMgr
<br>ServerCore драйверы — общие — WOW64
<br>ServerCore драйверы — Общие
<br>ServerForNFS инфраструктуры
<br>ServerManager-Core-RSAT-Feature-Tools
<br>ServerMediaFoundation
<br>ServerMigration
<br>SessionDirectory
<br>SetupAndBootEventCollection
<br>ShieldedVMToolsAdminPack
<br>SMB1Protocol-сервер
<br>SmbDirect
<br>SMBHashGeneration
<br>SmbWitness
<br>SNMP
<br>SoftwareLoadBalancer
<br>Хранилище, реплика, AdminPack
<br>Реплика хранилища
<br>Доверенный платформенный модуль PSH-командлеты
<br>UpdateServices-базы данных
<br>UpdateServices-Services
<br>UpdateServices-WidDatabase
<br>UpdateServices
<br>VmHostAgent
<br>VolumeActivation-Full-Role
<br>Прокси веб-приложения
<br>WebAccess
<br>WebEnrollmentServices
<br>Защитник Windows
<br>WindowsServerBackup
<br>WindowsStorageManagementService
<br>WINSRuntime
<br>WMISnmpProvider
<br>WorkFolders сервер
<br>WSS пакета

</div>