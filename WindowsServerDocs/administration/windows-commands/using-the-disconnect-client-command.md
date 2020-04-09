---
title: Disconnect — клиент
description: Раздел команд Windows для Disconnect-Client, который отключает клиент от многоадресной передачи или пространства имен.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 876bbe6c-76ab-4de5-879b-d2066e700326
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2ba40a7e885cfa3e42065b939d3ddb21ead2f866
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831607"
---
# <a name="disconnect-client"></a>Disconnect — клиент

Отключает клиент от многоадресной передачи или пространства имен. Если не указано значение **/Force**, клиент будет возвращаться к другому методу передачи (если он поддерживается клиентом).

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Disconnect-Client /ClientId:<Client ID> [/Server:<Server name>] [/Force]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/Клиентид: идентификатор клиента\<>|Указывает идентификатор клиента, который должен быть отключен. Чтобы просмотреть идентификатор клиента, введите **WDSUTIL/жет-мултикасттрансмиссион/Show: Clients**.|
|[/Server:\<имя сервера >]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.|
|/Force|Полностью останавливает установку и не использует резервный метод. Обратите внимание, что Wdsmcast. exe не поддерживает никаких резервных механизмов. Если не использовать этот параметр, поведение по умолчанию будет следующим:</br>— Если используется клиент служб развертывания Windows, клиент продолжит установку с помощью одноадресной рассылки.</br>— Если клиент служб развертывания Windows не используется, установка завершается сбоем.</br>Важно. Этот параметр следует использовать с осторожностью, так как установка завершится сбоем и компьютер может остаться в неработоспособном состоянии.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы отключить клиент, введите:
```
WDSUTIL /Disconnect-Client /ClientId:1
```
Чтобы отключить клиент и принудительно завершить установку, введите:
```
WDSUTIL /Disconnect-Client /Server:MyWDSServer /ClientId:1 /Force
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)