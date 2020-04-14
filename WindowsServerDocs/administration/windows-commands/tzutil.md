---
title: tzutil
description: Раздел команд Windows для tzutil, в котором отображается служебная программа часового пояса Windows.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bcf6e007-c9b6-4df5-83c5-ed7b4b1b5913
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 330ee1eb4318df5aca1a5bb1a456711cd103c467
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832347"
---
# <a name="tzutil"></a>tzutil

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает служебную программу часового пояса Windows. 

## <a name="syntax"></a>Синтаксис
```
tzutil [/?] [/g] [/s <timeZoneID>[_dstoff]] [/l]
```
#### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/?|Отображает справку в командной строке.|
|/g|Отображает текущий идентификатор часового пояса.|
|/s \<Тимезонеид > [_dstoff]|Задает текущий часовой пояс, используя указанный идентификатор часового пояса. Суффикс **_dstoff** отключает корректировки перехода на летнее время для часового пояса (если применимо).|
|/l|Список всех допустимых идентификаторов часовых поясов и отображаемых имен. Выходные данные будут:<p>-   \<отображаемое имя ><br />-   идентификатор часового пояса \<>|

## <a name="remarks"></a>Примечания
Код выхода **0** указывает, что команда выполнена успешно.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров
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
## <a name="additional-references"></a>Дополнительные материалы
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

