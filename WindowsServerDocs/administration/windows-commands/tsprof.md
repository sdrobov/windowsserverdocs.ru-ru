---
title: tsprof
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: e17d60126125fcd4b10373133dd61ca0db030290
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59836075"
---
# <a name="tsprof"></a>tsprof

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует сведения о конфигурации службы удаленных рабочих столов от одного пользователя в другое.
Сведения о конфигурации службы удаленных рабочих столов пользователя отображается в расширения служб удаленных рабочих столов для локальных пользователей и групп active directory пользователи и компьютеры.

**tsprof** можно также задать путь к профилю для пользователя.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы найти новые возможности в последней версии, см. в разделе [какие возможности служб удаленных рабочих столов в Windows Server 2012](https://technet.microsoft.com/library/hh831527) в технической библиотеке Windows Server.

## <a name="syntax"></a>Синтаксис
```
tsprof /update {/domain:<DomainName> | /local} /profile:<path> <UserName>
tsprof /copy {/domain:<DomainName> | /local} [/profile:<path>] <Src_usr> <Dest_usr>
tsprof /q {/domain:<DomainName> | /local} <UserName>
```

## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ Update|Обновления пути сведения о профиле для <*UserName*> в домене <*DomainName*> для <*путь_к_профилю*>.|
|/ domain:\<DomainName >|Указывает имя домена, в котором применяется операция.|
|/ локального|Применяет операцию только для учетных записей локальных пользователей.|
|/ profile:\<путь >|Указывает путь к профилю, показанной в расширения служб удаленных рабочих столов в локальных пользователей и групп active directory пользователи и компьютеры.|
|\<Имя пользователя >|Указывает имя пользователя, для которого вы хотите обновить или запросить путь к профилю сервера.|
|/ Copy|Копирует сведения о конфигурации из \< *SourceUser*> для \< *DestinationUser*> и обновляет сведения о пути профиля для \<  *DestinationUser*> для \< *путь_к_профилю*>. Оба \< *SourceUser*> и \< *DestinationUser*> должны быть локальными или должны находиться в домене \< *DomainName*> .|
|\<Src_usr>|Указывает имя пользователя, из которого требуется скопировать данные конфигурации пользователя.|
|\<Dest_usr>|Указывает имя пользователя, которому требуется скопировать данные конфигурации пользователя.|
|/q|Отображает текущий путь к профилю пользователя, для которого требуется запросить путь к профилю сервера.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания
-   **Tsprof** команда доступна только в случае, если вы установили службу роли сервера терминалов на компьютер под управлением Windows Server 2008 или узла сеансов удаленных рабочих Столов службу роли на компьютере под управлением Windows Server 2008 R2.

## <a name="BKMK_examples"></a>Примеры
-   Чтобы скопировать сведения о конфигурации из Локального_пользователя1 в папку Локальный_пользователь2, введите следующую команду:
    ```
    tsprof /copy /local LocalUser1 LocalUser2
    ```
-   Чтобы установить путь к профилю служб удаленных рабочих столов для Локального_пользователя1 в каталог с именем «c:\profiles», введите следующую команду:
    ```
    tsprof /update /local /profile:c:\profiles LocalUser1
    ```

#### <a name="additional-references"></a>Дополнительная справка
[Синтаксис командной строки Key](command-line-syntax-key.md)
[служб удаленных рабочих столов &#40;служб терминалов&#41; описанием команды](remote-desktop-services-terminal-services-command-reference.md)
