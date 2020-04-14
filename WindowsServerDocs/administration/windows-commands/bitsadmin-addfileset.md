---
title: bitsadmin addfileset
description: Раздел команд Windows для **битсадмин аддфилесет**, который добавляет один или несколько файлов в указанное задание.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75466994-262f-4724-b14d-f813c5397675
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1c4cff7dc8439fe8e1c54d1f5d231d1b487dc70c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850977"
---
# <a name="bitsadmin-addfileset"></a>bitsadmin addfileset

Добавляет один или несколько файлов к указанному заданию.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /addfileset <Job> <TextFile>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Job | Отображаемое имя задания или идентификатор GUID. |
| TextFile | Текстовый файл, каждая строка которого содержит удаленное и локальное имя файла. **Примечание.** Имена разделяются пробелами. Строки, начинающиеся с `#` символа, обрабатываются как комментарии. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

```
C:\>bitsadmin /addfileset files.txt
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)