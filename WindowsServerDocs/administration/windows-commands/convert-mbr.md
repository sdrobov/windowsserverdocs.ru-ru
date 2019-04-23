---
title: convert mbr
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a635a4c0-af73-4330-b021-51d483424537
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: da8d62567863bc38a5aa0b35a8f3fe4ee24cc888
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59834615"
---
# <a name="convert-mbr"></a>convert mbr



Преобразует пустой базовый диск со стилем разделов таблицы разделов GUID (GPT) в базовый диск со стилем раздела основная загрузочная запись (MBR).

> [!IMPORTANT]
> Диск должен быть пустым, чтобы преобразовать его в MBR-диска. Резервное копирование данных, а затем удалите все разделы или тома перед преобразованием диска.

Инструкции о том, как использовать эту команду, см. в разделе [преобразование диска таблицы разделов GUID в диск с основной загрузочной записью](https://go.microsoft.com/fwlink/?LinkId=207050) (https://go.microsoft.com/fwlink/?LinkId=207050).

## <a name="syntax"></a>Синтаксис

```
convert mbr [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Для успешного выполнения этой операции необходимо выбрать базовый диск. Используйте **выберите диск** команду, чтобы выбрать базовый диск и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Чтобы преобразовать базовый диск из стиля раздела GPT стиля раздела MBR, введите >:
```
convert mbr
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

