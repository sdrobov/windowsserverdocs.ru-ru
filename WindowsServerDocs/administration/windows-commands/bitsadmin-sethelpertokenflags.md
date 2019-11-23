---
title: битсадмин сеселпертокенфлагс
description: Раздел команд Windows для **битсадмин сеселпертокенфлагс** — задает флаги использования для вспомогательного токена, связанного с заданием передачи BITS.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 6047c63677fac3311634ababb675be5301b7f3b5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380585"
---
# <a name="bitsadmin-sethelpertokenflags"></a>битсадмин сеселпертокенфлагс

Задает флаги использования для [вспомогательного токена](/windows/desktop/bits/helper-tokens-for-bits-transfer-jobs) , связанного с заданием передачи BITS.

**BITS 3,0 и более ранних версий**: не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetHelperTokenFlags <Job> <Flags>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID.|
|Флажки|Возможны следующие значения: 0x0001&mdash;вспомогательный токен используется для открытия локального файла задания отправки, создания или переименования временного файла задания загрузки, а также для создания или переименования файла ответов для задания отправки и ответа. 0x0002&mdash;вспомогательный токен используется для открытия удаленного файла задания передачи или загрузки SMB или в ответ на HTTP-сервер или запрос прокси-сервера для неявных учетных данных NTLM или Kerberos. Чтобы разрешить отправку учетных данных по протоколу HTTP, необходимо вызвать   `/SetCredentialsJob TargetScheme NULL NULL`.|

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
