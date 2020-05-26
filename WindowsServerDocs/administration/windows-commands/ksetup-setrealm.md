---
title: ksetup сетреалм
description: Справочный раздел по команде ksetup сетреалм, который задает имя области Kerberos.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ab268c40-276b-46ef-ab16-d5ce7667fbed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 03b33977f57e187a8bea69be78c1e9c094b9a73e
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817284"
---
# <a name="ksetup-setrealm"></a>ksetup сетреалм

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

- [ksetup ремовереалм](ksetup-removerealm.md)
