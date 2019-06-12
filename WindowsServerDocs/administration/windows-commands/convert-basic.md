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
ms.openlocfilehash: df1f999499154366304d59e0573ba921ab1af83d
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434242"
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
> -   Для успешного выполнения этой операции необходимо выбрать динамический диск. Используйте **выберите диск** команду, чтобы выбрать динамический диск и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Для преобразования выбранного динамического диска в basic, введите следующую команду:
```
convert basic
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

