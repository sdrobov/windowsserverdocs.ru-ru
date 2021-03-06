---
title: tsprof
description: Справочная статья по тспроф, которая копирует данные пользовательской конфигурации службы удаленных рабочих столов от одного пользователя к другому.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 27047868-b706-4208-b7e0-1437a2325dd3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3abaf2413348edd723962ad99a19be5aa435a495
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86954876"
---
# <a name="tsprof"></a>tsprof

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Копирует службы удаленных рабочих столов сведения о конфигурации пользователя из одного пользователя в другой.
Службы удаленных рабочих столов сведения о конфигурации пользователя отображаются в службы удаленных рабочих столов расширениях локальным пользователям и группам, а также пользователям и компьютерам Active Directory.

**тспроф** также может задать путь к профилю для пользователя.



> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](/previous-versions/orphan-topics/ws.11/hh831527(v=ws.11)) в библиотеке TechNet по Windows Server.

## <a name="syntax"></a>Синтаксис
```
tsprof /update {/domain:<DomainName> | /local} /profile:<path> <UserName>
tsprof /copy {/domain:<DomainName> | /local} [/profile:<path>] <Src_usr> <Dest_usr>
tsprof /q {/domain:<DomainName> | /local} <UserName>
```

### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/update|Обновляет сведения о пути к профилю для <*имени пользователя*> в домене <*имя_домена*> *в <.*|
|/Domain\<DomainName>|Указывает имя домена, в котором применяется операция.|
|/Local|Применяет операцию только к локальным учетным записям пользователей.|
|загружать\<path>|Указывает путь к профилю, отображаемый в службы удаленных рабочих столов расширениях в оснастке "Локальные пользователи и группы" и "пользователи и компьютеры Active Directory".|
|\<UserName>|Указывает имя пользователя, для которого необходимо обновить или запросить путь к профилю сервера.|
|/Copy|Копирует сведения о конфигурации пользователя из \<*SourceUser*> в \<*DestinationUser*> и обновляет сведения о пути к профилю для \<*DestinationUser*> на \<*Profilepath*> . \<*SourceUser*>И, и \<*DestinationUser*> должны быть либо локальными, либо должны находиться в домене \<*DomainName*> .|
|\<Src_usr>|Указывает имя пользователя, от которого необходимо скопировать сведения о конфигурации пользователя.|
|\<Dest_usr>|Указывает имя пользователя, которому необходимо скопировать сведения о конфигурации пользователя.|
|/q|Отображает текущий путь к профилю пользователя, для которого требуется запросить путь к профилю сервера.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Комментарии
-   Команда **тспроф** доступна только в том случае, если служба роли сервера терминалов установлена на компьютере с windows Server 2008 или службой роли узла сеансов удаленных рабочих столов на компьютере под windows Server 2008 R2.

## <a name="examples"></a>Примеры
-   Чтобы скопировать сведения о конфигурации пользователя из LocalUser1 в LocalUser2, введите:
    ```
    tsprof /copy /local LocalUser1 LocalUser2
    ```
-   Чтобы установить службы удаленных рабочих столов путь к профилю для LocalUser1 в каталог с именем к:\профилес, введите:
    ```
    tsprof /update /local /profile:c:\profiles LocalUser1
    ```

## <a name="additional-references"></a>Дополнительные ссылки
- Ключ синтаксиса [командной строки](command-line-syntax-key.md) 
 [Справочник по командам служб терминалов службы удаленных рабочих столов](remote-desktop-services-terminal-services-command-reference.md)
