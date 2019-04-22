---
title: Обновление готов
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: dc28dfc98a66a60172c812d12a16d03c078b79e1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59822285"
---
# <a name="manage-bde-upgrade"></a>готов: обновление



Обновление версии BitLocker. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -upgrade [<Drive>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Диск >|Представляет букву диска, за которым следует двоеточие.|
|-computername|Указывает, что Manage-bde.exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать **- cn** как сокращенную версию этой команды.|
|\<Имя >|Представляет имя компьютера, на которой требуется изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или /?|Отображение кратких справки в командной строке.|
|-help или -h|Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеры

В следующем примере демонстрируется использование **-обновление** команду, чтобы обновить шифрование BitLocker на диске C.
```
manage-bde –upgrade C:
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Готов](manage-bde.md)
-   [Обновление защищаемый BitLocker компьютер с Windows Vista до Windows 7](https://technet.microsoft.com/library/ee424325(v=ws.10).aspx)