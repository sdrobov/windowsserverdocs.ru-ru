---
title: bitsadmin setreplyfilename
description: Раздел Windows команды для **bitsadmin setreplyfilename** -указать путь к файлу, содержащему ответ сервера.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c26d3342-0533-40b1-a13e-e09678232b25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b86d4137f661e9953d6d397b2fbc890393bbd8a0
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852875"
---
# <a name="bitsadmin-setreplyfilename"></a>bitsadmin setreplyfilename

Укажите путь к файлу, содержащему ответ сервера.

**БИТЫ 1.2 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetReplyFileName <Job> <Path>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Путь|Место для размещения ответ сервера|

## <a name="remarks"></a>Примечания

Допустимо только для задания отправки ответа.

## <a name="BKMK_examples"></a>Примеры

В следующем примере задается pathfor filename ответного задания с именем *myDownloadJob*.
```
C:\>bitsadmin /SetReplyFileName myDownloadJob c:\reply
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)