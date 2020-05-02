---
title: Откат команду scwcmd
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4fd9f89b-0420-420a-ad20-4a328636b1e7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0cd4eeec1113717a40dca43f0320f2db3c4c414e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722135"
---
# <a name="scwcmd-rollback"></a>Scwcmd: rollback

> Область применения: Windows Server 2012 R2, Windows Server 2012

Применяет последнюю доступную политику отката, а затем удаляет эту политику отката.

## <a name="syntax"></a>Синтаксис

```
scwcmd rollback /m:<ComputerName> [/u:<UserName>] [/pw:<Password>]
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/m:\<имя_компьютера>|Указывает имя NetBIOS, DNS-имя или IP-адрес компьютера, на котором должна быть выполнена операция отката.|
|/u:\<имя_пользователя>|Указывает альтернативную учетную запись пользователя, используемую при удаленном откате. Значение по умолчанию — вошедший в систему пользователь.|
|/ПВ:\<пароль>|Указывает альтернативные учетные данные пользователя для использования при удаленном откате. Значение по умолчанию — вошедший в систему пользователь.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Команду scwcmd. exe доступен только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="examples"></a>Примеры

Чтобы выполнить откат политики безопасности на компьютере с IP-адресом 172.16.0.0, введите:
```
scwcmd rollback /m:172.16.0.0
```

## <a name="additional-references"></a>Дополнительные ссылки

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)