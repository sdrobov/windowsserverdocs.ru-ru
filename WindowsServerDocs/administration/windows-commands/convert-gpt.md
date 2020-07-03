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
ms.openlocfilehash: d8025e897a8ce7083b938e984f9a11b6c32ed312
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928951"
---
# <a name="convert-gpt"></a>convert gpt

Преобразует пустой базовый диск с стилем разделов основной загрузочной записи (MBR) в базовый диск с стилем разделов GPT. Для выполнения этой операции необходимо выбрать базовый MBR-диск. Используйте [команду Выбор диска](select-disk.md) , чтобы выбрать базовый диск и переместить фокус на него.

> [!IMPORTANT]
> Диск должен быть пустым, чтобы преобразовать его в базовый диск. Создайте резервную копию данных, а затем удалите все разделы или тома перед преобразованием диска. Необходимый минимальный размер диска для преобразования в GPT составляет 128 МБ.

> [!NOTE]
> Инструкции по использованию этой команды см. [в разделе Изменение диска основной загрузочной записи на диск с таблицей разделов GUID](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725671(v=ws.11)).

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
