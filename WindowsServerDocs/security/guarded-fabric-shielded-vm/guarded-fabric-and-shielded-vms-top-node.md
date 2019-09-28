---
title: Защищенная структура и экранированные виртуальные машины
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 5c7ada81-2d97-41d4-87cf-1a7ccf06cd20
manager: dongill
author: rpsqrd
ms.author: justinha
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: c06432a039341978956066344710920652187b97
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403663"
---
# <a name="guarded-fabric-and-shielded-vms"></a>Защищенная структура и экранированные виртуальные машины

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

Одной из наиболее важных целей предоставления размещенной среды является обеспечение безопасности виртуальных машин, работающих в среде. Поставщики облачных услуг и администраторы корпоративного частного облака могут использовать защищенную структуру для создания более безопасной среды для виртуальных машин. Защищенная структура состоит из одной службы защиты узла (HGS), являющейся, как правило, кластером из трех узлов, одного или нескольких защищенных узлов и набора экранированных виртуальных машин.

> [!IMPORTANT]
> Перед развертыванием экранированных виртуальных машин в рабочей среде убедитесь, что установлено последнее накопительное обновление.

## <a name="videos-blog-and-overview-topic-about-guarded-fabrics-and-shielded-vms"></a>Видеоролики, блоги и обзорные разделы о защищенных структурах и экранированных виртуальных машинах

- Видео [Как защитить структуру виртуализации от предварительных угроз с помощью Windows Server 2019](https://myignite.techcommunity.microsoft.com/sessions/64690)
- Видео [Общие сведения о экранированных виртуальных машинах в Windows Server 2016](https://channel9.msdn.com/Shows/Mechanics/Introduction-to-Shielded-Virtual-Machines-in-Windows-Server-2016)
- Видео [Познакомьтесь с экранированными виртуальными машинами с помощью Windows Server 2016 Hyper-V](https://channel9.msdn.com/events/Ignite/2016/BRK3124)
- Видео [Развертывание экранированных виртуальных машин и защищенной структуры с помощью Windows Server 2016](https://mva.microsoft.com/en-US/training-courses/deploying-shielded-vms-and-a-guarded-fabric-with-windows-server-2016-17131?l=WFLef7vUD_4604300474)
- Серверах [Блог по безопасности центра обработки данных и частного облака](https://blogs.technet.microsoft.com/datacentersecurity/)
- Обзор: [Обзор защищенной структуры и экранированных виртуальных машин](Guarded-Fabric-and-Shielded-VMs.md)

## <a name="planning-topics"></a>Темы по планированию

- [Структура планирования для поставщиков услуг размещения](guarded-fabric-planning-for-hosters.md)
- [Структура планирования для клиентов](guarded-fabric-shielded-vm-planning-for-tenants.md)

## <a name="deployment-topics"></a>Разделы по развертыванию

- [Рекомендации по развертыванию](guarded-fabric-deploying-hgs-overview.md)
    - [Быстрый запуск](guarded-fabric-deployment-overview.md)
    - [Развертывание HGS](guarded-fabric-setting-up-the-host-guardian-service-hgs.md)
    - [Развертывание защищенных узлов](guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts.md)
        - [Настройка DNS структуры для узлов, которые станут защищенными узлами](guarded-fabric-configuring-fabric-dns.md)
        - [Развертывание защищенного узла в режиме AD](guarded-fabric-admin-trusted-attestation-creating-a-security-group.md)
        - [Развертывание защищенного узла с помощью режима TPM](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md)
        - [Подтверждение аттестации защищенных узлов](guarded-fabric-confirm-hosts-can-attest-successfully.md)
        - [Экранированные виртуальные машины. поставщик услуг размещения развертывает защищенные узлы в VMM.](https://technet.microsoft.com/system-center-docs/vmm/scenario/guarded-hosts)
    - [Развертывание экранированных виртуальных машин](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)
        - [Создание шаблона экранированной виртуальной машины](guarded-fabric-create-a-shielded-vm-template.md)
        - [Подготовка виртуального жесткого диска экранирования виртуальной машины](guarded-fabric-vm-shielding-helper-vhd.md)
        - [Установка Windows Azure Pack](guarded-fabric-hoster-sets-up-windows-azure-pack.md)
        - [Создание файла данных экранирования](guarded-fabric-tenant-creates-shielding-data.md)
        - [Развертывание экранированной виртуальной машины с помощью Windows Azure Pack](guarded-fabric-shielded-vm-windows-azure-pack.md)
        - [Развертывание экранированной виртуальной машины с помощью Virtual Machine Manager](guarded-fabric-tenant-deploys-shielded-vm-using-vmm.md)

## <a name="operations-and-management-topic"></a>Раздел "операции и управление"

- [Управление службой защиты узла](guarded-fabric-manage-hgs.md)
