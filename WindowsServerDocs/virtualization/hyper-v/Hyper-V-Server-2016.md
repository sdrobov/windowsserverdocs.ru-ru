---
title: Microsoft Hyper-V Server 2016
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f815ada0-4c63-4e73-9c24-dc5eb21526c7
author: KBDAzure
ms.author: kathydav
ms.date: 07/26/2017
ms.openlocfilehash: c9e1b5e2d30276bf89bc2d56482ec76d1c2241a2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71365584"
---
# <a name="microsoft-hyper-v-server-2016"></a>Microsoft Hyper-V Server 2016

Microsoft Hyper-V Server 2016 — это автономный\-ный продукт, который содержит только гипервизор Windows, модель драйвера Windows Server и компоненты виртуализации. Она предоставляет простое и надежное решение для виртуализации, помогающее повысить эффективность использования сервера и снизить затраты.

Технология гипервизора Windows в Microsoft Hyper-V Server 2016 аналогична роли Hyper\-V в Windows Server 2016. Таким образом, большая часть содержимого, доступного для роли Hyper\-V в Windows Server 2016, также применима к Microsoft Hyper-V Server 2016.

## <a name="hyper-v-server-resources-for-it-pros"></a>Ресурсы по Hyper\-V Server для ИТ-специалистов

|Задачи|Ресурсы|
|-|-|
|![Соответствует символу требований](media/All_Symbols_MeetsRequirements.png)|**Оцените Hyper-V**<br /><br />[Обзор технологии Hyper-V](hyper-v-technology-overview.md) -   <br />- [новые возможности Hyper-V в Windows Server 2016](what-s-new-in-hyper-v-on-windows.md)<br />-   [требования к системе для Hyper-V в Windows Server 2016](system-requirements-for-hyper-v-on-windows.md)<br />-   [Поддерживаемые гостевые операционные системы Windows для Hyper-V](supported-windows-guest-operating-systems-for-hyper-v-on-windows.md)<br />-   [Поддерживаемые виртуальные машины Linux и FreeBSD](supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows.md)<br />-   [совместимости функций по поколениям и гостям](hyper-v-feature-compatibility-by-generation-and-guest.md)<br /><br />**Планирование Hyper-V**<br /><br />— Решите, какое [поколение виртуальных машин](plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v.md) соответствует вашим потребностям. <br/>— Если вы перемещаете или импортируете виртуальные машины, решите, когда следует [обновлять версию](deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server.md). <br />[масштабируемость](plan/plan-hyper-v-scalability-in-windows-server.md) -  <br />- [сети](plan/plan-hyper-v-networking-in-windows-server.md) <br />[безопасность](plan/plan-hyper-v-security-in-windows-server.md) - |
|![Получить символ начала работы](media/All_Symbols_GetStarted.png)|**Приступая к работе с Hyper-V Server**<br /><br />[Скачайте и установите Microsoft Hyper\-V Server 2016](https://www.microsoft.com/evalcenter/evaluate-hyper-v-server-2016). При этом устанавливается низкоуровневая оболочка Windows, модель драйвера Windows Server и компоненты виртуализации. Это похоже на выполнение варианта установки Server Core в Windows Server 2016 и роли Hyper\-V.|
|![Управление символом](media/All_Symbols_Administrator.png)|**Настройка сервера Hyper-V и управление им**<br /><br />Сервер Hyper\-V не имеет графического пользовательского интерфейса \(\)GUI. Для настройки сервера Hyper\-V и управления им можно использовать следующие средства.<br /><br />-   [настроить установку основных серверных компонентов Windows server 2016 с помощью SCONFIG. cmd](../../get-started/sconfig-on-ws2016.md) для обновления параметров домена или рабочей группы, изменения параметров центр обновления Windows, включения удаленного управления и многого другого.<br />— Используйте обычную [командную строку](../../administration/windows-commands/windows-commands.md) для команд, недоступных в SCONFIG.<br />— Используйте [Диспетчер hyper\-v](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/remote_host_management) или [Virtual Machine Manager](https://docs.microsoft.com/system-center/vmm) для удаленного управления сервером Hyper\-V. Чтобы использовать диспетчер Hyper\-V, [установите роль Hyper\-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v) или [Windows Server 2016](get-started/install-the-hyper-v-role-on-windows-server.md).<br />— См. раздел [Установка Server Core](../../get-started/getting-started-with-server-core.md) для дополнительных вариантов управления основными функциями сервера, которые не относятся к Hyper\-V. Большинство описанных методов управления также работают с сервером Hyper\-V.<br /><br />**Настройка виртуальных машин Hyper\-V и управление ими**<br /><br />-   [создать виртуальный коммутатор для виртуальных машин Hyper-V](get-started/create-a-virtual-switch-for-hyper-v-virtual-machines.md)<br />-   [создать виртуальную машину в Hyper-V](get-started/create-a-virtual-machine-in-hyper-v.md)<br />-   [выбрать контрольные точки "Стандартный" или "Рабочая](manage/choose-between-standard-or-production-checkpoints-in-hyper-v.md) "<br />-   [включения или отключения контрольных точек](manage/enable-or-disable-checkpoints-in-hyper-v.md)<br />-   [Управление виртуальными машинами Windows с помощью PowerShell Direct](manage/manage-windows-virtual-machines-with-powershell-direct.md) <br /><br />**Развертывание**<br /><br />-   [настройке узлов для динамической миграции без отказоустойчивой кластеризации](deploy/set-up-hosts-for-live-migration-without-failover-clustering.md)<br />- [обновление узлов кластера Windows Server](../../failover-clustering/cluster-operating-system-rolling-upgrade.md)<br />- [обновить версию виртуальной машины](deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server.md)<br />|
