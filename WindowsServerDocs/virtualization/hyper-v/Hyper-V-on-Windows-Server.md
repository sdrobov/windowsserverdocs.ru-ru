---
title: Hyper-V в Windows Server
description: Содержит ссылки на основные статьи об использовании и планировании, развертывании и управлении Hyper-V.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0baef6b8-598c-4fe0-9f31-5869fc4e0f69
author: KBDAzure
ms.author: kathydav
ms.date: 10/07/2016
ms.openlocfilehash: 558733e3472578d1df413fe220f1846debc0f358
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71366841"
---
# <a name="hyper-v-on-windows-server"></a>Hyper-V в Windows Server

>Область применения. Windows Server 2016, Windows Server 2019

Роль Hyper-V в Windows Server позволяет создать виртуализированную вычислительную среду, в которой можно создавать виртуальные машины и управлять ими. Можно запустить несколько операционных систем на одном физическом компьютере и изолировать операционные системы друг от друга. С помощью этой технологии можно повысить эффективность вычислительных ресурсов и освободить ресурсы оборудования.

Дополнительные сведения о Hyper-V в Windows Server см. в подразделах, приведенных в следующей таблице.

## <a name="hyper-v-resources-for-it-pros"></a>Ресурсы Hyper-V для ИТ-специалистов

|Задача |Ресурсы|
|---|---|
|![Значок галочки и документ, чтобы отобразить требования](media/All_Symbols_MeetsRequirements.png)|**Оцените Hyper-V**<br /><br />[Обзор технологии Hyper-V](Hyper-V-Technology-Overview.md) - <br />- [новые возможности Hyper-V в Windows Server](What-s-new-in-Hyper-V-on-Windows.md)<br />- [системных требований для Hyper-V в Windows Server](System-requirements-for-Hyper-V-on-Windows.md)<br />- [Поддерживаемые гостевые операционные системы Windows для Hyper-V](Supported-Windows-guest-operating-systems-for-Hyper-V-on-Windows.md) <br />- [поддерживаемых виртуальных машин Linux и FreeBSD](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)<br />Совместимость компонентов - [по поколениям и гостям](Hyper-V-feature-compatibility-by-generation-and-guest.md) <br /><br />**Планирование Hyper-V**<br /><br />- [создавать виртуальную машину поколения 1 или 2 в Hyper-V?](plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md) <br />- [планирование масштабирования Hyper-V в Windows Server](plan/plan-hyper-v-scalability-in-windows-server.md) <br />- [план для сетей Hyper-V в Windows Server](plan/plan-hyper-v-networking-in-windows-server.md) <br />- [план для обеспечения безопасности Hyper-V в Windows Server](plan/plan-hyper-v-security-in-windows-server.md)|
|![Значок курсора и «солнечного лучи»](media/All_Symbols_GetStarted.png)|**Начало работы с Hyper-V**<br /><br />- [скачивание и установка Windows Server 2019](https://www.microsoft.com/evalcenter/evaluate-windows-server-2019)<br /><br />**Вариант установки Server Core или GUI Windows Server 2019 в качестве узла виртуальной машины**<br /><br />- [установите роль Hyper-V в Windows Server](get-started/Install-the-Hyper-V-role-on-Windows-Server.md)<br />- [Создание виртуального коммутатора для виртуальных машин Hyper-V](get-started/Create-a-virtual-switch-for-Hyper-V-virtual-machines.md)<br />- [Создание виртуальной машины в Hyper-V](get-started/Create-a-virtual-machine-in-Hyper-V.md)|
|![Значок "пользователь и инструменты"](media/All_Symbols_Administrator.png)|**Обновление узлов и виртуальных машин Hyper-V**<br /><br />- [обновление узлов кластера Windows Server](../../failover-clustering/Cluster-Operating-System-Rolling-Upgrade.md)<br />- [Обновление версии виртуальной машины](deploy/Upgrade-virtual-machine-version-in-Hyper-V-on-Windows-or-Windows-Server.md)<br /><br />**Настройка Hyper-V и управление им**<br /><br />- [Настройка узлов для динамической миграции без отказоустойчивой кластеризации](deploy/Set-up-hosts-for-live-migration-without-Failover-Clustering.md)<br />- [Удаленное управление Nano Server](../../get-started/manage-nano-server.md)<br />- [Выбор между контрольными точками](manage/Choose-between-standard-or-production-checkpoints-in-Hyper-V.md) уровня "Стандартный" или "Рабочая"<br />- [Включение или отключение контрольных точек](manage/Enable-or-disable-checkpoints-in-Hyper-V.md)<br />- [Управление виртуальными машинами Windows с помощью PowerShell Direct](manage/Manage-Windows-virtual-machines-with-PowerShell-Direct.md)<br />- [Настройка реплики Hyper-V](manage/Set-up-Hyper-V-Replica.md)|
|![Значок пузырька диалога](media/All_Symbols_Chat.png)|**Тех**<br /><br />Ознакомьтесь с последними сообщениями от руководителей программ, менеджеров по продуктам, разработчиков и тестировщиков в группах Microsoft Virtualization и Hyper-V.<br /><br />[блог по виртуализации](https://blogs.technet.com/b/virtualization/) - <br />Блог -  по[Windows Server](https://blogs.technet.com/b/windowsserver/)<br />[блог по виртуализации](https://blogs.msdn.com/b/virtual_pc_guy/) -  Бен Армстронга (архивный)|
|![Значок группы пользователей](media/All_Symbols_Users_Group.png)|**Форум и группы новостей**<br /><br />Есть вопросы? Общайтесь с коллегами, специалистами MVP и группой разработчиков Hyper-V.<br /><br />[сообщество Windows Server](https://techcommunity.microsoft.com/t5/Windows-Server/ct-p/Windows-Server) - <br />- [Форум TechNet по Windows Server Hyper-V](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverhyperv)|

## <a name="related-technologies"></a>Связанные технологии

В следующей таблице перечислены технологии, которые может потребоваться использовать в вычислительной среде виртуализации.

|Технология|Описание|
|--------------|---------------|
|[Клиент Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/index)|Технология виртуализации, входящая в состав Windows 8, Windows 8.1 и Windows 10, которые можно установить с помощью компонента " **программы и компоненты** " на **панели управления**.|
|[Отказоустойчивая кластеризация](https://docs.microsoft.com/windows-server/failover-clustering/whats-new-in-failover-clustering)|Компонент Windows Server, обеспечивающий высокий уровень доступности для узлов и виртуальных машин Hyper-V.|
|[Virtual Machine Manager](https://docs.microsoft.com/system-center/vmm/overview)|Компонент System Center, предоставляющий решение для управления виртуализованным центром обработки данных. Вы можете настраивать узлы виртуализации, сети и ресурсы хранилища, а также управлять ими, позволяя создавать и развертывать виртуальные машины и службы в созданных вами частных облаках.|
|[Контейнеры Windows](https://docs.microsoft.com/virtualization/windowscontainers/)|Используйте Windows Server и контейнеры Hyper-V для предоставления стандартизированных сред для групп разработки, тестирования и Рабочей группы.|