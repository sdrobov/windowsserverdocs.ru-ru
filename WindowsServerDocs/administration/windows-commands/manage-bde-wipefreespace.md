---
title: WipeFreeSpace готов
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b8d83a2a-c5c8-4019-9041-23d1d6abf282
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7cf99a9124f78189de223018608d9864e51d7897
ms.sourcegitcommit: 08eba714d3ceb5f2dfb5486d6b990da1aa4dcbdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65564693"
---
# <a name="manage-bde-wipefreespace"></a>готов: WipeFreeSpace



Очищает свободного места на томе, удаляя все фрагменты данных, которые могли существовать в пространстве. Выполните следующую команду на томе, который был зашифрован при помощи метода шифрования «Только используемого пространства» предоставляет тот же уровень защиты, что и метод шифрования «Full Volume Encryption». Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -WipeFreeSpace|-w [<Drive>] [-Cancel] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Диск >|Представляет букву диска, за которым следует двоеточие, пути GUID тома или подключенный том.|
|— Отмена|Отменяет его очистку свободного пространства, которое находится в процессе.|
|-computername|Указывает, что Manage-bde.exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать **- cn** как сокращенную версию этой команды.|
|\<Имя >|Представляет имя компьютера, на которой требуется изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или /?|Отображение кратких справки в командной строке.|
|-help или -h|Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеры

В следующем примере демонстрируется использование **-w** команду, чтобы создать Очистка свободного места на диске C.
```
manage-bde -w C:
```
В следующем примере демонстрируется использование **-w** с **-Отмена** параметр, чтобы отменить очистку свободного места на диске C.
```
manage-bde -w -Cancel C:
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Готов](manage-bde.md)