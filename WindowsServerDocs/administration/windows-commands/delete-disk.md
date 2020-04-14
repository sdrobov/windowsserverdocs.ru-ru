---
title: удалить диск
description: Команды Windows для удаления диска, в результате чего в списке дисков удаляется отсутствующий динамический диск.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 44079900-e4ed-49d0-81e4-d652c38cd636
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1a767e0689d5fbabb193df37528a0909ab63a1ab
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846657"
---
# <a name="delete-disk"></a>удалить диск

Удаляет отсутствующий динамический диск из списка дисков.

Инструкции по использованию этой команды см. [в разделе Удаление отсутствующего динамического диска](https://go.microsoft.com/fwlink/?LinkId=207055) (https://go.microsoft.com/fwlink/?LinkId=207055).

## <a name="syntax"></a>Синтаксис

```
delete disk [noerr] [override]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Noerr|Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки.|
|override|Позволяет программе DiskPart удалять все простые тома на диске. Если диск содержит половину зеркального тома, половина зеркала на диске удаляется. Команда удалить переопределение диска завершается сбоем, если диск входит в том RAID-5.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы удалить отсутствующий динамический диск из списка дисков, введите:
```
delete disk
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

