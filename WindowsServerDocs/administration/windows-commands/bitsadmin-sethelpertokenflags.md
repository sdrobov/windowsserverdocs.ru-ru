---
title: bitsadmin sethelpertokenflags
description: Раздел Windows команды для **bitsadmin sethelpertokenflags** -задает флаги использования вспомогательный маркер, связанный с задание передачи службы BITS.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: cc9652afe73476041aa42e64671885bfc1af9628
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813865"
---
# <a name="bitsadmin-sethelpertokenflags"></a>bitsadmin sethelpertokenflags

Задает флаги использования для [вспомогательный маркер](/windows/desktop/bits/helper-tokens-for-bits-transfer-jobs) связанный с задание передачи службы BITS.

**БИТЫ 3.0 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetHelperTokenFlags <Job> <Flags>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания.|
|Флажки|Возможные значения включают следующее. 0x0001&mdash;вспомогательный маркер используется откройте локальный файл Задание передачи, чтобы создать или переименовать временный файл задания загрузки, для создания или переименования файла ответа задания отправки ответа. 0x0002&mdash;вспомогательный маркер используется для открытия удаленного файла загрузки Server Message Block (SMB) или задание загрузки или в ответ на запрос HTTP сервер или прокси-сервера для неявного NTLM или Kerberos учетные данные. Необходимо вызвать `/SetCredentialsJob TargetScheme NULL NULL` чтобы разрешить учетные данные, отправляемые по протоколу HTTP.|

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
