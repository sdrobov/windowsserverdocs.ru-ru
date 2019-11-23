---
title: Управление обновлением BDE
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23bfa824-6ff0-44cc-9b8b-b199a769fb8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d426af59f5acc958768b316f363bf78ea249b3a7
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373849"
---
# <a name="manage-bde-upgrade"></a>Manage-bde: обновление



Обновляет версию BitLocker. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -upgrade [<Drive>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|> \<диска|Представляет букву диска, за которой следует двоеточие.|
|-ComputerName|Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды.|
|Имя \<>|Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или/?|Отображает краткую справку в командной строке.|
|-Help или-h|Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеров

В следующем примере показано использование команды **-Upgrade** для обновления шифрования BitLocker на диске C.
```
manage-bde –upgrade C:
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Управление — BDE](manage-bde.md)
-   [Обновление компьютера, защищенного с помощью BitLocker, с Windows Vista на Windows 7](https://technet.microsoft.com/library/ee424325(v=ws.10).aspx)