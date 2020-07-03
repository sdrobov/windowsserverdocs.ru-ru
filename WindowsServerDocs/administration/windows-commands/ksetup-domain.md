---
title: ksetup domain
description: Справочная статья по команде домена ksetup, которая задает доменное имя для всех операций Kerberos.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ef766e3-6071-44f2-946b-22ea5b61a508
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 70454205f73375b11dc63e3496a2d7fc1bb3e50e
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926102"
---
# <a name="ksetup-domain"></a>ksetup domain

Задает доменное имя для всех операций Kerberos.

## <a name="syntax"></a>Синтаксис

```
ksetup /domain <domainname>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<domainname>` | Имя домена, для которого требуется установить соединение. Используйте полное доменное имя или простую форму имени, например contoso.com или contoso.|

### <a name="examples"></a>Примеры

Чтобы установить подключение к допустимому домену, такому как Microsoft, с помощью `ksetup /mapuser` подкоманды, введите:

```
ksetup /mapuser principal@realm domain-user /domain domain-name
```

После успешного подключения вы получите новый TGT или обновите существующий TGT.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)

- [ksetup мапусер, команда](ksetup-mapuser.md)