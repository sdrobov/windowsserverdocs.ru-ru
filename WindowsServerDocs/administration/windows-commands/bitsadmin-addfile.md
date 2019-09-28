---
title: bitsadmin addfile
description: Раздел команд Windows для **битсадмин AddFile** . добавляет файл в указанное задание.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b31aa93-0364-465b-af36-754968825989
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8dfddda92e506dbfca2a47394a310edf16fe78aa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382042"
---
# <a name="bitsadmin-addfile"></a>bitsadmin addfile

Добавляет файл в указанное задание.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /AddFile <Job> <RemoteURL> <LocalName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|ремотеурл|URL-адрес файла на сервере.|
|Локально|Имя файла на локальном компьютере. *LocalName* должно содержать абсолютный путь к файлу.|

## <a name="BKMK_examples"></a>Примеров

Добавьте файл в задание. Повторите этот вызов для каждого файла, который нужно добавить. Если несколько заданий используют *мидовнлоаджоб* в качестве имени, необходимо заменить *мидовнлоаджоб* на GUID задания для уникальной идентификации задания.
```
C:\>bitsadmin /addfile myDownloadJob http://downloadsrv/10mb.zip c:\10mb.zip
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)