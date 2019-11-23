---
title: Откат команду scwcmd
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4fd9f89b-0420-420a-ad20-4a328636b1e7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3f089ea3e6e5d5b95080356dd239272b95a76b37
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371212"
---
# <a name="scwcmd-rollback"></a>Scwcmd: rollback

> Область применения: Windows Server 2012 R2, Windows Server 2012

Применяет последнюю доступную политику отката, а затем удаляет эту политику отката.

## <a name="syntax"></a>Синтаксис

```
scwcmd rollback /m:<ComputerName> [/u:<UserName>] [/pw:<Password>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/m:\<ComputerName >|Указывает имя NetBIOS, DNS-имя или IP-адрес компьютера, на котором должна быть выполнена операция отката.|
|/u:\<имя пользователя >|Указывает альтернативную учетную запись пользователя, используемую при удаленном откате. Значение по умолчанию — вошедший в систему пользователь.|
|/ПВ:\<пароль >|Указывает альтернативные учетные данные пользователя для использования при удаленном откате. Значение по умолчанию — вошедший в систему пользователь.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Замечания

Команду scwcmd. exe доступен только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="BKMK_Examples"></a>Примеров

Чтобы выполнить откат политики безопасности на компьютере с IP-адресом 172.16.0.0, введите:
```
scwcmd rollback /m:172.16.0.0
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)