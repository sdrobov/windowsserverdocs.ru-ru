---
title: convert basic
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61329896-3b56-4959-8d58-45cbe18ba860
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5a5aef930689e809b9b697e5f428177610ff723b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862405"
---
# <a name="convert-basic"></a>convert basic



Преобразует пустого динамического диска в базовом диске.

Инструкции о том, как использовать эту команду, см. в разделе [изменить динамический диск обратно на базовом диске](https://go.microsoft.com/fwlink/?LinkId=207048) (https://go.microsoft.com/fwlink/?LinkId=207048).

## <a name="syntax"></a>Синтаксис

```
convert basic [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|

## <a name="remarks"></a>Примечания

> [!IMPORTANT]
> Диск должен быть пустым, чтобы преобразовать его в базовом диске. Резервное копирование данных, а затем удалите все разделы или тома перед преобразованием диска.
-   Для успешного выполнения этой операции необходимо выбрать динамический диск. Используйте **выберите диск** команду, чтобы выбрать динамический диск и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Для преобразования выбранного динамического диска в basic, введите следующую команду:
```
convert basic
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

