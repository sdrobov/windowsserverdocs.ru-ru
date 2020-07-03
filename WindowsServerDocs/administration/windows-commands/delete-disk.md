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
ms.openlocfilehash: 5ba9f3c965d4746a5a61f06b99e4601a131ed79e
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928739"
---
# <a name="delete-disk"></a>delete disk

Удаляет отсутствующий динамический диск из списка дисков.

> [!NOTE]
> Подробные инструкции по использованию этой команды см. [в разделе Удаление отсутствующего динамического диска](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753029(v=ws.11)).

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
