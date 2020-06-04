---
title: mklink
description: Справочный раздел по команде Mklink, который создает символьную или жесткую связь в каталоге или файле.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0ce4df22-2dbc-48fc-9c16-b721ae85f857
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2f998533ce3184213786a341c2413e7323496e96
ms.sourcegitcommit: 5e313a004663adb54c90962cfdad9ae889246151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2020
ms.locfileid: "84354614"
---
# <a name="mklink"></a>mklink

Создает символьную или жесткую связь в каталоге или файле.

## <a name="syntax"></a>Синтаксис

```
mklink [[/d] | [/h] | [/j]] <link> <target>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /d | Создает символьную ссылку каталога. По умолчанию эта команда создает символьную ссылку на файл. |
| /h | Создает жесткую связь вместо символьной ссылки. |
| /j | Создает соединение с каталогом. |
| `<link>` | Указывает имя создаваемой символьной ссылки. |
| `<target>` | Указывает путь (относительный или абсолютный), на который ссылается Новая символьная ссылка. |
| /? | Отображение справки в командной строке. |

### <a name="examples"></a>Примеры

Чтобы создать и удалить символическую ссылку с именем, MyFolder и MyFile. File, из корневого каталога в каталог \Users\User1\Documents и файл example. File, находящийся в каталоге, введите:

```
mklink /d \MyFolder \Users\User1\Documents
mklink /h \MyFile.file \User1\Documents\example.file
rd \MyFolder
del \MyFile.file
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [команда del](del.md)

- [RD, команда](rd.md)

- [Новый элемент в Windows PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-6)
