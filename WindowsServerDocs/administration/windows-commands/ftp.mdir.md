---
title: ftp mdir
description: Справочная статья по команде FTP мдир, которая отображает список каталогов файлов и подкаталогов в удаленном каталоге.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90eec45b-558b-4b8d-bbe4-b56d98e1ca70
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5a4d1b00941d350776fd953607a5cc5da433993c
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926157"
---
# <a name="ftp-mdir"></a>ftp mdir

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает список каталогов файлов и подкаталогов в удаленном каталоге.

## <a name="syntax"></a>Синтаксис

```
mdir <remotefile>[...] <localfile>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<remotefile>` | Указывает каталог или файл, для которого требуется просмотреть список. Можно указать несколько *ремотефилес*. Введите дефис (-), чтобы использовать текущий рабочий каталог на удаленном компьютере. |
| `<localfile>` | Указывает локальный файл для хранения списка. Это обязательный параметр. Введите дефис (-) для отображения списка на экране. |

### <a name="examples"></a>Примеры

Чтобы вывести на экран список каталогов *Dir1* и *Dir2* , введите:

```
mdir dir1 dir2 -
```

Чтобы сохранить Объединенный каталог со списком *Dir1* и *Dir2* в локальном файле с именем *dirlist.txt*, введите:

```
mdir dir1 dir2 dirlist.txt
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
