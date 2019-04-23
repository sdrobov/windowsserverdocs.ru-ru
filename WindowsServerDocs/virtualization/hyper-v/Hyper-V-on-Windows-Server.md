---
title: Hyper-V в Windows Server
description: Ссылки на ключевые ресурсы, посвященные разделена, планирования, развертывания и управления Hyper-V
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0baef6b8-598c-4fe0-9f31-5869fc4e0f69
author: KBDAzure
ms.author: kathydav
ms.date: 10/07/2016
ms.openlocfilehash: 1a658b611b68d7ecde64bdf0f8a318cc1af2804c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59880265"
---
# <a name="hyper-v-on-windows-server"></a>Hyper-V в Windows Server

>Область применения. Windows Server 2016, Windows Server 2019 г.

Роль Hyper-V в Windows Server позволяет создавать виртуализованную компьютерную среду, где можно создать и управлять виртуальными машинами. Можно запускать несколько операционных систем на одном физическом компьютере и изоляцию операционных систем друг от друга. С этой технологией можно повысить эффективность вычислительных ресурсов и освободите свои ресурсы оборудования.

См. в разделах, в таблице ниже, чтобы узнать больше о Hyper-V в Windows Server.

## <a name="hyper-v-resources-for-it-pros"></a>Ресурсы по Hyper-V для ИТ-специалистов

|Задача |Ресурсы|
|---|---|
|![Флажок и значок документа, чтобы показать требования выполнены](media/All_Symbols_MeetsRequirements.png)|**Оценить Hyper-V**<br /><br />- [Общие сведения о технологии Hyper-V](Hyper-V-Technology-Overview.md)<br />- [Новые возможности в Hyper-V в Windows Server](What-s-new-in-Hyper-V-on-Windows.md)<br />- [Требования к системе для Hyper-V в Windows Server](System-requirements-for-Hyper-V-on-Windows.md)<br />- [Поддерживаемых гостевых ОС Windows для Hyper-V](Supported-Windows-guest-operating-systems-for-Hyper-V-on-Windows.md) <br />- [Поддерживаемые виртуальные машины Linux и FreeBSD](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)<br />- [Совместимость компонентов в зависимости от поколения и гостя](Hyper-V-feature-compatibility-by-generation-and-guest.md) <br /><br />**Планирование для Hyper-V**<br /><br />- [Следует ли создавать виртуальные машины поколения 1 или 2 в Hyper-V?](plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md) <br />- [Планирование масштабируемость Hyper-V в Windows Server](plan/plan-hyper-v-scalability-in-windows-server.md) <br />- [Планирование сети Hyper-V в Windows Server](plan/plan-hyper-v-networking-in-windows-server.md) <br />- [Планирование безопасности Hyper-V в Windows Server](plan/plan-hyper-v-security-in-windows-server.md)|
|![Значок курсора и "солнечные лучи"](media/All_Symbols_GetStarted.png)|**Начало работы с Hyper-V**<br /><br />- [Скачайте и установите Windows Server 2019](https://www.microsoft.com/evalcenter/evaluate-windows-server-2019)<br /><br />**Server Core или графического пользовательского интерфейса вариант установки Windows Server 2019 как основного компьютера виртуальной машины**<br /><br />- [Установка роли Hyper-V в Windows Server](get-started/Install-the-Hyper-V-role-on-Windows-Server.md)<br />- [Создайте виртуальный коммутатор для виртуальных машин Hyper-V](get-started/Create-a-virtual-switch-for-Hyper-V-virtual-machines.md)<br />- [Создание виртуальной машины в Hyper-V](get-started/Create-a-virtual-machine-in-Hyper-V.md)|
|![Значок пользователя и средства](media/All_Symbols_Administrator.png)|**Обновление узлов Hyper-V и виртуальных машин**<br /><br />- [Обновления узлов кластера Windows Server](../../failover-clustering/Cluster-Operating-System-Rolling-Upgrade.md)<br />- [Обновление версии виртуальной машины](deploy/Upgrade-virtual-machine-version-in-Hyper-V-on-Windows-or-Windows-Server.md)<br /><br />**Настройка и управление ими в Hyper-V**<br /><br />- [Настройка узлов для динамической миграции без отказоустойчивой кластеризации](deploy/Set-up-hosts-for-live-migration-without-Failover-Clustering.md)<br />- [Удаленное управление Nano Server](../../get-started/manage-nano-server.md)<br />- [Выбор между стандартных или рабочих контрольных точек](manage/Choose-between-standard-or-production-checkpoints-in-Hyper-V.md)<br />- [Включение или отключение контрольных точек](manage/Enable-or-disable-checkpoints-in-Hyper-V.md)<br />- [Управление виртуальными машинами Windows с помощью PowerShell Direct](manage/Manage-Windows-virtual-machines-with-PowerShell-Direct.md)<br />- [Настройка реплики Hyper-V](manage/Set-up-Hyper-V-Replica.md)|
|![Значок пузырьки сообщений](media/All_Symbols_Chat.png)|**Блоги**<br /><br />Извлечь последние сообщения руководителей программ, менеджеры по продуктам и разработчиков и инженеров-испытателей в группах Microsoft виртуализации и Hyper-V.<br /><br />- [Блог виртуализации](https://blogs.technet.com/b/virtualization/)<br />- [Блог по Windows Server](https://blogs.technet.com/b/windowsserver/)<br />- [Блог виртуализации Бена Армстронга](https://blogs.msdn.com/b/virtual_pc_guy/) (архивированным)|
|![Значок группы пользователя](media/All_Symbols_Users_Group.png)|**Форум и группы новостей**<br /><br />У вас есть вопросы? Взаимодействовать с коллегами, специалистами MVP и команде разработчиков Hyper-V.<br /><br />- [Windows Server Community](https://techcommunity.microsoft.com/t5/Windows-Server/ct-p/Windows-Server)<br />- [Форум по Windows Server Hyper-V TechNet](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverhyperv)|

## <a name="related-technologies"></a>Связанные технологии

Ниже перечислены технологии, которые можно использовать в своей компьютерной среде виртуализации.

|Технология|Описание|
|--------------|---------------|
|[Клиент Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/index)|Технология виртуализации, в состав Windows 8, Windows 8.1 и Windows 10, которую можно установить через **программы и компоненты** в **панели управления**.|
|[Отказоустойчивая кластеризация](https://docs.microsoft.com/windows-server/failover-clustering/whats-new-in-failover-clustering)|Компонент Windows Server, который обеспечивает высокий уровень доступности для узлов Hyper-V и виртуальных машин.|
|[Virtual Machine Manager](https://docs.microsoft.com/system-center/vmm/overview)|Компонент System Center, который предоставляет решение для управления виртуализованным центром данных. Можно настроить и управлять узлов виртуализации, сетей и ресурсы хранения, поэтому можно создать и развернуть виртуальные машины и службы в частных облаках, которые вы создали.|
|[Контейнеры Windows](https://docs.microsoft.com/virtualization/windowscontainers/)|Используйте контейнеры Windows Server и Hyper-V для предоставления стандартизированные среды для разработки, тестирования и рабочих групп.|