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
ms.openlocfilehash: 6e1db167b12d47afccb8842da617f1e9fe72acff
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434961"
---
# <a name="bitsadmin-getsecurityflags"></a>bitsadmin getsecurityflags

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
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)


