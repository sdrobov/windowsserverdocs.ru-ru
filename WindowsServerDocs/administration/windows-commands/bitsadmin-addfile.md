---
title: bitsadmin addfile
description: Раздел команд Windows для **битсадмин AddFile**, который добавляет файл к указанному заданию.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1b31aa93-0364-465b-af36-754968825989
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 330e79eb2ba5a824cea54094f64ceb6f9cfd66b9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850967"
---
# <a name="bitsadmin-addfile"></a>bitsadmin addfile

Добавляет файл в указанное задание.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /AddFile <Job> <RemoteURL> <LocalName>
```

#### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Job | Отображаемое имя задания или идентификатор GUID. |
| ремотеурл | URL-адрес файла на сервере. |
| Локально | Имя файла на локальном компьютере. *LocalName* должно содержать абсолютный путь к файлу. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Добавьте файл в задание. Повторите этот вызов для каждого файла, который нужно добавить. Если несколько заданий используют *мидовнлоаджоб* в качестве имени, необходимо заменить *мидовнлоаджоб* на GUID задания для уникальной идентификации задания.

```
C:\>bitsadmin /addfile myDownloadJob http://downloadsrv/10mb.zip c:\10mb.zip
```

## <a name="additional-references"></a>Дополнительные материалы

- [Ключ синтаксиса командной строки](command-line-syntax-key.md)&copy;