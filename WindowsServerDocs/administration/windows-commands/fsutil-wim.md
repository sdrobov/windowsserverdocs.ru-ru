---
title: fsutil wim
description: Справочная статья по команде fsutil WIM, которая предоставляет функции для обнаружения и управления файлами, поддерживающими образ Windows (WIM).
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: 6c6ff819-f349-4aea-b0be-1f637f631736
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 791eb80942187b0a0309097b2b785fb3dcea88ec
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931416"
---
# <a name="fsutil-wim"></a>fsutil wim

> Применяется к: Windows Server (Semi-Annual Channel), Windows Server 2019, Windows Server 2016, Windows 10

Предоставляет функции для обнаружения и управления файлами, поддерживающими образ Windows (WIM).

## <a name="syntax"></a>Синтаксис

```
fsutil wim [enumfiles] <drive name> <data source>
fsutil wim [enumwims] <drive name>
fsutil wim [queryfile] <filename>
fsutil wim [removewim] <drive name> <data source>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| енумфилес | Перечисляет файлы с резервным копированием WIM. |
| `<drive name>` | Указывает имя диска. |
| `<data source>` | Указывает источник данных. |
| енумвимс | Перечисляет резервные WIM-файлы. |
| куерифиле | Запросы, если файл поддерживается WIM, и, если это так, отображает сведения о WIM-файле. |
| `<filename>` | Указывает имя файла. |
| ремовевим | Удаляет WIM из резервных файлов. |

### <a name="examples"></a>Примеры

Чтобы перечислить файлы для диска C: из источника данных 0, введите:

```
fsutil wim enumfiles C: 0
```

Чтобы перечислить резервные WIM-файлы для диска C:, введите:

```
fsutil wim enumwims C:
```

Чтобы узнать, поддерживается ли файл WIM, введите:

```
fsutil wim C:\Windows\Notepad.exe
```

Чтобы удалить WIM из резервных файлов для тома C: и источника данных 2, введите:

```
fsutil wim removewims C: 2
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [fsutil](fsutil.md)
