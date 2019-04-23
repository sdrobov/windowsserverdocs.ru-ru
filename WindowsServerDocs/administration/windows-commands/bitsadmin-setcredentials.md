---
title: bitsadmin setcredentials
description: Раздел Windows команды для **bitsadmin setcredentials** -добавляет учетные данные к заданию.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3cd099a4-9e85-46d8-8527-edb6dfab7f97
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 923dcff7d268d40b72db3254e2a97c808c7c7253
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59877395"
---
# <a name="bitsadmin-setcredentials"></a>bitsadmin setcredentials

Добавляет учетные данные для задания.

**БИТЫ 1.2 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetCredentials <Job> <Target> <Scheme> <Username> <Password>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Целевой объект|СЕРВЕР или прокси-сервера|
|Схема|Возможно одно из следующих:.</br>— БАЗОВЫЙ, схема проверки подлинности, в которой имя пользователя и пароль отправляются в виде открытого текста с сервером или прокси.</br>-ДАЙДЖЕСТ — схему проверки подлинности запроса и ответа, использующая данных указанную сервером строку запроса.</br>-NTLM — схема проверки подлинности запроса и ответа, который использует учетные данные пользователя для проверки подлинности в сетевой среде Windows.</br>— NEGOTIATE, также известное как простые и защищенные согласования протокола (Snego) — схему проверки подлинности запроса и ответа, которая согласовывает с сервером или прокси-сервера, чтобы определить схему, которую нужно использовать для проверки подлинности. Примерами являются протокол Kerberos и NTLM.</br>-PASSPORT — централизованная служба проверки подлинности, предоставляемые Майкрософт и поддерживающая единый вход на сайты-участники.|
|Имя пользователя|Имя предоставленных учетных данных|
|Пароль|Пароль, связанный с предоставленным *имя пользователя*|

## <a name="BKMK_examples"></a>Примеры

Следующий пример добавляет учетные данные, задания с именем *myDownloadJob*.
```
C:\>bitsadmin /RemoveCredentials myDownloadJob SERVER BASIC Edward Password20
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)