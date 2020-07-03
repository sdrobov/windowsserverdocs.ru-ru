---
title: tzutil
description: Справочная статья по tzutil, в которой отображается служебная программа часового пояса Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bcf6e007-c9b6-4df5-83c5-ed7b4b1b5913
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 99d88057c88a55aaf529d238088f8422c33e9ba7
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937290"
---
# <a name="tzutil"></a>tzutil

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает служебную программу часового пояса Windows.

## <a name="syntax"></a>Синтаксис
```
tzutil [/?] [/g] [/s <timeZoneID>[_dstoff]] [/l]
```
#### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/?|Отображение справки в командной строке.|
|/g|Отображает текущий идентификатор часового пояса.|
|/s \<timeZoneID> [_dstoff]|Задает текущий часовой пояс, используя указанный идентификатор часового пояса. Суффикс **_dstoff** отключает корректировки перехода на летнее время для часового пояса (если применимо).|
|/l|Список всех допустимых идентификаторов часовых поясов и отображаемых имен. Выходные данные должны выглядеть следующим образом:<p>-   \<display name><br />-   \<time zone ID>|

## <a name="remarks"></a>Комментарии
Код выхода **0** указывает, что команда выполнена успешно.

## <a name="examples"></a>Примеры
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
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

