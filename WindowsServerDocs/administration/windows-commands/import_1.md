---
title: импорт
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b9d2751-7637-4738-83b0-8c578eb28f27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 379d5923a9355db2965b56c27cedd207b1b63006
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59885995"
---
# <a name="import"></a>импорт



Импортирует внешней группы в группе дисков на локальном компьютере.

## <a name="syntax"></a>Синтаксис

```
import [noerr]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|

## <a name="remarks"></a>Примечания

-   Команда импорта импортирует каждый диск, находящийся в той же группе, что и диск с фокусом.
-   Для успешного выполнения этой операции необходимо выбрать динамический диск в внешней группы. Используйте **выберите диск** команду, чтобы выбрать диск и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Чтобы импортировать каждый диск, находящийся в той же группе диск как диск с фокусом в группе дисков на локальном компьютере, введите следующую команду:
```
import
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

