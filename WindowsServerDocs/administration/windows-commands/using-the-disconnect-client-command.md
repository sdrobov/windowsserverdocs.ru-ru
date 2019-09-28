---
title: Использование команды Disconnect-Client
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: dbb96d64b47ec72ff0710bfb3684257c1bda2d04
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363472"
---
# <a name="using-the-disconnect-client-command"></a>Использование команды Disconnect-Client



Отключает клиент от многоадресной передачи или пространства имен. Если не указано значение **/Force**, клиент будет возвращаться к другому методу передачи (если он поддерживается клиентом).

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Disconnect-Client /ClientId:<Client ID> [/Server:<Server name>] [/Force]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/Клиентид: @no__t — идентификатор 0Client >|Указывает идентификатор клиента, который должен быть отключен. Чтобы просмотреть идентификатор клиента, введите **WDSUTIL/жет-мултикасттрансмиссион/Show: Clients**.|
|[/Server: \<Server имя >]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.|
|/Force|Полностью останавливает установку и не использует резервный метод. Обратите внимание, что Wdsmcast. exe не поддерживает никаких резервных механизмов. Если не использовать этот параметр, поведение по умолчанию будет следующим:</br>— Если используется клиент служб развертывания Windows, клиент продолжит установку с помощью одноадресной рассылки.</br>— Если клиент служб развертывания Windows не используется, установка завершается сбоем.</br>Внимание! Этот параметр следует использовать с осторожностью, так как установка завершится сбоем и компьютер может остаться в неработоспособном состоянии.|

## <a name="BKMK_examples"></a>Примеров

Чтобы отключить клиент, введите:
```
WDSUTIL /Disconnect-Client /ClientId:1
```
Чтобы отключить клиент и принудительно завершить установку, введите:
```
WDSUTIL /Disconnect-Client /Server:MyWDSServer /ClientId:1 /Force
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)