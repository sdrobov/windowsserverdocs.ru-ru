---
title: битсадмин сеселпертокенфлагс
description: Раздел команд Windows для битсадмин сеселпертокенфлагс, который задает флаги использования для вспомогательного токена, связанного с заданием передачи BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: c644e82026cfc1d62f3fb5d20e3925002b871036
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849497"
---
# <a name="bitsadmin-sethelpertokenflags"></a>битсадмин сеселпертокенфлагс

Задает флаги использования для [вспомогательного токена](/windows/desktop/bits/helper-tokens-for-bits-transfer-jobs) , связанного с заданием передачи BITS.

**BITS 3,0 и более ранних версий**: не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetHelperTokenFlags <Job> <Flags>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID.|
|Флажки|Возможны следующие значения: 0x0001&mdash;вспомогательный токен используется для открытия локального файла задания отправки, создания или переименования временного файла задания загрузки, а также для создания или переименования файла ответов для задания отправки и ответа. 0x0002&mdash;вспомогательный токен используется для открытия удаленного файла задания передачи или загрузки SMB или в ответ на HTTP-сервер или запрос прокси-сервера для неявных учетных данных NTLM или Kerberos. Чтобы разрешить отправку учетных данных по протоколу HTTP, необходимо вызвать   `/SetCredentialsJob TargetScheme NULL NULL`.|

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
