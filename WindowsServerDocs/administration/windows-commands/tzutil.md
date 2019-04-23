---
title: tzutil
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bcf6e007-c9b6-4df5-83c5-ed7b4b1b5913
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 41a46ea7974b67cc557973484428480e7beb5484
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59876805"
---
# <a name="tzutil"></a>tzutil

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Windows отображает время служебной программы зоны. 
## <a name="syntax"></a>Синтаксис
```
tzutil [/?] [/g] [/s <timeZoneID>[_dstoff]] [/l]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/?|Отображение справки в командной строке.|
|/g|Отображает идентификатор текущего часового пояса|
|/s \<timeZoneID>[_dstoff]|Задает текущий часовой пояс, используя идентификатор указанного часового пояса. **_Dstoff** суффикс отключает корректировки летнего времени для часового пояса, (где применимо).|
|/l|списки все истории зоны идентификаторы и отображаемые имена. Выходные данные будут:<br /><br />-   \<отображаемое имя ><br />-   \<Идентификатор часового пояса >|

## <a name="remarks"></a>Примечания
Код выхода **0** указывает команда выполнена успешно.

## <a name="BKMK_Examples"></a>Примеры
Чтобы отобразить идентификатор текущего часового пояса, введите следующую команду:
```
tzutil /g
```
Чтобы установить по стандартному тихоокеанскому времени текущего часового пояса, введите следующую команду:
```
tzutil /s Pacific Standard time
```
Для задания по стандартному тихоокеанскому времени текущего часового пояса и отключает корректировки летнее время, введите следующую команду:
```
tzutil /s Pacific Standard time_dstoff
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)

