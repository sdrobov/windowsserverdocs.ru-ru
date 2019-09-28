---
title: Установка, обновление или миграция в Windows Server 2019
description: Как выполнить чистую установку, обновление на месте или миграцию в Windows Server
ms.prod: windows-server
ms.technology: server-general
ms.topic: article
ms.assetid: 99f7daa4-30ce-4d13-be65-0a4e99cca754
author: jasongerend
ms.author: jgerend
manager: jasgroce
ms.localizationpriority: medium
ms.openlocfilehash: e10d4cff4b45d1c0d3b447c63104b97ded1cd0d5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71360869"
---
# <a name="install-upgrade-or-migrate-to-windows-server"></a>Установка, обновление или миграция в Windows Server

> Относится к: Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

> [!IMPORTANT]
> Расширенная поддержка Windows Server 2008 R2 и Windows Server 2008 закончится в январе 2020 года. [Узнайте больше о вариантах обновления](http://aka.ms/upgradecenter). Чтобы скачать Windows Server 2019, см. об [ознакомительных версиях Windows Server](https://www.microsoft.com/evalcenter/evaluate-windows-server-2019).

Пришло время перейти на более новую версию Windows Server? В зависимости от того, какая операционная система сейчас установлена на вашем компьютере, у вас есть несколько вариантов.

## <a name="clean-install"></a>Чистая установка

Самый простой способ установить Windows Server — выполнить чистую установку на пустой сервер или перезаписать существующую операционную систему. Это самый простой способ, но для начала вам необходимо создать резервную копию данных и запланировать переустановку приложений. Существует несколько факторов, которые следует учитывать, например требования к системе. Поэтому обязательно проверьте данные [Windows Server 2019](https://go.microsoft.com/fwlink/?linkid=2006124), [Windows Server 2016](https://go.microsoft.com/fwlink/?LinkID=825558), [Windows Server 2012 R2](https://technet.microsoft.com/library/dn303418) и [Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx).

## <a name="in-place-upgrade"></a>Обновление на месте

Если вы хотите использовать то же оборудование и сохранить все роли сервера, которые вы настроили, без сброса настроек сервера, вам подойдет **обновление на месте**, когда вы переходите со старой операционной системы на более новую, сохраняя параметры, роли сервера и данные неповрежденными. Например, если ваш сервер работает под управлением Windows Server 2012 R2, вы можете обновить его до Windows Server 2016 или Windows Server 2019. Однако не каждая устаревшая операционная система позволяет перейти на любую новую ОС. 

Ознакомьтесь со статьей [Общие сведения об обновлениях Windows Server](../upgrade/upgrade-overview.md), чтобы получить пошаговые инструкции по обновлению.

## <a name="cluster-os-rolling-upgrade"></a>Последовательное обновление операционной системы кластера

Последовательное обновление ОС кластера позволяет администратору обновлять ОС узлов кластера с Windows Server 2012 R2 до Windows Server 2016, не останавливая рабочие нагрузки Hyper-V или масштабируемого файлового сервера. Эта функция позволяет избежать простоя, который может нарушать соглашения об уровне обслуживания. Подробнее эта новая функция рассматривается в статье [Последовательное обновление ОС кластера](https://technet.microsoft.com/windows-server-docs/failover-clustering/cluster-operating-system-rolling-upgrade).

## <a name="migration"></a>Миграция

Документация по миграции Windows Server помогает переместить одну роль или компонент за раз с исходного компьютера, работающего под управлением Windows Server, на другой целевой компьютер, работающий под управлением Windows Server такой же или более новой версии. Для этих целей миграция определяется как перемещение одной роли или компонента и его данных на другой компьютер без обновления компонентов на том же компьютере. 

## <a name="license-conversion"></a>Преобразование лицензии

Для некоторых версий ОС можно перейти с определенного выпуска версии на другой выпуск той же версии за один шаг с помощью простой команды и соответствующего лицензионного ключа. Это называется **преобразованием лицензии**. Например, если ваш сервер работает под управлением Windows Server 2016 Standard, вы можете преобразовать его в Windows Server 2016 Datacenter. Следует помнить, что вы можете перейти с плана Standard Server 2016 на Server 2016 Datacenter, вы не сможете обратить этот процесс и перейти с Datacenter на Standard. В некоторых выпусках Windows Server можно также свободно выбирать переход на оригинальную версию, версию с корпоративным лицензированием и розничную версию с помощью той же команды и соответствующего ключа.