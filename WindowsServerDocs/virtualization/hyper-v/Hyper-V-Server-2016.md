---
title: Microsoft Hyper-V Server 2016
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f815ada0-4c63-4e73-9c24-dc5eb21526c7
author: KBDAzure
ms.author: kathydav
ms.date: 07/26/2017
ms.openlocfilehash: 9a1b6ea7b9abc94f63a1390b6fa18e4c8d4a1822
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59839375"
---
# <a name="microsoft-hyper-v-server-2016"></a>Microsoft Hyper-V Server 2016

Microsoft Hyper-V Server 2016 является автономным\-только продукт, который содержит только низкоуровневую оболочку Windows, модель драйверов Windows Server и компоненты виртуализации. Она обеспечивает простое и надежное решение виртуализации помогут вам повысить эффективность использования вашей серверов и снизить затраты.

Технология низкоуровневой оболочки Windows в Microsoft Hyper-V Server 2016 совпадает со значением в Hyper\-роли V в Windows Server 2016. Таким образом, большая часть содержимого, доступного для Hyper\-роли V в Windows Server 2016 также относится к Microsoft Hyper-V Server 2016.

## <a name="hyper-v-server-resources-for-it-pros"></a>Hyper\-сервера V-ресурсы для ИТ-специалистов

|Задачи|Ресурсы|
|-|-|
|![Соответствует требованиям символ](media/All_Symbols_MeetsRequirements.png)|**Оценить Hyper-V**<br /><br />-   [Общие сведения о технологии Hyper-V](hyper-v-technology-overview.md)<br />- [Новые возможности в Hyper-V в Windows Server 2016](what-s-new-in-hyper-v-on-windows.md)<br />-   [Требования к системе для Hyper-V в Windows Server 2016](system-requirements-for-hyper-v-on-windows.md)<br />-   [Поддерживаемых гостевых ОС Windows для Hyper-V](supported-windows-guest-operating-systems-for-hyper-v-on-windows.md)<br />-   [Поддерживаемые ОС Linux и FreeBSD виртуальных машин](supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows.md)<br />-   [Совместимость компонентов в зависимости от поколения и гостя](hyper-v-feature-compatibility-by-generation-and-guest.md)<br /><br />**Планирование для Hyper-V**<br /><br />— Решить, какие [поколение виртуальной машины](plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v.md) соответствует вашим потребностям. <br/>-При перемещении или импорте виртуальных машин, принимается решение о [обновление до версии](deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server.md). <br />- [Масштабируемость](plan/plan-hyper-v-scalability-in-windows-server.md) <br />- [Сетевые подключения](plan/plan-hyper-v-networking-in-windows-server.md) <br />- [Безопасность](plan/plan-hyper-v-security-in-windows-server.md)|
|![Получение символов по началу работы](media/All_Symbols_GetStarted.png)|**Начало работы с Hyper-V Server**<br /><br />[Скачайте и установите Microsoft Hyper\-V Server 2016](https://www.microsoft.com/evalcenter/evaluate-hyper-v-server-2016). Установится гипервизор Windows, модель драйверов Windows Server и компоненты виртуализации. Это похоже на под управлением варианта установки основных серверных компонентов Windows Server 2016 и Hyper\-V роли.|
|![Управление символ](media/All_Symbols_Administrator.png)|**Настройка и управление сервером Hyper-V**<br /><br />Hyper\-V сервер не имеет графического интерфейса \(графического пользовательского интерфейса\). Можно использовать следующие средства для настройки и управления Hyper\-V Server.<br /><br />-   [Настройка установки Server Core Windows Server 2016 с помощью Sconfig.cmd](../../get-started/sconfig-on-ws2016.md) для обновления параметров домена или рабочей группы, изменять Windows обновить параметры, Включение удаленного управления и многое другое.<br />— Используйте обычный [командной](../../administration/windows-commands/windows-commands.md) для команд не доступно в Sconfig.<br />— Используйте [Hyper\-V Manager](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/remote_host_management) или [Virtual Machine Manager](https://docs.microsoft.com/system-center/vmm) для удаленного управления Hyper\-V Server. Для использования Hyper\-диспетчера V [установить Hyper\-роли V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v) или [Windows Server 2016](get-started/install-the-hyper-v-role-on-windows-server.md).<br />— См. в разделе [Установка основных серверных компонентов](../../get-started/getting-started-with-server-core.md) параметры дополнительного управления для функции базового сервера, не требующих Hyper\-V. Большинство методов управления, описанных существует также работают с Hyper\-V Server.<br /><br />**Настройка и управление ими Hyper\-V виртуальных машин**<br /><br />-   [Создайте виртуальный коммутатор для виртуальных машин Hyper-V](get-started/create-a-virtual-switch-for-hyper-v-virtual-machines.md)<br />-   [Создание виртуальной машины в Hyper-V](get-started/create-a-virtual-machine-in-hyper-v.md)<br />-   [Выбор между стандартных или рабочих контрольных точек](manage/choose-between-standard-or-production-checkpoints-in-hyper-v.md)<br />-   [Включение или отключение контрольных точек](manage/enable-or-disable-checkpoints-in-hyper-v.md)<br />-   [Управление виртуальными машинами Windows с помощью PowerShell Direct](manage/manage-windows-virtual-machines-with-powershell-direct.md) <br /><br />**Развертывание**<br /><br />-   [Настройка узлов для динамической миграции без отказоустойчивой кластеризации](deploy/set-up-hosts-for-live-migration-without-failover-clustering.md)<br />- [Обновления узлов кластера Windows Server](../../failover-clustering/cluster-operating-system-rolling-upgrade.md)<br />- [Обновление версии виртуальной машины](deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server.md)<br />|
