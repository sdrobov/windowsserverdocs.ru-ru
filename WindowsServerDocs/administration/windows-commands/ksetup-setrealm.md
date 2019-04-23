---
title: ksetup:setrealm
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab268c40-276b-46ef-ab16-d5ce7667fbed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aa6b2a21904ec4dae1e60def5bd36647291b1af6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59877405"
---
# <a name="ksetupsetrealm"></a>ksetup:setrealm



Задает имя области Kerberos. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /setrealm <DNSDomainName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<DNSDomainName >|DNS-имя домена может быть в форме Простое доменное имя или полное доменное имя.|

## <a name="remarks"></a>Примечания

Параметр имени домена DNS должны вводиться прописными буквами. В противном случае **ksetup** команда запросит проверку, чтобы продолжить.

Задание области Kerberos на контроллере домена не поддерживается. Попытка выполнить такую операцию вызовет предупреждение и ошибка команды.

## <a name="BKMK_Examples"></a>Примеры

Задайте область для этого компьютера для доменного имени, чтобы ограничить доступ, не являющемся контроллером домена только для области CONTOSO Kerberos:
```
ksetup /setrealm CONTOSO
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Ksetup](ksetup.md)
-   [ksetup:removerealm](ksetup-removerealm.md)