---
title: битсадмин сеселпертокенфлагс
description: Раздел команд Windows для **битсадмин сеселпертокенфлагс**, который задает флаги использования для вспомогательного токена, связанного с заданием передачи BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 77fac03dba2bb0686a98206405622e2eb398953e
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122976"
---
# <a name="bitsadmin-sethelpertokenflags"></a>битсадмин сеселпертокенфлагс

Задает флаги использования для [вспомогательного токена](https://docs.microsoft.com/windows/win32/bits/helper-tokens-for-bits-transfer-jobs) , связанного с заданием передачи BITS.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 3,0 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /sethelpertokenflags <job> <flags>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| flags | Возможные значения вспомогательных маркеров, включая:<ul><li>**0x0001.** Используется для открытия локального файла задания отправки, для создания или переименования временного файла задания загрузки, а также для создания или переименования файла ответов для задания отправки и ответа.</li><li>**0x0002.** Используется для открытия удаленного файла задания передачи или загрузки SMB, а также в ответ на HTTP-сервер или запрос прокси-сервера для неявных учетных данных NTLM или Kerberos.</li></ul>Для отправки учетных данных по протоколу HTTP необходимо вызвать   `/setcredentialsjob targetscheme null null`. |

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
