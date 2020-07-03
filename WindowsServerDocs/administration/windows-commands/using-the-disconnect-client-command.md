---
title: Disconnect — клиент
description: Справочная статья по Disconnect-Client, которая отключает клиент от многоадресной передачи или пространства имен.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 876bbe6c-76ab-4de5-879b-d2066e700326
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 387f9b1e476371a6aee1487f418241afa1464d02
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936851"
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
|ClientID\<Client ID>|Указывает идентификатор клиента, который должен быть отключен. Чтобы просмотреть идентификатор клиента, введите **WDSUTIL/жет-мултикасттрансмиссион/Show: Clients**.|
|[/Server: \<Server name> ]|Указывает имя сервера. Это может быть NetBIOS-имя или полное доменное имя (FQDN). Если имя сервера не указано, используется локальный сервер.|
|/Force|Полностью останавливает установку и не использует резервный метод. Обратите внимание, что Wdsmcast.exe не поддерживает никаких резервных механизмов. Если не использовать этот параметр, поведение по умолчанию будет следующим:</br>— Если используется клиент служб развертывания Windows, клиент продолжит установку с помощью одноадресной рассылки.</br>— Если клиент служб развертывания Windows не используется, установка завершается сбоем.</br>Важно. Этот параметр следует использовать с осторожностью, так как установка завершится сбоем и компьютер может остаться в неработоспособном состоянии.|

## <a name="examples"></a>Примеры

Чтобы отключить клиент, введите:
```
WDSUTIL /Disconnect-Client /ClientId:1
```
Чтобы отключить клиент и принудительно завершить установку, введите:
```
WDSUTIL /Disconnect-Client /Server:MyWDSServer /ClientId:1 /Force
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)