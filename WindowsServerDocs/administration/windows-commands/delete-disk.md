---
title: delete disk
description: Справочная статья по команде "удалить диск", которая удаляет отсутствующий динамический диск из списка дисков.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 44079900-e4ed-49d0-81e4-d652c38cd636
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 55eabb19e10a7ca6fe4dd705ab91961919bb2b7c
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86958406"
---
# <a name="delete-disk"></a>delete disk

Удаляет отсутствующий динамический диск из списка дисков.

> [!NOTE]
> Подробные инструкции по использованию этой команды см. [в разделе Удаление отсутствующего динамического диска](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc753029(v=ws.11)).

## <a name="syntax"></a>Синтаксис

```
delete disk [noerr] [override]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |
| override | Позволяет программе DiskPart удалять все простые тома на диске. Если диск содержит половину зеркального тома, половина зеркала на диске удаляется. Команда удалить переопределение диска завершается сбоем, если диск входит в том RAID-5. |

## <a name="examples"></a>Примеры

Чтобы удалить отсутствующий динамический диск из списка дисков, введите:

```
delete disk
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [удалить команду](delete.md)
