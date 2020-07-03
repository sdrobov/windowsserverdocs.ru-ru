---
title: ksetup setrealm
description: Справочная статья по команде ksetup сетреалм, которая задает имя области Kerberos.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ab268c40-276b-46ef-ab16-d5ce7667fbed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c6fa5573322237dfee5909d9afc2e99696ac82b3
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933134"
---
# <a name="ksetup-setrealm"></a>ksetup setrealm

Задает имя области Kerberos.

> [!IMPORTANT]
> Установка области Kerberos на контроллере домена не поддерживается. Попытка сделать это вызовет предупреждение и сбой команды.

## <a name="syntax"></a>Синтаксис

```
ksetup /setrealm <DNSdomainname>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<DNSdomainname>` | Указывает DNS-имя в верхнем регистре, например CORP. CONTOSO.COM. Можно использовать полное доменное имя или простую форму имени. Если вы не используете прописные буквы в качестве DNS-имени, вам будет предложено выполнить проверку, чтобы продолжить. |

### <a name="examples"></a>Примеры

Чтобы задать для области этого компьютера определенное доменное имя и ограничить доступ неконтроллером домена только к сфере CONTOSO Kerberos, введите:

```
ksetup /setrealm CONTOSO
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)

- [ksetup removerealm](ksetup-removerealm.md)
