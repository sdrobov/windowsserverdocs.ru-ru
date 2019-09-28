---
title: Использование команды «Disable-Server»
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b69fcfe0-b744-4794-bc75-2c9218c0ba66
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9376bf1c5a5641aa6763c88b58bfe92d799b44f5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363509"
---
# <a name="using-the-disable-server-command"></a>Использование команды «Disable-Server»



Отключает все службы для сервера служб развертывания Windows.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL [Options] /Disable-Server [/Server:<Server name>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[/Server: \<Server имя >]|Указывает имя сервера. Это может быть либо NetBIOS-имя, либо полное доменное имя (FQDN). Если имя сервера не указано, будет использоваться локальный сервер.|

## <a name="BKMK_examples"></a>Примеров

Чтобы отключить сервер, выполните одно из следующих действий.
```
WDSUTIL /Disable-Server
WDSUTIL /Verbose /Disable-Server /Server:MyWDSServer
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

