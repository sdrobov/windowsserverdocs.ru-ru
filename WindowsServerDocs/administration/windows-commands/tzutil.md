---
title: tzutil
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 347254bd5a00a8bfb4a80f20d518f1e0e8b593bf
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392306"
---
# <a name="tzutil"></a>tzutil

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает служебную программу часового пояса Windows. 
## <a name="syntax"></a>Синтаксис
```
tzutil [/?] [/g] [/s <timeZoneID>[_dstoff]] [/l]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/?|Отображение справки в командной строке.|
|/g|Отображает текущий идентификатор часового пояса.|
|/s \<timeZoneID > [_dstoff]|Задает текущий часовой пояс, используя указанный идентификатор часового пояса. Суффикс **_dstoff** отключает корректировки перехода на летнее время для часового пояса (если применимо).|
|/l|Список всех допустимых идентификаторов часовых поясов и отображаемых имен. Выходные данные будут:<br /><br />-    @ no__t-1display имя ><br />-    @ no__t-1time идентификатор зоны >|

## <a name="remarks"></a>Примечания
Код выхода **0** указывает, что команда выполнена успешно.

## <a name="BKMK_Examples"></a>Примеров
Чтобы отобразить текущий идентификатор часового пояса, введите:
```
tzutil /g
```
Чтобы задать для текущего часового пояса стандартное тихоокеанское время, введите:
```
tzutil /s Pacific Standard time
```
Чтобы задать для текущего часового пояса стандартное тихоокеанское время и отключить настройку перехода на летнее время, введите:
```
tzutil /s Pacific Standard time_dstoff
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

