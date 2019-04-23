---
title: Обновление и установка Windows Server
description: ''
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.date: 07/12/2018
ms.technology: server-general
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98f876bd-63ff-4c3a-95d4-a8dd8d0d119c
author: jaimeo
ms.author: jaimeo
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: c3b9070fc6cb9227ccfa445e23983d9e91fe5c82
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59859195"
---
# <a name="windows-server-installation-and-upgrade"></a>Обновление и установка Windows Server

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

> [!IMPORTANT]
> Расширенная поддержка для Windows Server 2008 R2 и Windows Server 2008 закончится в январе 2020 г. [Дополнительные сведения о вариантах обновления](#upgrading-from-windows-server-2008-r2-or-windows-server-2008).

Пришло время перейти на более новую версию Windows Server? В зависимости от того, какая операционная система сейчас установлена на вашем компьютере, у вас есть множество вариантов.

## <a name="installation"></a>Установка
Если вы хотите перейти на более новую версию Windows Server на том же оборудовании, единственным способом, который всегда работает, является **чистая установка**, когда вы просто устанавливаете более новую операционную систему поверх старой на имеющемся у вас оборудовании, удаляя таким образом предыдущую операционную систему. Это самый простой способ, но для начала вам необходимо создать резервную копию данных и запланировать переустановку приложений. Существует несколько факторов, которые следует учитывать, например, требования к системе. Поэтому обязательно проверьте данные по [Windows Server 2016](https://go.microsoft.com/fwlink/?LinkID=825558), [Windows Server 2012 R2](https://technet.microsoft.com/library/dn303418) и [Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx).

При переходе с любой предварительной версии (например, Windows Server 2016 Technical Preview) на выпущенную версию (Windows Server 2016) всегда требуется чистая установка.

## <a name="migration-recommended-for-windows-server-2016"></a>Миграция (рекомендуется для Windows Server 2016)

Документация [по миграции] Windows Server помогает перенести одну роль или компонент за раз из исходного компьютера, работающего под управлением Windows Server, на другой целевой компьютер, работающий под управлением Windows Server, такой же или более новой версии. Для этих целей миграция определяется как перемещение одной роли или компонента и его данных на другой компьютер без обновления компонентов на том же компьютере. Это рекомендуемый способ, при котором перемещаются существующие рабочая нагрузка и данные на более новую версию Windows Server. Чтобы начать работу, проверьте [матрицу миграции и обновления роли сервера](https://go.microsoft.com/fwlink/?LinkId=828595) для Windows Server 2016.

## <a name="cluster-os-rolling-upgrade"></a>Последовательное обновление кластерной ОС
Последовательное обновление ОС кластера: новая функция в Windows Server2016, которая позволяет администратору обновлять ОС узлов кластера с Windows Server2012R2 до Windows Server2016, не останавливая рабочие нагрузки Hyper-V или масштабируемого файлового сервера. Эта функция позволяет избежать простоя, который может нарушать соглашения об уровне обслуживания. Подробнее эта новая функция рассматривается в статье [Последовательное обновление ОС кластера](https://technet.microsoft.com/windows-server-docs/failover-clustering/cluster-operating-system-rolling-upgrade).

## <a name="license-conversion"></a>Преобразование лицензии
для некоторых версий ОС можно перейти с определенного выпуска версии на другой выпуск той же версии за один шаг с помощью простой команды и соответствующего лицензионного ключа. Это называется **преобразованием лицензии**. Например, если ваш сервер работает под управлением Windows Server2016 Standard, вы можете преобразовать его в Windows Server2016 Datacenter. В некоторых выпусках Windows Server также можно свободно выбирать переход на оригинальную версию, версию с корпоративным лицензированием и розничную версию с помощью той же команды и соответствующего ключа.

## <a name="upgrade"></a>Обновление с более ранней версии:
Если вы хотите сохранить существующее оборудование и все роли сервера, которые вы настроили, без сжатия сервера, **обновление с более ранней версии** является подходящим вариантом, и для этого существует множество способов. В классическом обновлении вы переходите с более старой операционной системы на более новую, сохраняя свои параметры, роли сервера и данные. Например, если ваш сервер работает под управлением Windows Server 2012 R2, вы можете обновить его до Windows Server 2016. Однако не все устаревшие операционные системы имеют канал к каждой новой ОС.
 
>[!NOTE]
>Обновление лучше всего работает на виртуальных машинах, где для успешного обновления не нужны специальные драйверы оборудования OEM.
 
Вы можете провести обновление с ознакомительной версии операционной системы на розничную, с более старой розничной версии на более новую или, в некоторых случаях, с корпоративного выпуска ОС на обычный.

Прежде чем начать обновление, изучите таблицы на этой странице, чтобы узнать, как перейти с имеющейся у вас ОС на более новую.

Подробнее о различиях между вариантами установки, доступными для Windows Server 2016 Technical Preview, включая компоненты, устанавливаемые в каждом случае, и параметры управления, доступные после установки, см. в статье [Windows Server 2016](https://go.microsoft.com/fwlink/?LinkId=828598).

>[!NOTE]
>При миграции или обновлении до любой версии Windows Server следует просмотреть и понять [политику сроков поддержки](https://support.microsoft.com/lifecycle) и период времени для этой версии и плана, соответственно. Вы можете [найти информацию о сроках](https://support.microsoft.com/lifecycle) для определенного выпуска Windows Server, который вас интересуют.
 
 
## <a name="upgrading-to-windows-server-2016"></a>Обновление до Windows Server 2016
Для получения подробных сведений, в том числе важных оговорок и ограничений по обновлению, преобразованию лицензий между выпусками Windows Server 2016 и преобразованию ознакомительных выпусков на розничные, см. статью [Поддерживаемые пути обновления для Windows Server 2016](https://go.microsoft.com/fwlink/?LinkId=828602).
 
>[!NOTE]
>Примечание. Обновления, переключающиеся с установки основных серверных компонентов на режим "Сервер с рабочим столом" (или наоборот), не поддерживаются. Если более старая операционная система, которую вы обновляете или преобразовываете, является установкой Server Core, результатом по-прежнему будет установка Server Core более новой операционной системы.
 
Краткая справочная таблица поддерживаемых путей обновления из более старых розничных выпусков Windows Server до розничных выпусков Windows Server 2016:


|Если вы используете эти версии и выпуски:|Доступно обновление до этих версий и выпусков:|
|--------------------------------|---------------------------------------|
|Windows Server2012 Standard|Windows Server2016 Standard или Datacenter|
|Windows Server 2012 Datacenter|Windows Server 2016 Datacenter|
|Windows Server 2012 R2 Standard|Windows Server2016 Standard или Datacenter|
|Windows Server 2012 R2 Datacenter|Windows Server 2016 Datacenter|
|Hyper-V Server 2012 R2|Hyper-V Server 2016 (с использованием компонента последовательного обновления ОС кластера)|
|Windows Server 2012 R2 Essentials|Windows Server2016 Essentials|
|Windows Storage Server 2012 Standard|Windows Storage Server2016 Standard|
|Windows Storage Server 2012 Workgroup|Windows Storage Server2016 Workgroup|
|Windows Storage Server 2012 R2 Standard|Windows Storage Server2016 Standard|
|Windows Storage Server 2012 R2 Workgroup|Windows Storage Server2016 Workgroup|
 
### <a name="license-conversion"></a>Преобразование лицензии
Вы можете преобразовать Windows Server 2016 Standard (розничную версию) в Windows Server 2016 Datacenter (розничную версию).

Вы можете преобразовать Windows Server 2016 Essentials (розничную версию) в Windows Server 2016 Standard (розничную версию).

Вы можете перейти с ознакомительной версии Windows Server2016 Standard, Windows Server2016 Standard (розничная версия) либо Datacenter (розничная версия).

Вы можете перейти с ознакомительной версии Windows Server 2016 Datacenter на Windows Server 2016 Datacenter (розничную).
 
## <a name="upgrading-to-windows-server-2012-r2"></a>Обновление до Windows Server 2012 R2
Для получения подробных сведений, в том числе важных оговорок и ограничений по обновлению, преобразованию лицензий между выпусками Windows Server 2012 R2 и преобразованию ознакомительных выпусков на розничные, см. статью [Варианты обновления для Windows Server 2012 R2](https://technet.microsoft.com/library/dn303416.aspx).

Краткая справочная таблица поддерживаемых путей обновления из более старых розничных выпусков Windows Server до розничных выпусков Windows Server 2012 R2:

|Используемая версия|Доступно обновление до следующих выпусков|
|-------------------------|---------------------------|
|Windows Server 2008 R2 Datacenter с пакетом обновления 1|Windows Server 2012 R2 Datacenter|
|Windows Server 2008 R2 Enterprise с пакетом обновления 1|Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter|
|Windows Server 2008 R2 Standard с пакетом обновления 1|Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter|
|Windows Web Server 2008 R2 с пакетом обновления 1|Windows Server 2012 R2 Standard|
|Windows Server 2012 Datacenter|Windows Server 2012 R2 Datacenter|
|Windows Server2012 Standard|Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter|
|Hyper-V Server 2012|Hyper-V Server 2012 R2|

### <a name="license-conversion"></a>Преобразование лицензии
Вы можете преобразовать Windows Server 2012 Standard (розничную версию) в Windows Server 2012 Datacenter (розничную версию).

Вы можете преобразовать Windows Server 2012 Essentials (розничную версию) в Windows Server 2012 Standard (розничную версию).

Вы можете перейти с ознакомительной версии Windows Server 2012 Standard, Windows Server 2012 Standard (розничная версия) либо Datacenter (розничная версия).

## <a name="upgrading-to-windows-server-2012"></a>Обновление до Windows Server 2012
Для получения подробных сведений, в том числе оговорок и ограничений по обновлению и преобразованию ознакомительных версий в розничные, см. статью [Ознакомительные версии и параметры обновления к Windows Server 2012](https://technet.microsoft.com/library/jj574204.aspx).
 
Краткая справочная таблица поддерживаемых путей обновления из более старых розничных выпусков Windows Server до розничных выпусков Windows Server 2012:

|Используемая версия|Доступно обновление до следующих выпусков|
|--------------------------|--------------------------|
|Windows Server 2008 Standard с SP2 или Windows Server 2008 Enterprise с SP2|Windows Server 2012 Standard, Windows Server 2012 Datacenter|
|Windows Server 2008 Datacenter с пакетом обновления 2 (SP2)|Windows Server 2012 Datacenter|
|Windows Web Server 2008|Windows Server2012 Standard|
|Windows Server 2008 R2 Standard с SP1 или Windows Server 2008 R2 Enterprise с пакетом обновления 1|Windows Server 2012 Standard, Windows Server 2012 Datacenter|
|Windows Server 2008 R2 Datacenter с пакетом обновления 1|Windows Server 2012 Datacenter|
|Windows Web Server 2008 R2|Windows Server2012 Standard|

### <a name="license-conversion"></a>Преобразование лицензии
Вы можете преобразовать Windows Server 2012 Standard (розничную версию) в Windows Server 2012 Datacenter (розничную версию).

Вы можете преобразовать Windows Server 2012 Essentials (розничную версию) в Windows Server 2012 Standard (розничную версию).

Вы можете перейти с ознакомительной версии Windows Server 2012 Standard, Windows Server 2012 Standard (розничная версия) либо Datacenter (розничная версия).

## <a name="upgrading-from-windows-server-2008-r2-or-windows-server-2008"></a>Обновление с Windows Server 2008 R2 или Windows Server 2008

Как описано в разделе [обновление Windows Server 2008 и Windows Server 2008 R2](modernize-windows-server-2008.md), расширенная поддержка для Windows Server 2008 R2 или Windows Server 2008, заканчивается в января 2020 г. Чтобы обеспечить пропусков в поддержке, необходимо обновить до поддерживаемой версии Windows Server или повторного размещения в Azure, переместив [специализированных ВМ Windows Server 2008 R2](uploading-specialized-WS08-image-to-azure.md). Ознакомьтесь с [руководство по миграции для Windows Server](https://go.microsoft.com/fwlink/?linkid=872689) сведения и рекомендации по планированию миграции/обновления.

Для локальных серверов нет прямого пути обновления с Windows Server 2008 R2 до Windows Server 2016 или более поздней версии. Вместо этого сначала обновить до Windows Server 2012 R2, а затем [обновления до Windows Server 2016](#Upgrading-to-Windows-Server-2016).

Так как вы планируете обновление, учитывайте следующие рекомендации по средний обновления до Windows Server 2012 R2.

  - Невозможно выполнение обновления на месте из 32-разрядной на 64-разрядные архитектуры или из одной сборки типа для другого типа (например, с fre до chk, например).

  - Обновление на месте поддерживаются только на одном языке. Нельзя обновить с одного языка на другой.

  - Установка основных серверных компонентов Windows Server 2008 невозможно перенести на Windows Server 2012 R2 с помощью графического интерфейса пользователя сервера (называемых «Server с полный рабочий стол» в Windows Server). Вы можете core установку обновленного сервера к серверу с полным рабочим столом, но только в Windows Server 2012 R2. Windows Server 2016 и более поздних версий *не* поддерживают переключение с основных серверных компонентов на полный рабочий стол, поэтому этот коммутатор перед обновлением до Windows Server 2016.
  
Дополнительные сведения, ознакомьтесь с [ознакомительные версии и варианты обновления для Windows Server 2012](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574204\(v=ws.11\)), включающий сведения об обновлении конкретной роли.

