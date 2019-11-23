---
title: битсадмин жеселпертокенфлагс
description: Раздел команд Windows для **битсадмин жеселпертокенфлагс** . Возвращает флаги использования для вспомогательного токена, связанного с заданием передачи BITS.
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
ms.openlocfilehash: 25d667736d5fdcd018f557b2a5565b94898f6e51
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381566"
---
# <a name="bitsadmin-gethelpertokenflags"></a>битсадмин жеселпертокенфлагс

Возвращает флаги использования [вспомогательного маркера](/windows/desktop/bits/helper-tokens-for-bits-transfer-jobs) , связанного с заданием передачи BITS.

**BITS 3,0 и более ранних версий**: не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetHelperTokenFlags <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="remarks"></a>Замечания

Возможные возвращаемые значения включают следующее.

- 0x0001. Вспомогательный токен используется для открытия локального файла задания отправки, создания или переименования временного файла задания загрузки, а также для создания или переименования файла ответов для задания отправки и ответа.
- 0x0002. Вспомогательный токен используется для открытия удаленного файла задания передачи или загрузки SMB, а также в ответ на HTTP-сервер или запрос прокси-сервера для неявных учетных данных NTLM или Kerberos. Чтобы разрешить отправку учетных данных по протоколу HTTP, необходимо вызвать/Сеткредентиалсжоб Таржетсчеме NULL NULL.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
