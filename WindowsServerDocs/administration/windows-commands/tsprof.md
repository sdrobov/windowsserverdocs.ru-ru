---
title: tsprof
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 27047868-b706-4208-b7e0-1437a2325dd3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 77d0752f74d2f6031f83f805273650747d24cfee
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392316"
---
# <a name="tsprof"></a>tsprof

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует службы удаленных рабочих столов сведения о конфигурации пользователя из одного пользователя в другой.
Службы удаленных рабочих столов сведения о конфигурации пользователя отображаются в службы удаленных рабочих столов расширениях локальным пользователям и группам, а также пользователям и компьютерам Active Directory.

**тспроф** также может задать путь к профилю для пользователя.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.

## <a name="syntax"></a>Синтаксис
```
tsprof /update {/domain:<DomainName> | /local} /profile:<path> <UserName>
tsprof /copy {/domain:<DomainName> | /local} [/profile:<path>] <Src_usr> <Dest_usr>
tsprof /q {/domain:<DomainName> | /local} <UserName>
```

## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/Update|Обновляет сведения о пути к профилю для <*имени пользователя*> в домене <*имя_домена*>*в <.*|
|/Domain:\<имя_домена >|Указывает имя домена, в котором применяется операция.|
|/Local|Применяет операцию только к локальным учетным записям пользователей.|
|/profile:\<путь >|Указывает путь к профилю, отображаемый в службы удаленных рабочих столов расширениях в оснастке "Локальные пользователи и группы" и "пользователи и компьютеры Active Directory".|
|\<имя пользователя >|Указывает имя пользователя, для которого необходимо обновить или запросить путь к профилю сервера.|
|/Copy|Копирует сведения о конфигурации пользователя из \<*SourceUser*> в \<*DestinationUser*> и обновляет сведения о пути к профилю для \<*DestinationUser*> *в \<.* Оба \<*SourceUser*> и \<*DestinationUser*> должны быть локальными или должны находиться в домене \<*имя_домена*>.|
|\<Src_usr >|Указывает имя пользователя, от которого необходимо скопировать сведения о конфигурации пользователя.|
|\<Dest_usr >|Указывает имя пользователя, которому необходимо скопировать сведения о конфигурации пользователя.|
|/q|Отображает текущий путь к профилю пользователя, для которого требуется запросить путь к профилю сервера.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Замечания
-   Команда **тспроф** доступна только в том случае, если служба роли сервера терминалов установлена на компьютере с windows Server 2008 или службой роли узла сеансов удаленных рабочих столов на компьютере под windows Server 2008 R2.

## <a name="BKMK_examples"></a>Примеров
-   Чтобы скопировать сведения о конфигурации пользователя из LocalUser1 в LocalUser2, введите:
    ```
    tsprof /copy /local LocalUser1 LocalUser2
    ```
-   Чтобы установить службы удаленных рабочих столов путь к профилю для LocalUser1 в каталог с именем к:\профилес, введите:
    ```
    tsprof /update /local /profile:c:\profiles LocalUser1
    ```

#### <a name="additional-references"></a>Дополнительная справка
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[службы удаленных рабочих столов &#40;Справочник по&#41; командам служб терминалов](remote-desktop-services-terminal-services-command-reference.md)
