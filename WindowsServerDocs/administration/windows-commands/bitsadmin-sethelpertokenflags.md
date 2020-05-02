---
title: bitsadmin sethelpertokenflags
description: Справочный раздел по команде битсадмин сеселпертокенфлагс, который задает флаги использования для вспомогательного токена, связанного с заданием передачи BITS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 2bb93664d88c0f346e2926102f97287ac8fc35de
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719362"
---
# <a name="bitsadmin-sethelpertokenflags"></a>bitsadmin sethelpertokenflags

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
| задание | Отображаемое имя задания или идентификатор GUID. |
| flags | Возможные значения вспомогательных маркеров, включая:<ul><li>**0x0001.** Используется для открытия локального файла задания отправки, для создания или переименования временного файла задания загрузки, а также для создания или переименования файла ответов для задания отправки и ответа.</li><li>**0x0002.** Используется для открытия удаленного файла задания передачи или загрузки SMB, а также в ответ на HTTP-сервер или запрос прокси-сервера для неявных учетных данных NTLM или Kerberos.</li></ul>Необходимо вызвать `/setcredentialsjob targetscheme null null` , чтобы отправить учетные данные по протоколу HTTP. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
