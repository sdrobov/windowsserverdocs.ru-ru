---
title: Использование Локальные дисковые пространства в виртуальной машине
description: Развертывание Локальные дисковые пространства в гостевом кластере виртуальной машины, например в Microsoft Azure.
ms.prod: windows-server
ms.author: eldenc
manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: eldenchristensen
ms.date: 10/25/2017
ms.localizationpriority: medium
ms.openlocfilehash: 816e589cbb7ed4196411b8f5bab740c7ee5f7595
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436769"
---
# <a name="using-storage-spaces-direct-in-guest-virtual-machine-clusters"></a>Использование Локальные дисковые пространства в кластерах гостевых виртуальных машин

> Применяется к: Windows Server 2019, Windows Server 2016

Вы можете развернуть Локальные дисковые пространства в кластере физических серверов или в гостевых кластерах виртуальных машин, как описано в этом разделе. Этот тип развертывания обеспечивает виртуальное общее хранилище на множестве виртуальных машин на основе частного или общедоступного облака, чтобы можно было использовать решения высокого уровня доступности приложения для повышения доступности приложений.

![](media/storage-spaces-direct-in-vm/storage-spaces-direct-in-vm.png)

## <a name="deploying-in-azure-iaas-vm-guest-clusters"></a>Развертывание в гостевых кластерах виртуальных машин IaaS Azure

Опубликованные [шаблоны Azure](https://github.com/robotechredmond/301-storage-spaces-direct-md) снижают сложность, настраивают рекомендации и ускоряют развертывание Локальные дисковые пространства на виртуальной машине Azure IaaS. Это рекомендуемое решение для развертывания в Azure.

<iframe src="https://channel9.msdn.com/Series/Microsoft-Hybrid-Cloud-Best-Practices-for-IT-Pros/Step-by-Step-Deploy-Windows-Server-2016-Storage-Spaces-Direct-S2D-Cluster-in-Microsoft-Azure/player" width="960" height="540" allowfullscreen></iframe>

## <a name="requirements"></a>Требования

При развертывании Локальные дисковые пространства в виртуализованной среде следует учитывать следующие моменты.

> [!TIP]
> Шаблоны Azure автоматически настраивают указанные ниже рекомендации и являются рекомендуемым решением при развертывании на виртуальных машинах Azure IaaS.

- Минимум 2 узла и максимум 3 узла

- развертывания с двумя узлами должны настроить следящий сервер (облако-свидетель или файловый ресурс-свидетель)

- Развертывание из трех узлов может допускать 1 узел и потерять 1 или более дисков на другом узле.  При завершении 2 узлов виртуальные диски находятся в автономном режиме до тех пор, пока один из узлов не вернет значение.

- Настройка виртуальных машин для развертывания в доменах сбоя

    - Azure — Настройка группы доступности

    - Hyper-V — Настройка AntiAffinityClassNames на виртуальных машинах для разделения виртуальных машин между узлами

    - VMware — настройте правило защиты виртуальных машин виртуальной машины, создав правило DRS типа "отдельные виртуальные машины" для разделения виртуальных машин между узлами ESX. Диски, представленные для использования с Локальные дисковые пространства, должны использовать адаптер Virtual SCSI (PVSCSI). Сведения о поддержке PVSCSI в Windows Server см https://kb.vmware.com/s/article/1010398 . в.

- Используйте хранилище с низкой задержкой или высокой производительностью. требуются управляемые диски Azure класса Premium.

- Развертывание плоской структуры хранилища без настроенных устройств кэширования

- Не менее 2 виртуальных дисков данных, представленных для каждой виртуальной машины (VHD/VHDX/VMDK)

    Это число отличается от развертывания на компьютере без операционной системы, так как виртуальные диски могут быть реализованы как файлы, не подверженные физическим сбоям.

- Отключите функции автоматического замены дисков в служба работоспособности, выполнив следующий командлет PowerShell:

    ```powershell
          Get-storagesubsystem clus* | set-storagehealthsetting -name "System.Storage.PhysicalDisk.AutoReplace.Enabled" -value "False"
          ```

- To give greater resiliency to possible VHD / VHDX / VMDK storage latency in guest clusters, increase the Storage Spaces I/O timeout value:

    `HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\spaceport\\Parameters\\HwTimeout`

    `dword: 00007530`

    The decimal equivalent of Hexadecimal 7530 is 30000, which is 30 seconds. Note that the default value is 1770 Hexadecimal, or 6000 Decimal, which is 6 seconds.

## Not supported

- Host level virtual disk snapshot/restore

    Instead use traditional guest level backup solutions to backup and restore the data on the Storage Spaces Direct volumes.

- Host level virtual disk size change

    The virtual disks exposed through the virtual machine must retain the same size and characteristics. Adding more capacity to the storage pool can be accomplished by adding more virtual disks to each of the virtual machines and adding them to the pool. It's highly recommended to use virtual disks of the same size and characteristics as the current virtual disks.

## See also

- [Additional Azure Iaas VM templates for deploying Storage Spaces Direct, videos, and step-by-step guides](https://techcommunity.microsoft.com/t5/Failover-Clustering/Deploying-IaaS-VM-Guest-Clusters-in-Microsoft-Azure/ba-p/372126).

- [Additional Storage Spaces Direct Overview](https://docs.microsoft.com/windows-server/storage/storage-spaces/storage-spaces-direct-overview)
