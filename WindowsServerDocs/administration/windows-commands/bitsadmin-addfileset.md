---
title: bitsadmin addfileset
description: Справочный раздел по команде битсадмин аддфилесет, который добавляет один или несколько файлов в указанное задание.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75466994-262f-4724-b14d-f813c5397675
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d610c1330818cf820923b6d4f2e3555dc477444b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718481"
---
# <a name="bitsadmin-addfileset"></a>bitsadmin addfileset

Добавляет один или несколько файлов к указанному заданию.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /addfileset <job> <textfile>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| textfile | Текстовый файл, каждая строка которого содержит удаленное и локальное имя файла. **Примечание.** Имена должны быть разделены пробелами. Строки, начинающиеся `#` с символа, обрабатываются как комментарии. |

## <a name="examples"></a>Примеры

```
bitsadmin /addfileset files.txt
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
