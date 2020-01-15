---
title: Развертывание службы защиты узла
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 310b63d9-5ac7-4961-98ef-103af45d706a
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 52b88dde5a273d64ad2428965754f714fe2392d0
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75950407"
---
# <a name="deploying-the-host-guardian-service"></a>Развертывание службы защиты узла 

>Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

Одной из наиболее важных целей предоставления размещенной среды является обеспечение безопасности виртуальных машин, работающих в среде. Поставщики облачных служб и администраторы корпоративного частного облака могут использовать защищенную структуру для создания более безопасной среды для виртуальных машин. Защищенная структура состоит из одной службы защиты узла (HGS), являющейся, как правило, кластером из трех узлов, одного или нескольких защищенных узлов и набора экранированных виртуальных машин.

## <a name="video-deploying-a-guarded-fabric"></a>Видео. Развертывание защищенной структуры 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/dcd8e99f-36f1-4bc8-b3d2-9576da38d9f1?autoplay=false]

## <a name="deployment-tasks-for-guarded-fabrics-and-shielded-vms"></a>Задачи развертывания для защищенных структур и экранированных виртуальных машин

Следующая таблица разделяет задачи на развертывание защищенной структуры и создание экранированных виртуальных машин в соответствии с разными ролями администратора. Обратите внимание, что когда администратор HGS настраивает HGS с полномочными узлами Hyper-V, администратор структуры будет одновременно получать и предоставлять идентифицирующие сведения о узлах.    

|<img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-hgs-administrator-tasks.png" alt="Host Guardian Service administrator tasks" width="238" height="62" align="left" /> | <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-fabric-administrator-tasks.png" alt="Fabric administrator tasks" width="300" height="62" align="left" /> | <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-tenant-administrator-tasks.png" alt="Tenant administrator tasks" width="184" height="66" align="left" /> |
|-------------------------------------|--------------------------------|-----------------------------------------|
|<img src="../media/Guarded-Fabric-Shielded-VM/1111.png" alt="Step 1" hspace="8" align="left" /> [Проверка предварительных требований для HGS](guarded-fabric-prepare-for-hgs.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-verify.png" alt="Step 1" hspace="8" align="right" />| | |
|<img src="../media/Guarded-Fabric-Shielded-VM/2222.png" alt="Step 2" hspace="8" align="left" /> [Настройка первого узла&nbsp;HGS](guarded-fabric-choose-where-to-install-hgs.md)&nbsp;<img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-configure-first-hgs-node.png" alt="Step 2" hspace="8" align="right" />| | |
|<img src="../media/Guarded-Fabric-Shielded-VM/3333.png" alt="Step 3" hspace="8" align="left" /> [Настройка дополнительных узлов&nbsp;HGS](guarded-fabric-configure-additional-hgs-nodes.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-configure-secondary-hgs-nodes.png" alt="Step 3" hspace="8" align="right" />| | |
|<img src="../media/Guarded-Fabric-Shielded-VM/4444.png" alt="Step 4" hspace="8" align="left" /> [Проверка конфигурации HGS](guarded-fabric-verify-hgs-configuration.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-verify-hgs-configuration.png" alt="Step 4" hspace="8" align="right" />| | |
| &nbsp; |<img src="../media/Guarded-Fabric-Shielded-VM/5555.png" alt="Step 5" hspace="8" align="left" /> [Настройка DNS структуры](guarded-fabric-configuring-fabric-dns.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-configure-fabric-dns.png" alt="Step 5" hspace="8" align="right" />| |
| &nbsp; |<img src="../media/Guarded-Fabric-Shielded-VM/6666.png" alt="Step 6" hspace="8" align="left" /> [Проверка предварительных требований для&nbsp;узла (ключ)](guarded-fabric-guarded-host-prerequisites.md#host-key-attestation)<br>[Проверка предварительных требований&nbsp;узла (TPM)](guarded-fabric-guarded-host-prerequisites.md#tpm-trusted-attestation)<img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-verify.png" alt="Step 6" hspace="8" align="right" />| |
|<img src="../media/Guarded-Fabric-Shielded-VM/8888.png" alt="Step 8" hspace="8" align="left" /> [Настройка HGS со сведениями об узле](guarded-fabric-add-host-information-to-hgs.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-configure-hgs-with-host-info.png" alt="Step 8" hspace="8" align="right" />|<img src="../media/Guarded-Fabric-Shielded-VM/7777.png" alt="Step 7" hspace="8" align="left" /> [Создать ключ узла (ключ)](guarded-fabric-create-host-key.md)<br>[Получение сведений об узле (TPM)](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-collect-info-from-hosts.png" alt="Step 7" hspace="8" align="right" />| |
| &nbsp; |<img src="../media/Guarded-Fabric-Shielded-VM/9999.png" alt="Step 9" hspace="8" align="left" /> [Подтвердить, что узлы могут подтверждать](guarded-fabric-confirm-hosts-can-attest-successfully.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-confirm-hosts-attest.png" alt="Step 9" hspace="8" align="right" />| |
| &nbsp; |<img src="../media/Guarded-Fabric-Shielded-VM/101010.png" alt="Step 10" hspace="8" align="left" /> [Настройка VMM (необязательно)](https://technet.microsoft.com/system-center-docs/vmm/scenario/guarded-overview) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-configure-vmm.png" alt="Step 10" hspace="8" align="right" />| |
| &nbsp; |<img src="../media/Guarded-Fabric-Shielded-VM/11eleven.png" alt="Step 11" hspace="8" align="left" /> [Создание шаблонов дисков](guarded-fabric-create-a-shielded-vm-template.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-create-template-disk.png" alt="Step 11" hspace="8" align="right" />| |
| &nbsp; |<img src="../media/Guarded-Fabric-Shielded-VM/121212.png" alt="Step 12" hspace="8" align="left" /> [Создание вспомогательного диска экранирования виртуальных машин для VMM (необязательно)](guarded-fabric-vm-shielding-helper-vhd.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-create-helper-disk.png" alt="Step 12" hspace="8" align="right" />| |
| &nbsp; |<img src="../media/Guarded-Fabric-Shielded-VM/131313.png" alt="Step 13" hspace="8" align="left" /> [Настройка Windows Azure Pack (необязательно)](guarded-fabric-shielded-vm-windows-azure-pack.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-windows-azure-pack.png" alt="Step 13" hspace="8" align="right" />| |
| &nbsp; | &nbsp; |<img src="../media/Guarded-Fabric-Shielded-VM/141414.png" alt="Step 14" hspace="8" align="left" /> [Создание файла данных экранирования](guarded-fabric-tenant-creates-shielding-data.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-shielding-data-file.png" alt="Step 14" hspace="8" align="right" />|
| &nbsp; | &nbsp; |<img src="../media/Guarded-Fabric-Shielded-VM/151515.png" alt="Step 15" hspace="8" align="left" /> [Создание экранированных виртуальных машин с помощью Windows Azure Pack](guarded-fabric-shielded-vm-windows-azure-pack.md) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-shielded-vms.png" alt="Step 15" hspace="8" align="right" /><br>[Создание экранированных виртуальных машин с помощью VMM](https://technet.microsoft.com/system-center-docs/vmm/scenario/guarded-vms) <img src="../media/Guarded-Fabric-Shielded-VM/guarded-host-shielded-vms.png" alt="Step 15" hspace="8" align="right" />|


## <a name="see-also"></a>См. также статью

- [Защищенная структура и экранированные виртуальные машины](guarded-fabric-and-shielded-vms-top-node.md)
