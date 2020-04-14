---
title: Hyper-V в Windows Server
description: Содержит ссылки на основные статьи об использовании и планировании, развертывании и управлении Hyper-V.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.topic: article
ms.assetid: 0baef6b8-598c-4fe0-9f31-5869fc4e0f69
author: kbdazure
ms.author: kathydav
ms.date: 10/07/2016
ms.openlocfilehash: e75f61fb957929e668b3a1663402786cc399abe8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853257"
---
# <a name="hyper-v-on-windows-server"></a>Hyper-V в Windows Server

>Область применения: Windows Server 2016, Windows Server 2019

Роль Hyper-V в Windows Server позволяет создать виртуализированную вычислительную среду, в которой можно создавать виртуальные машины и управлять ими. Можно запустить несколько операционных систем на одном физическом компьютере и изолировать операционные системы друг от друга. С помощью этой технологии можно повысить эффективность вычислительных ресурсов и освободить ресурсы оборудования.

Дополнительные сведения о Hyper-V в Windows Server см. в подразделах, приведенных в следующей таблице.

## <a name="hyper-v-resources-for-it-pros"></a>Ресурсы Hyper-V для ИТ-специалистов

|Задача |Ресурсы|
|---|---|
|![Значок галочки и документ, чтобы отобразить требования](media/All_Symbols_MeetsRequirements.png)|**Оцените Hyper-V**<p>[Обзор технологии Hyper-V](Hyper-V-Technology-Overview.md) - <br />- [новые возможности Hyper-V в Windows Server](What-s-new-in-Hyper-V-on-Windows.md)<br />- [требования к системе для Hyper-V в Windows Server](System-requirements-for-Hyper-V-on-Windows.md)<br />- [Поддерживаемые гостевые операционные системы Windows для Hyper-V](Supported-Windows-guest-operating-systems-for-Hyper-V-on-Windows.md) <br />- [Поддерживаемые виртуальные машины Linux и FreeBSD](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)<br />- [совместимости функций по поколениям и гостям](Hyper-V-feature-compatibility-by-generation-and-guest.md) <p>**Планирование Hyper-V**<p>- [следует ли создать виртуальную машину поколения 1 или 2 в Hyper-V?](plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md) <br />- [план масштабируемости Hyper-V в Windows Server](plan/plan-hyper-v-scalability-in-windows-server.md) <br />[план - для сетей Hyper-V в Windows Server](plan/plan-hyper-v-networking-in-windows-server.md) <br />[план - для обеспечения безопасности Hyper-V в Windows Server](plan/plan-hyper-v-security-in-windows-server.md)|
|![Значок курсора и «солнечного лучи»](media/All_Symbols_GetStarted.png)|**Начало работы с Hyper-V**<p>- [загрузить и установить Windows Server 2019](https://www.microsoft.com/evalcenter/evaluate-windows-server-2019)<p>**Вариант установки Server Core или GUI Windows Server 2019 в качестве узла виртуальной машины**<p>- [установить роль Hyper-V в Windows Server](get-started/Install-the-Hyper-V-role-on-Windows-Server.md)<br />- [создать виртуальный коммутатор для виртуальных машин Hyper-V](get-started/Create-a-virtual-switch-for-Hyper-V-virtual-machines.md)<br />- [создать виртуальную машину в Hyper-V](get-started/Create-a-virtual-machine-in-Hyper-V.md)|
|![Значок "пользователь и инструменты"](media/All_Symbols_Administrator.png)|**Обновление узлов и виртуальных машин Hyper-V**<p>- [обновление узлов кластера Windows Server](../../failover-clustering/Cluster-Operating-System-Rolling-Upgrade.md)<br />- [обновить версию виртуальной машины](deploy/Upgrade-virtual-machine-version-in-Hyper-V-on-Windows-or-Windows-Server.md)<p>**Настройка Hyper-V и управление им**<p>- [настройке узлов для динамической миграции без отказоустойчивой кластеризации](deploy/Set-up-hosts-for-live-migration-without-Failover-Clustering.md)<br />[Удаленное управление сервером Nano Server](../../get-started/manage-nano-server.md) - <br />- [выбрать контрольные точки "Стандартный" или "Рабочая](manage/Choose-between-standard-or-production-checkpoints-in-Hyper-V.md) "<br />- [включения или отключения контрольных точек](manage/Enable-or-disable-checkpoints-in-Hyper-V.md)<br />- [Управление виртуальными машинами Windows с помощью PowerShell Direct](manage/Manage-Windows-virtual-machines-with-PowerShell-Direct.md)<br />- [настроить реплику Hyper-V](manage/Set-up-Hyper-V-Replica.md)|
|![Значок пузырька диалога](media/All_Symbols_Chat.png)|**Тех**<p>Ознакомьтесь с последними сообщениями от руководителей программ, менеджеров по продуктам, разработчиков и тестировщиков в группах Microsoft Virtualization и Hyper-V.<p>Блог - ной [виртуализации](https://blogs.technet.com/b/virtualization/)<br />[блог - Windows Server](https://blogs.technet.com/b/windowsserver/)<br />[блог о виртуализации - Бен Армстронга](https://blogs.msdn.com/b/virtual_pc_guy/) (архивный)|
|![Значок группы пользователей](media/All_Symbols_Users_Group.png)|**Форум и группы новостей**<p>Есть вопросы? Общайтесь с коллегами, специалистами MVP и группой разработчиков Hyper-V.<p>[сообщество - Windows Server](https://techcommunity.microsoft.com/t5/Windows-Server/ct-p/Windows-Server)<br />[Форум TechNet по Windows Server Hyper-V](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverhyperv) - |

## <a name="related-technologies"></a>Связанные технологии

В следующей таблице перечислены технологии, которые может потребоваться использовать в вычислительной среде виртуализации.

|Технология|Описание|
|--------------|---------------|
|[Клиент Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/index)|Технология виртуализации, входящая в состав Windows 8, Windows 8.1 и Windows 10, которые можно установить с помощью компонента " **программы и компоненты** " на **панели управления**.|
|[Отказоустойчивая кластеризация](https://docs.microsoft.com/windows-server/failover-clustering/whats-new-in-failover-clustering)|Компонент Windows Server, обеспечивающий высокий уровень доступности для узлов и виртуальных машин Hyper-V.|
|[Virtual Machine Manager](https://docs.microsoft.com/system-center/vmm/overview)|Компонент System Center, предоставляющий решение для управления виртуализованным центром обработки данных. Вы можете настраивать узлы виртуализации, сети и ресурсы хранилища, а также управлять ими, позволяя создавать и развертывать виртуальные машины и службы в созданных вами частных облаках.|
|[Контейнеры Windows](https://docs.microsoft.com/virtualization/windowscontainers/)|Используйте Windows Server и контейнеры Hyper-V для предоставления стандартизированных сред для групп разработки, тестирования и Рабочей группы.|