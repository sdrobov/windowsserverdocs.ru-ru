---
title: convert basic
description: Справочная статья по команде Convert Basic, которая преобразует пустой динамический диск в базовый.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 61329896-3b56-4959-8d58-45cbe18ba860
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a61c3d9fd8d708a41347f0bcf46aa627e960153c
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928988"
---
# <a name="convert-basic"></a>convert basic

Преобразует пустой динамический диск в базовый. Для выполнения этой операции должен быть выбран динамический диск. Используйте [команду Выбор диска](select-disk.md) , чтобы выбрать динамический диск и переместить фокус на него.

> [!IMPORTANT]
> Диск должен быть пустым, чтобы преобразовать его в базовый диск. Создайте резервную копию данных, а затем удалите все разделы или тома перед преобразованием диска.

> [!NOTE]
> Инструкции по использованию этой команды см. в разделе [Переключение динамического диска обратно на базовый диск](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc755238(v=ws.11)).

## <a name="syntax"></a>Синтаксис

```
convert basic [noerr]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

## <a name="examples"></a>Примеры

Чтобы преобразовать выбранный динамический диск в базовый, введите:

```
convert basic
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [преобразовать команду](convert.md)
