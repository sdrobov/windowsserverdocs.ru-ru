---
title: bitsadmin setcredentials
description: Раздел команд Windows для **битсадмин сеткредентиалс** . добавляет учетные данные в задание.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 70ac9a01a2e713b5a2fb881f327a52552a6bbec6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380724"
---
# <a name="bitsadmin-setcredentials"></a>bitsadmin setcredentials

Добавляет учетные данные в задание.

**BITS 1,2 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetCredentials <Job> <Target> <Scheme> <Username> <Password>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Целевой объект|СЕРВЕР или прокси|
|Схема|Возможно одно из следующих:.</br>— BASIC — схема проверки подлинности, в которой имя пользователя и пароль отправляются открытым текстом на сервер или прокси.</br>-DIGEST — схема проверки подлинности "запрос — ответ", которая использует указанную сервером строку данных для запроса.</br>-NTLM — схема проверки подлинности типа "запрос-ответ", которая использует учетные данные пользователя для проверки подлинности в сетевой среде Windows.</br>-NEGOTIATE — также известный как простой и защищенный протокол согласования (снего) — это схема проверки подлинности типа "запрос-ответ", которая согласовывается с сервером или прокси, чтобы определить, какую схему использовать для проверки подлинности. Примерами являются протокол Kerberos и NTLM.</br>-PASSPORT — централизованная служба проверки подлинности, предоставляемая корпорацией Майкрософт, предоставляющая единый вход для сайтов-членов.|
|Имя пользователя|Имя предоставленных учетных данных|
|Пароль|Пароль, связанный с указанным *именем пользователя*|

## <a name="BKMK_examples"></a>Примеров

В следующем примере учетные данные добавляются к заданию с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /RemoveCredentials myDownloadJob SERVER BASIC Edward Password20
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)