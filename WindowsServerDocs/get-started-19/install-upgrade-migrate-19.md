---
title: Установка | Обновление | Миграция в Windows Server 2019 г.
description: Как чистая установка, обновление на месте или перенести в Windows Server 2019.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: server-general
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99f7daa4-30ce-4d13-be65-0a4e99cca754
author: coreyp-at-msft
ms.author: coreyp
manager: jasgroce
ms.localizationpriority: medium
ms.openlocfilehash: 58c363fc0a1e336519bc6ec4276651345cc2b5eb
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868715"
---
# <a name="install--upgrade--migrate-to-windows-server-2019"></a>Установка | Обновление | Миграция в Windows Server 2019 г.

>Область применения. Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

> [!IMPORTANT]
> Расширенная поддержка для Windows Server 2008 R2 и Windows Server 2008 закончится в январе 2020 г. [Дополнительные сведения о вариантах обновления](http://aka.ms/upgradecenter).

Пришло время перейти на более новую версию Windows Server? В зависимости от того, какая операционная система сейчас установлена на вашем компьютере, у вас есть множество вариантов.

## <a name="clean-install"></a>Провести чистую установку
Если вы хотите переместить из более старой версии Windows Server в Windows Server 2019 на том же оборудовании, необходимо выполнить **чистой установки**, где просто установить новую операционную систему непосредственно поверх старой на том же оборудовании, Таким образом удалить предыдущую операционную систему. Это самый простой способ, но для начала вам необходимо создать резервную копию данных и запланировать переустановку приложений. Существует несколько моментов, которые следует учитывать, например требования к системе, поэтому не забудьте проверить сведения для [Windows Server 2019](https://go.microsoft.com/fwlink/?linkid=2006124), [Windows Server 2016](https://go.microsoft.com/fwlink/?LinkID=825558), [Windows Server 2012 R2](https://technet.microsoft.com/library/dn303418) , и [Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx).

## <a name="in-place-upgrade"></a>Обновление на месте
Если вы хотите сохранить то же оборудование и всех ролей сервера, вы настроили без сведение сервера, нужно будет сделать **обновление на месте**, по которой вы перейти из старой операционной системы на более новую, сохранив ваши параметры сервера роли и неповрежденными данными. Например если сервер работает под управлением Windows Server 2012 R2, можно обновить его в Windows Server 2016 или Windows Server 2019. Однако не все устаревшие операционные системы имеют канал к каждой новой ОС. См. на следующей схеме доступны варианты обновления:

![Схема варианты обновления на месте Windows Server](media/upgrade-paths.png)

Пошаговое руководство по обновлению см. в статье [Центр обновления Windows Server](http://aka.ms/upgradecenter):

<a href="http://aka.ms/upgradecenter"><img src="media/upgrade-center.png" alt="Screenshot of Windows Upgrade Center" title="Центр обновления Windows Server"></a>

## <a name="cluster-os-rolling-upgrade"></a>Последовательное обновление кластерной ОС
Последовательного обновления кластерной ОС позволяет администратору обновлять ОС узлов кластера с Windows Server 2012 R2 и Windows Server 2016, не останавливая рабочие нагрузки Scale-Out File Server или Hyper-V. Эта функция позволяет избежать простоя, который может нарушать соглашения об уровне обслуживания. Подробнее эта новая функция рассматривается в статье [Последовательное обновление ОС кластера](https://technet.microsoft.com/windows-server-docs/failover-clustering/cluster-operating-system-rolling-upgrade).

## <a name="migration"></a>Миграция

Миграция Windows Server — при перемещении одной роли или компонента одновременно с исходного компьютера, на котором выполняется Windows Server на другой конечный компьютер, на котором работает Windows Server, в той же или более новой версии. Для этих целей миграция определяется как перемещение одной роли или компонента и его данных на другой компьютер без обновления компонентов на том же компьютере. 

## <a name="license-conversion"></a>Преобразование лицензии
для некоторых версий ОС можно перейти с определенного выпуска версии на другой выпуск той же версии за один шаг с помощью простой команды и соответствующего лицензионного ключа. Это называется **преобразованием лицензии**. Например, если ваш сервер работает под управлением Windows Server2016 Standard, вы можете преобразовать его в Windows Server2016 Datacenter. В некоторых выпусках Windows Server также можно свободно выбирать переход на оригинальную версию, версию с корпоративным лицензированием и розничную версию с помощью той же команды и соответствующего ключа.


 
 
