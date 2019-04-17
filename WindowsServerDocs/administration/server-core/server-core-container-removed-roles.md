---
title: Роли, службы ролей и компонентов не в версии контейнеров - сервере Windows Server Core 1803
description: Сведения о роли и компоненты, которые были удалены из контейнера изображения ядра сервера для Windows Server.
ms.prod: windows-server-threshold
ms.mktglfcycl: manage
ms.sitesec: library
author: lizap
ms.localizationpriority: medium
ms.date: 05/07/2018
ms.openlocfilehash: 0ad574a04ba7ecd235f1825bd25c247a1565edf6
ms.sourcegitcommit: 1533d994a6ddea54ac189ceb316b7d3c074307db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "1859920"
---
# <a name="roles-role-services-and-features-not-in-server-core-containers---windows-server-version-1803"></a>Роли, службы ролей и компонентов не в версии контейнеров - сервере Windows Server Core 1803

> Применимо к: версия 1803 Windows Server

В Windows Server, версия 1803, что [сокращение общий размер изображения, контейнер основных серверных компонентов **1.58 ГБ**](https://blogs.technet.microsoft.com/virtualization/2018/01/22/a-smaller-windows-server-core-container-with-better-application-compatibility/). Это сделано можно путем оптимизации архитектуры и удаление вещей, которые не требуется в [контейнер основных серверных компонентов](https://docs.microsoft.com/virtualization/windowscontainers/about/). Некоторые были вещей, которые не работают в контейнерах, некоторые были ролей и компонентов, которые никто использует. 

> [!IMPORTANT]
> Были удалены их из него **контейнер** основных серверных компонентов, не [сам основных серверных компонентов](server-core-roles-and-services.md). 

Ниже приведен полный список функций и ролями, удалены из контейнера изображения основных серверных компонентов:

<div style='font-size:9.0pt'>

<br>ADCertificateServicesRole
<br>AuthManager
<br>Служебные программы BitLocker
<br>BitLocker
<br>БИТ
<br>Отправка BITSExtensions
<br>CCFFilter
<br>CertificateEnrollmentPolicyServer
<br>CertificateEnrollmentServer
<br>CertificateServices
<br>ClientForNFS инфраструктуры
<br>Контейнеры
<br>CoreFileServer
<br>DataCenterBridging-LLDP-средства
<br>DataCenterBridging
<br>Основные Dedup
<br>DeviceHealthAttestationService
<br>Компьютеры сервера
<br>DFSR инфраструктуры ServerEdition
<br>Режим ADAM DirectoryServices
<br>DirectoryServices DomainController
<br>Качество обслуживания дисковый ввод-вывод
<br>EnhancedStorage
<br>FailoverCluster-пакет средств администрирования
<br>FailoverCluster AutomationServer
<br>FailoverCluster CmdInterface
<br>FailoverCluster FullServer
<br>FailoverCluster PowerShell
<br>Файловые службы
<br>FileServerVSSAgent
<br>Инфраструктура службы репликации файлов
<br>FSRM инфраструктура служб
<br>FSRM инфраструктуры
<br>HardenedFabricEncryptionTask
<br>HostGuardian
<br>Пакет HostGuardianService
<br>IdentityServer SecurityTokenService
<br>IPAMClientFeature
<br>IPAMServerFeature
<br>iSCSITargetServer PowerShell
<br>iSCSITargetServer
<br>iSCSITargetStorageProviders
<br>iSNS_Service
<br>Лицензирование
<br>LightweightServer
<br>Microsoft Hyper-V-управления клиентов
<br>Microsoft-Hyper-V-автономный режим
<br>Microsoft Hyper-V-подключении
<br>Microsoft Hyper-V
<br>Microsoft Windows-FCI-Client пакет
<br>Windows-групповой политики ServerAdminTools-Центр обновления Майкрософт
<br>Microsoft Windows подсистема Linux
<br>MSRDC-инфраструктуры
<br>MultipathIo
<br>NetworkController
<br>NetworkControllerTools
<br>NetworkDeviceEnrollmentServices
<br>NetworkLoadBalancingFullServer
<br>NetworkVirtualization
<br>OnlineRevocationServices
<br>P2P PnrpOnly
<br>PeerDist
<br>Печать клиента графического интерфейса пользователя
<br>LPDPrintService печати
<br>Печать Server-Foundation функции
<br>Роль сервера печати
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
<br>Службы управления правами федерации
<br>Пользовательский Интерфейс SBMgr
<br>ServerCore драйверы General WOW64
<br>ServerCore драйверы Общие
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
<br>Хранилище реплики AdminPack
<br>Реплики хранилища
<br>TPM PSH командлеты
<br>База данных UpdateServices
<br>UpdateServices служб
<br>UpdateServices WidDatabase
<br>UpdateServices
<br>VmHostAgent
<br>VolumeActivation-Full-Role
<br>Прокси веб-приложения
<br>Веб-клиент
<br>WebEnrollmentServices
<br>Защитник Windows
<br>Значение WindowsServerBackup
<br>WindowsStorageManagementService
<br>WINSRuntime
<br>WMISnmpProvider
<br>WorkFolders сервер
<br>Пакет продукта WSS

</div>