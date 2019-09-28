---
title: Управление — состояние BDE
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1444a360-fabf-4dd3-b67f-188e6ea3fa5b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 235db54ef2361c0e95c66b15a15be7f188fb74d9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373865"
---
# <a name="manage-bde-status"></a>Manage-bde: Status



Предоставляет следующие сведения обо всех дисках на компьютере. независимо от того, защищены ли они с помощью BitLocker:
-   Size
-   Версия BitLocker
-   Состояние преобразования
-   Зашифровано в процентах
-   Метод шифрования
-   Состояние защиты
-   Состояние блокировки
-   Поле идентификации
-   Предохранители ключа

Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -status [<Drive>] [-protectionaserrorlevel] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0Drive >|Представляет букву диска, за которой следует двоеточие.|
|-протектионасеррорлевел|Приводит к тому, что программа командной строки Manage-bde отправляет код возврата 0, когда том защищен, и 1, если том не защищен. чаще всего используется для пакетных сценариев, чтобы определить, защищен ли диск BitLocker. Можно также использовать параметр **-p** в качестве сокращенной версии этой команды.|
|-ComputerName|Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды.|
|\<Имя >|Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или/?|Отображает краткую справку в командной строке.|
|-Help или-h|Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеров

В следующем примере показано использование команды **-Status** для вывода состояния диска C.
```
manage-bde –status C:
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Управление — BDE](manage-bde.md)