---
title: ftp mls
description: Справочная статья по команде FTP MLS, которая отображает сокращенный список файлов и подкаталогов в удаленном каталоге.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4738fd49-0e80-4bdf-a773-0f973db3a710
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2f3d5c6b595cf6f8261a4af742cef60d0c9e3abd
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957656"
---
# <a name="ftp-mls"></a>ftp mls

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сокращенный список файлов и подкаталогов в удаленном каталоге.

## <a name="syntax"></a>Синтаксис

```
mls <remotefile>[ ] <localfile>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<remotefile>` | Указывает файл, для которого требуется просмотреть список. При указании *ремотефилес*Используйте дефис для представления текущего рабочего каталога на удаленном компьютере. |
| `<localfile>` | Указывает локальный файл для хранения списка. При указании параметра *локальный_файл*Используйте дефис для отображения списка на экране. |

### <a name="examples"></a>Примеры

Чтобы отобразить сокращенный список файлов и подкаталогов для *Dir1* и *Dir2*, введите:

```
mls dir1 dir2 -
```

Чтобы сохранить сокращенный список файлов и подкаталогов для *Dir1* и *Dir2* в локальном файле *dirlist.txt*, введите:

```
mls dir1 dir2 dirlist.txt
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Дополнительные рекомендации по FTP](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
