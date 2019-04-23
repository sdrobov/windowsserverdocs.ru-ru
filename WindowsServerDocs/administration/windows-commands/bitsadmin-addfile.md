---
title: bitsadmin addfile
description: Раздел Windows команды для **bitsadmin addfile** -добавляет файл к указанному заданию.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 1c3027bdc4f3f8f3e3ca50400b2c5dbf33bf2bc5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59861755"
---
# <a name="bitsadmin-addfile"></a>bitsadmin addfile

Добавляет файл к указанному заданию.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /AddFile <Job> <RemoteURL> <LocalName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|RemoteURL|URL-адрес файла на сервере.|
|LocalName|Имя файла на локальном компьютере. *LocalName* должен содержать абсолютный путь к файлу.|

## <a name="BKMK_examples"></a>Примеры

Добавьте файл к заданию. Повторите этот вызов для каждого файла, который вы хотите добавить. Если использовать несколько заданий *myDownloadJob* в имени, необходимо заменить *myDownloadJob* с идентификатором GUID задания для уникальной идентификации задания.
```
C:\>bitsadmin /addfile myDownloadJob http://downloadsrv/10mb.zip c:\10mb.zip
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)