---
title: Удалить раздел
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 65752312-cb16-46f6-870f-1b95c507b101
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bf9f456ad6ab3010493154da843b2b519754e250
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59816335"
---
# <a name="delete-partition"></a>Удалить раздел



Удаление раздела, имеющего фокус.

## <a name="syntax"></a>Синтаксис

```
delete partition [noerr] [override]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Переопределение|Позволяет программе DiskPart Удаление любого раздела, независимо от типа. Как правило DiskPart только позволяет удалять разделы с известными данными.|
|успешного|для использования в сценариях. При обнаружении ошибки, DiskPart продолжает обрабатывать команды, как если бы ошибки не было. Без этого параметра по ошибке будет возобновлено DiskPart завершить работу с кодом ошибки.|

## <a name="remarks"></a>Примечания

> [!CAUTION]
> Удаление раздела на динамическом диске можно удалить все динамические тома на диске, тем самым чего все данные и диск останется в поврежденном состоянии. Чтобы удалить это динамический том, всегда используйте **удалить том** command. Секции могут быть удалены из динамических дисков, но они не создается. Например можно удалить раздел нераспознанный таблица разделов GUID (GPT) на динамическом диске GPT. Удаление этого раздела не ведет к итоговый свободного места для их появления. Эта команда предназначена позволяет вам писать reclame пространства поврежденного автономного динамического диска в аварийной ситуации, где **чистой** невозможно использовать команду в DiskPart.
-   Невозможно удалить системный раздел, загрузочный раздел или любого раздела со сведениями active разбиения на страницы файла или сбой дампа.
-   Для успешного выполнения этой операции необходимо выбрать секцию. Используйте **выберите секцию** команду, чтобы выбрать раздел и перетянуть внимание к нему.

## <a name="BKMK_examples"></a>Примеры

Чтобы удалить секцию с фокусом, введите:
```
delete partition
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
