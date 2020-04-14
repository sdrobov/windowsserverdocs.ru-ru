---
title: 'ksetup: домен'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ef766e3-6071-44f2-946b-22ea5b61a508
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bfaa8a37ae4ee5c9669b09f27a73b3d016324dea
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841587"
---
# <a name="ksetupdomain"></a>ksetup: домен



Задает доменное имя для всех операций Kerberos. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /domain <DomainName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<имя_домена >|Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например contoso.com или contoso.|

## <a name="remarks"></a>Примечания

Нет

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Установите подключение к допустимому домену, например Microsoft, с помощью подкоманды/мапусер:
```
ksetup /mapuser principal@realm domain-user /domain domain-name
```
После успешного подключения вы получите новый TGT или обновите существующий TGT.

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)