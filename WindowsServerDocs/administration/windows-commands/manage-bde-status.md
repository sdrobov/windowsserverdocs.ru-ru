---
title: состояние готов
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: d81808b57b1833ca30b95dc9d4b6aa0b0a4bdbaa
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59836565"
---
# <a name="manage-bde-status"></a>готов: состояние



Предоставляет следующие сведения о всех дисков на компьютере. ли они защищенными BitLocker:
-   Размер
-   Версии BitLocker
-   Состояние преобразования
-   Шифрование в процентах
-   Метод шифрования
-   Состояние защиты
-   Состояние блокировки
-   Поля идентификации
-   Предохранители ключа

Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -status [<Drive>] [-protectionaserrorlevel] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Диск >|Представляет букву диска, за которым следует двоеточие.|
|-protectionaserrorlevel|Вызывает средство командной строки Manage-bde для отправки код возврата 0 при использовании защищенного тома и 1, если том не защищен; Чаще всего используется для пакетных сценариев, чтобы определить, используется ли на диске, защищенных с помощью BitLocker. Можно также использовать **-p** как сокращенную версию этой команды.|
|-computername|Указывает, что Manage-bde.exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать **- cn** как сокращенную версию этой команды.|
|\<Имя >|Представляет имя компьютера, на которой требуется изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или /?|Отображение кратких справки в командной строке.|
|-help или -h|Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеры

В следующем примере демонстрируется использование **-состояние** команду, чтобы отобразить состояние диска C.
```
manage-bde –status C:
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Готов](manage-bde.md)