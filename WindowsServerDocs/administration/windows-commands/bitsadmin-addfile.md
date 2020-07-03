---
title: bitsadmin addfile
description: Справочная статья по команде битсадмин AddFile, которая добавляет файл к указанному заданию.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1b31aa93-0364-465b-af36-754968825989
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 817a6d3af81d88e571db17c3f57dc129130b2783
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927107"
---
# <a name="bitsadmin-addfile"></a>bitsadmin addfile

Добавляет файл в указанное задание.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /addfile <job> <remoteURL> <localname>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| ремотеурл | URL-адрес файла на сервере. |
| localname | Имя файла на локальном компьютере. *LocalName* должно содержать абсолютный путь к файлу. |

## <a name="examples"></a>Примеры

Чтобы добавить файл в задание, выполните следующие действия.

```
bitsadmin /addfile myDownloadJob http://downloadsrv/10mb.zip c:\10mb.zip
```

Повторите этот вызов для каждого добавляемого файла. Если несколько заданий используют *мидовнлоаджоб* в качестве имени, необходимо заменить *мидовнлоаджоб* на GUID задания для уникальной идентификации задания.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
