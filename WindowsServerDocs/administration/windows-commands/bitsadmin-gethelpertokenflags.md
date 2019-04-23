---
title: bitsadmin gethelpertokenflags
description: Раздел Windows команды для **bitsadmin gethelpertokenflags** -Возвращает флаги использования вспомогательный маркер, связанный с задание передачи службы BITS.
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
ms.openlocfilehash: e5665ed4670891dcbecd56215342f3d94e1ed753
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59885795"
---
# <a name="bitsadmin-gethelpertokenflags"></a>bitsadmin gethelpertokenflags

Возвращает флаги использования для [вспомогательный маркер](/windows/desktop/bits/helper-tokens-for-bits-transfer-jobs) связанный с задание передачи службы BITS.

**БИТЫ 3.0 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetHelperTokenFlags <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="remarks"></a>Примечания

Ниже перечислены возможные возвращаемые значения.

- 0x0001. Вспомогательный маркер используется для открытия локального файла отправки задания, чтобы создать или переименовать временный файл задания загрузки, или для создания или переименования файла ответа задания отправки ответа.
- 0x0002. Вспомогательный маркер используется для открытия удаленного файла загрузки Server Message Block (SMB) или задание загрузки или в ответ на запрос HTTP сервер или прокси-сервера для неявного NTLM или Kerberos учетные данные. Необходимо вызвать SetCredentialsJob TargetScheme NULL значение NULL, чтобы разрешить учетные данные, отправляемые по протоколу HTTP.

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)
