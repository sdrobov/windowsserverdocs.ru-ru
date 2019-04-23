---
title: Защищенная структура и экранированные виртуальные машины
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 5c7ada81-2d97-41d4-87cf-1a7ccf06cd20
manager: dongill
author: rpsqrd
ms.author: justinha
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: c2c16574439569eeb1181977f23bae238f43865c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59857435"
---
# <a name="guarded-fabric-and-shielded-vms"></a>Защищенная структура и экранированные виртуальные машины

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

Одна из важнейших целей предоставления размещенной среде важно гарантировать безопасность виртуальных машин, работающих в среде. Поставщики облачных услуг и администраторы корпоративного частного облака могут использовать защищенную структуру для создания более безопасной среды для виртуальных машин. Защищенная структура состоит из одной службы защиты узла (HGS), являющейся, как правило, кластером из трех узлов, одного или нескольких защищенных узлов и набора экранированных виртуальных машин.

> [!IMPORTANT]
> Убедитесь, что вы установили последний накопительный пакет обновления, прежде чем развертывать экранированные виртуальные машины в рабочей среде.

## <a name="videos-blog-and-overview-topic-about-guarded-fabrics-and-shielded-vms"></a>Видео, блог и обзорной статье о защищенных структур и экранированных виртуальных машин

- Видео [Защита вашей структуры виртуализации от внутренних угроз с помощью Windows Server 2019](https://myignite.techcommunity.microsoft.com/sessions/64690)
- Видео [Общие сведения об экранированных виртуальных машин в Windows Server 2016](https://channel9.msdn.com/Shows/Mechanics/Introduction-to-Shielded-Virtual-Machines-in-Windows-Server-2016)
- Видео [Погружение в экранированные виртуальные машины с Windows Server 2016 Hyper-V](https://channel9.msdn.com/events/Ignite/2016/BRK3124)
- Видео [Развертывание экранированных виртуальных машин и защищенной структуры с помощью Windows Server 2016](https://mva.microsoft.com/en-US/training-courses/deploying-shielded-vms-and-a-guarded-fabric-with-windows-server-2016-17131?l=WFLef7vUD_4604300474)
- Блог: [Центр обработки данных и блог по безопасности частного облака](https://blogs.technet.microsoft.com/datacentersecurity/)
- Обзор: [Защищенная структура и экранированные виртуальные машины — Обзор](Guarded-Fabric-and-Shielded-VMs.md)

## <a name="planning-topics"></a>Темы по планированию

- [Руководство по планированию для поставщиков услуг размещения](guarded-fabric-planning-for-hosters.md)
- [Руководство по планированию для клиентов](guarded-fabric-shielded-vm-planning-for-tenants.md)

## <a name="deployment-topics"></a>Разделы, посвященные развертыванию

- [Руководство по развертыванию](guarded-fabric-deploying-hgs-overview.md)
    - [Быстрый запуск](guarded-fabric-deployment-overview.md)
    - [Развертывание HGS](guarded-fabric-setting-up-the-host-guardian-service-hgs.md)
    - [Развертывание защищенных узлов](guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts.md)
        - [Настройка структуры DNS для узлов, которые станут защищенных узлов](guarded-fabric-configuring-fabric-dns.md)
        - [Развертывание защищенного узла, с помощью режима AD](guarded-fabric-admin-trusted-attestation-creating-a-security-group.md)
        - [Развертывание защищенного узла, с помощью режима доверенного платформенного МОДУЛЯ](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md)
        - [Подтвердите подтвердят защищенных узлов](guarded-fabric-confirm-hosts-can-attest-successfully.md)
        - [Экранированные виртуальные машины: поставщик услуг развертывает защищенных узлов в VMM](https://technet.microsoft.com/system-center-docs/vmm/scenario/guarded-hosts)
    - [Развернуть экранированные виртуальные машины](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)
        - [Создать шаблон экранированной виртуальной Машины](guarded-fabric-create-a-shielded-vm-template.md)
        - [Подготовка виртуальной Машины, которое вспомогательный виртуальный жесткий ДИСК](guarded-fabric-vm-shielding-helper-vhd.md)
        - [Настройка Windows Azure Pack](guarded-fabric-hoster-sets-up-windows-azure-pack.md)
        - [Создайте файл данных экранирования](guarded-fabric-tenant-creates-shielding-data.md)
        - [Развертывание экранированной виртуальной Машины с помощью Windows Azure Pack](guarded-fabric-shielded-vm-windows-azure-pack.md)
        - [Развертывание экранированной виртуальной Машины с помощью Virtual Machine Manager](guarded-fabric-tenant-deploys-shielded-vm-using-vmm.md)

## <a name="operations-and-management-topic"></a>Операции и разделе управления

- [Управление службы защиты узла](guarded-fabric-manage-hgs.md)
