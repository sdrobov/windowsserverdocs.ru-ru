---
title: bitsadmin getreplydata
description: Раздел Windows команды для **bitsadmin getreplydata** -извлекает данные ответа сервера в шестнадцатеричном формате.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 819f97d5-b255-4b2d-9f63-0daa73915434
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 78d70a44d6881568c8d92db145fdf22a260ee8af
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59883825"
---
# <a name="bitsadmin-getreplydata"></a>bitsadmin getreplydata

Извлекает данные ответа сервера в шестнадцатеричном формате.

**БИТЫ 1.2 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetReplyData <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Допустимо только для задания отправки ответа.

## <a name="BKMK_examples"></a>Примеры

В следующем примере извлекаются данные ответа для задания с именем *myDownloadJob*.
```
C:\>bitsadmin /GetReplyData myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)