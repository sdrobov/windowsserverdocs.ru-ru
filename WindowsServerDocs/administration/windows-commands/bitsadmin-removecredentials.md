---
title: bitsadmin removecredentials
description: Раздел Windows команды для **bitsadmin removecredentials** -удаляет учетные данные из задания.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4a78ce9a-1feb-4811-a000-cce81287b22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cbd65442ff0d74ec1179a49df5d4a94785f3dd25
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59822295"
---
# <a name="bitsadmin-removecredentials"></a>bitsadmin removecredentials

Удаляет учетные данные из задания.

**БИТЫ 1.2 и более ранних версий**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /RemoveCredentials <Job> <Target> <Scheme>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Целевой объект|СЕРВЕР или прокси-сервера|
|Схема|Возможно одно из следующих:.</br>— БАЗОВЫЙ, схема проверки подлинности, в которой имя пользователя и пароль отправляются в виде открытого текста с сервером или прокси.</br>-ДАЙДЖЕСТ — схему проверки подлинности запроса и ответа, использующая данных указанную сервером строку запроса.</br>-NTLM — схема проверки подлинности запроса и ответа, который использует учетные данные пользователя для проверки подлинности в сетевой среде Windows.</br>— NEGOTIATE, также известное как простые и защищенные согласования протокола (Snego) — схему проверки подлинности запроса и ответа, которая согласовывает с сервером или прокси-сервера, чтобы определить схему, которую нужно использовать для проверки подлинности. Примерами являются протокол Kerberos и NTLM.</br>-PASSPORT — централизованная служба проверки подлинности, предоставляемые Майкрософт и поддерживающая единый вход на сайты-участники.|

## <a name="BKMK_examples"></a>Примеры

В следующем примере удаляются учетные данные из задания с именем *myDownloadJob*.
```
C:\>bitsadmin /RemoveCredentials myDownloadJob SERVER BASIC
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)