---
title: bitsadmin setcredentials
description: Раздел команд Windows для битсадмин сеткредентиалс, который добавляет учетные данные к заданию.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3cd099a4-9e85-46d8-8527-edb6dfab7f97
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 918bda93407e029cedaaf5eab937d1bb23dc3c4c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849647"
---
# <a name="bitsadmin-setcredentials"></a>bitsadmin setcredentials

Добавляет учетные данные в задание.

**BITS 1,2 и более ранних версий**: не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetCredentials <Job> <Target> <Scheme> <Username> <Password>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Target|СЕРВЕР или прокси|
|Схема|Возможно одно из следующих:.</br>— BASIC — схема проверки подлинности, в которой имя пользователя и пароль отправляются открытым текстом на сервер или прокси.</br>-DIGEST — схема проверки подлинности "запрос — ответ", которая использует указанную сервером строку данных для запроса.</br>-NTLM — схема проверки подлинности типа "запрос-ответ", которая использует учетные данные пользователя для проверки подлинности в сетевой среде Windows.</br>-NEGOTIATE — также известный как простой и защищенный протокол согласования (снего) — это схема проверки подлинности типа "запрос-ответ", которая согласовывается с сервером или прокси, чтобы определить, какую схему использовать для проверки подлинности. Примерами являются протокол Kerberos и NTLM.</br>-PASSPORT — централизованная служба проверки подлинности, предоставляемая корпорацией Майкрософт, предоставляющая единый вход для сайтов-членов.|
|Имя пользователя|Имя предоставленных учетных данных|
|Пароль|Пароль, связанный с указанным *именем пользователя*|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере учетные данные добавляются к заданию с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /RemoveCredentials myDownloadJob SERVER BASIC Edward Password20
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)