---
title: bitsadmin getreplyprogress
description: Раздел команд Windows для **битсадмин жетреплипрогресс** — получение размера и хода выполнения ответа сервера.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f7cb0b4-ad95-44fd-a35d-0ddf5fc0b0d0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c791fe98271b497e5ecf48338ab3bbb0cc50de98
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381241"
---
# <a name="bitsadmin-getreplyprogress"></a>bitsadmin getreplyprogress

Возвращает размер и ход ответа сервера.

**BITS 1,2 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetReplyProgress <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Примечания

Допустимо только для заданий отправки и ответа.

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается ход выполнения ответа для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetReplyProgress myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)