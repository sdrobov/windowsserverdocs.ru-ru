---
title: готов changekey
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69463db9-7e03-47ff-b233-a95d5055725f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 991d05cb79e6596c3efb3e69b681203838cd8c20
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842095"
---
# <a name="manage-bde-changekey"></a>готов: changekey



Изменяет ключ запуска для диска операционной системы. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -changekey [<Drive>] [<PathToExternalKeyDirectory>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Диск >|Представляет букву диска, за которым следует двоеточие.|
|\<PathToExternalKeyDirectory >|Представляет расположение каталога, чтобы сохранить файл ключа внешних запуска, который может использоваться для разблокировки диска.|
|-computername|Указывает, что Manage-bde.exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать **- cn** как сокращенную версию этой команды.|
|\<Имя >|Представляет имя компьютера, на которой требуется изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или /?|Отображение кратких справки в командной строке.|
|-help или -h|Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеры

В следующем примере демонстрируется использование **- changekey** команду, чтобы создать новый ключ запуска на диске E для использования с шифрованием BitLocker на диске C.
```
manage-bde –changekey C: E:\
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Готов](manage-bde.md)