---
title: cmdkey
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5fcd68ee-a14a-4b71-9300-c3f5c5d31e8e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7080a3ae28fed722f17cf8311aa1e2fd3bece41f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59854615"
---
# <a name="cmdkey"></a>cmdkey

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает, списков и удаляет сохраненные имена пользователей и пароли или учетные данные.

## <a name="syntax"></a>Синтаксис
```
cmdkey [{/add:<TargetName>|/generic:<TargetName>}] {/smartcard|/user:<UserName> [/pass:<Password>]} [/delete{:<TargetName>|/ras}] /list:<TargetName>
```
## <a name="parameters"></a>Параметры
|Параметры|Описание|
|-------|--------|
|/ add:<TargetName>|Добавляет в список имя пользователя и пароль.<br /><br />Требуется параметр <TargetName> определяющий имя компьютера или домена, которым будут связаны с данной записи.|
|Общие:<TargetName>|Добавляет в список общих учетных данных.<br /><br />Требуется параметр <TargetName> определяющий имя компьютера или домена, которым будут связаны с данной записи.|
|/ Smartcard|Загрузка учетных данных смарт-карты.|
|/ User:<UserName>|Указывает пользователя или имя учетной записи для данной записи. Если *UserName* — не указано, будет выдан запрос.|
|/PASS:<Password>|Указывает пароль для данной записи. Если *пароль* — не указано, будет выдан запрос.|
|/delete{:<TargetName> &#124; /ras}|Удаляет из списка имя пользователя и пароль. Если *TargetName* указано, что записи будут удалены. Если /ras указано, удаляется запись удаленного доступа.|
|/ List:<TargetName>|Отображает список имен пользователей и учетных данных. Если *TargetName* не указан, все сохраненные имена и отображаются учетные данные.|
|/?|Отображение справки в командной строке.|
## <a name="remarks"></a>Примечания
-   Если найден более одного смарт-карт в системе при использовании параметра командной строки/Smartcard **cmdkey** отображает сведения о всех доступных смарт-картах и предложит пользователю указать, какой из них следует использовать.
-   Пароли не отобразится, когда они хранятся.
## <a name="BKMK_examples"></a>Примеры
Чтобы вывести список всех имен пользователей и учетные данные, которые хранятся, введите следующую команду:
```
cmdkey /list
```
Чтобы добавить имя пользователя и пароль для пользователя Mikedan к компьютеру Server01 с помощью пароля Kleo, введите следующую команду:
```
cmdkey /add:server01 /user:mikedan /pass:Kleo
```
Чтобы добавить имя пользователя и пароль для пользователя Mikedan к компьютеру Server01 и запрашивать пароль при доступе к Server01, введите следующую команду:
```
cmdkey /add:server01 /user:mikedan
```
Чтобы удалить учетные данные, сохраненные при удаленном доступе, введите следующую команду:
```
cmdkey /delete /ras
```
Чтобы удалить учетные данные, хранящиеся в Server01, введите следующую команду:
```
cmdkey /delete:Server01
```
## <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
