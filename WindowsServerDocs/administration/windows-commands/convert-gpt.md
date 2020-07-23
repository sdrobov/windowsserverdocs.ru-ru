---
title: convert gpt
description: Справочная статья по команде Convert GPT, которая преобразует пустой базовый диск с стилем разделов основной загрузочной записи (MBR) в базовый диск с стилем разделов таблицы разделов GPT.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b3b1b747-0a7a-4be2-8487-2c4be16ee190
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2384ea5a94de64051dc45caecd88e08960b567b0
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86958536"
---
# <a name="convert-gpt"></a>convert gpt

Преобразует пустой базовый диск с стилем разделов основной загрузочной записи (MBR) в базовый диск с стилем разделов GPT. Для выполнения этой операции необходимо выбрать базовый MBR-диск. Используйте [команду Выбор диска](select-disk.md) , чтобы выбрать базовый диск и переместить фокус на него.

> [!IMPORTANT]
> Диск должен быть пустым, чтобы преобразовать его в базовый диск. Создайте резервную копию данных, а затем удалите все разделы или тома перед преобразованием диска. Необходимый минимальный размер диска для преобразования в GPT составляет 128 МБ.

> [!NOTE]
> Инструкции по использованию этой команды см. [в разделе Изменение диска основной загрузочной записи на диск с таблицей разделов GUID](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc725671(v=ws.11)).

## <a name="syntax"></a>Синтаксис

```
convert gpt [noerr]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

## <a name="examples"></a>Примеры

Чтобы преобразовать базовый диск из стиля раздела MBR в стиль раздела GPT, введите:

```
convert gpt
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [преобразовать команду](convert.md)
