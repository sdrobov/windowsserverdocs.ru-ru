---
title: Использование Локальные дисковые пространства в виртуальной машине
ms.prod: windows-server
ms.author: eldenc
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: eldenchristensen
ms.date: 10/25/2017
description: Развертывание Локальные дисковые пространства в гостевом кластере виртуальной машины, например в Microsoft Azure.
ms.localizationpriority: medium
ms.openlocfilehash: 74b1b90a780a0b238a356e942f8348e2a483d94a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856117"
---
# <a name="using-storage-spaces-direct-in-guest-virtual-machine-clusters"></a>Использование Локальные дисковые пространства в кластерах гостевых виртуальных машин

> Область применения: Windows Server 2019, Windows Server 2016

Локальные дисковые пространства можно развернуть в кластере физических серверов или в гостевых кластерах виртуальных машин, как описано в этом разделе. Этот тип развертывания обеспечивает виртуальное общее хранилище на множестве виртуальных машин на основе частного или общедоступного облака, чтобы можно было использовать решения высокого уровня доступности приложения для повышения доступности приложений.

![](media/storage-spaces-direct-in-vm/storage-spaces-direct-in-vm.png)

## <a name="deploying-in-azure-iaas-vm-guest-clusters"></a>Развертывание в гостевых кластерах виртуальных машин IaaS Azure

Опубликованные [шаблоны Azure](https://github.com/robotechredmond/301-storage-spaces-direct-md) снижают сложность, настраивают рекомендации и ускоряют развертывание Локальные дисковые пространства на виртуальной машине Azure IaaS. Это рекомендуемое решение для развертывания в Azure.

<iframe src="https://channel9.msdn.com/Series/Microsoft-Hybrid-Cloud-Best-Practices-for-IT-Pros/Step-by-Step-Deploy-Windows-Server-2016-Storage-Spaces-Direct-S2D-Cluster-in-Microsoft-Azure/player" width="960" height="540" allowfullscreen></iframe>

## <a name="requirements"></a>Требования

При развертывании Локальные дисковые пространства в виртуализованной среде следует учитывать следующие моменты.
       
>        !TIP]
>        zure templates will automatically configure the below considerations for you and are the recommended solution when deploying in Azure IaaS VMs.

-   Минимум 2 узла и максимум 3 узла

-   развертывания с двумя узлами должны настроить следящий сервер (облако-свидетель или файловый ресурс-свидетель)

-   Развертывание из трех узлов может допускать 1 узел и потерять 1 или более дисков на другом узле.  При завершении 2 узлов виртуальные диски находятся в автономном режиме до тех пор, пока один из узлов не вернет значение.  

-   Настройка виртуальных машин для развертывания в доменах сбоя

    -   Azure — Настройка группы доступности

    -   Hyper-V — Настройка AntiAffinityClassNames на виртуальных машинах для разделения виртуальных машин между узлами

    -   VMware — настройте правило защиты виртуальных машин виртуальной машины, создав правило DRS типа "отдельные виртуальные машины" для разделения виртуальных машин между узлами ESX. Диски, представленные для использования с Локальные дисковые пространства, должны использовать адаптер Virtual SCSI (PVSCSI). Сведения о поддержке PVSCSI в Windows Server см. в https://kb.vmware.com/s/article/1010398.

-   Используйте хранилище с низкой задержкой или высокой производительностью. требуются управляемые диски Azure класса Premium.

-   Развертывание плоской структуры хранилища без настроенных устройств кэширования

-   Не менее 2 виртуальных дисков данных, представленных для каждой виртуальной машины (VHD/VHDX/VMDK)

    Это число отличается от развертывания на компьютере без операционной системы, так как виртуальные диски могут быть реализованы как файлы, не подверженные физическим сбоям.

-   Отключите автоматическую замену диска "апаб" литиес в служба работоспособности, выполнив следующий командлет PowerShell:

    ```powershell
          Get-storagesubsystem clus* | set-storagehealthsetting -name "System.Storage.PhysicalDisk.AutoReplace.Enabled" -value "False"
          ```

-   To give greater resiliency to possible VHD / VHDX / VMDK storage latency in guest clusters, increase the Storage Spaces I/O timeout value:

    `HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\spaceport\\Parameters\\HwTimeout`

    `dword: 00007530`

    The decimal equivalent of Hexadecimal 7530 is 30000, which is 30 seconds. Note that the default value is 1770 Hexadecimal, or 6000 Decimal, which is 6 seconds.

## Not supported

-   Host level virtual disk snapshot/restore

    Instead use traditional guest level backup solutions to backup and restore the data on the Storage Spaces Direct volumes.

-   Host level virtual disk size change

    The virtual disks exposed through the virtual machine must retain the same size and characteristics. Adding more capacity to the storage pool can be accomplished by adding more virtual disks to each of the virtual machines and adding them to the pool. It's highly recommended to use virtual disks of the same size and characteristics as the current virtual disks.

## See also

[Additional Azure Iaas VM templates for deploying Storage Spaces Direct, videos, and step-by-step guides](https://techcommunity.microsoft.com/t5/Failover-Clustering/Deploying-IaaS-VM-Guest-Clusters-in-Microsoft-Azure/ba-p/372126).

[Additional Storage Spaces Direct Overview](https://docs.microsoft.com/windows-server/storage/storage-spaces/storage-spaces-direct-overview)
""""""''''                                                                                                                                                                        """"""''''                                                                                                                                                                        