---
title: bitsadmin getreplydata
description: Раздел команд Windows для **битсадмин жетреплидата** — получает данные ответа сервера в шестнадцатеричном формате.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 7ebd3ee77e5d442467f49bb209c560f089f2271b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381281"
---
# <a name="bitsadmin-getreplydata"></a>bitsadmin getreplydata

Получает данные ответа сервера в шестнадцатеричном формате.

**BITS 1,2 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetReplyData <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Допустимо только для заданий отправки и ответа.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекаются данные ответа для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetReplyData myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)