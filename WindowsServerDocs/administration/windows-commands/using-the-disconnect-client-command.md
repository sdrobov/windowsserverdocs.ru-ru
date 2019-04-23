---
title: С помощью команды отключения клиента
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 876bbe6c-76ab-4de5-879b-d2066e700326
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b89f6c2ff6d41230afd0a2b251ad6982dfa235b1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59841755"
---
# <a name="using-the-disconnect-client-command"></a>С помощью команды отключения клиента



Отключает клиента от многоадресной передачи или пространства имен. Если не указать **/Force**, клиент вернется к другой метод передачи (если оно поддерживается клиентом).

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Disconnect-Client /ClientId:<Client ID> [/Server:<Server name>] [/Force]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/ ClientId:\<идентификатор клиента >|Указывает идентификатор клиента для отключения. Чтобы просмотреть идентификатор клиента, введите **WDSUTIL /get-multicasttransmission /show:clients**.|
|[/ Server:\<имя сервера >]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, используется локальный сервер.|
|[/ Force]|Полностью останавливает установку и не использует метод резервной стратегии. Обратите внимание на то, что Wdsmcast.exe не поддерживает любой резервный механизм. Если этот параметр не используется, поведение по умолчанию выглядит следующим образом:</br>— Если вы используете клиент служб развертывания Windows, клиент продолжает установку, используя одноадресную.</br>-Если вы не используете клиента служб развертывания Windows, установка завершается сбоем.</br>Внимание! Этот параметр следует использовать с осторожностью, поскольку установка завершится ошибкой, и компьютер может остаться в нерабочем состоянии.|

## <a name="BKMK_examples"></a>Примеры

Чтобы отключить клиента, введите:
```
WDSUTIL /Disconnect-Client /ClientId:1
```
Чтобы отключить клиент и выполнить принудительную установку переход на другой, введите следующую команду:
```
WDSUTIL /Disconnect-Client /Server:MyWDSServer /ClientId:1 /Force
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)