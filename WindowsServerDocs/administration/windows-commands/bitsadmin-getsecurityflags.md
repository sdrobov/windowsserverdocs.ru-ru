---
title: bitsadmin getsecurityflags
description: Раздел Windows команды для **bitsadmin getsecurityflags** — сообщает флаги безопасности HTTP для перенаправления URL-адреса и проверяет выполнение сертификат сервера во время передачи.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c2e73519-34f4-487b-af11-97d5d08ef9bb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 97d889b54c4b0de0230c50e1d7c8d21617ea881a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59835855"
---
#<a name="bitsadmin-getsecurityflags"></a>bitsadmin getsecurityflags

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Флаги безопасности отчеты HTTP для перенаправления URL-адрес и проверки над сертификат сервера во время передачи.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetSecurityFlags <Job> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя или идентификатор GUID задания|

## <a name="BKMK_examples"></a>Примеры
В следующем примере извлекается securitly флаги из задания с именем *myJob*.

```
C:\>bitsadmin /GetSecurityFlags myJob 
```

## <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)


