---
title: 'ksetup: сетреалм'
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ab268c40-276b-46ef-ab16-d5ce7667fbed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 453977ac39dd3a52b4f5a3104995f944e4a48392
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724550"
---
# <a name="ksetupsetrealm"></a>ksetup: сетреалм



Задает имя области Kerberos.

## <a name="syntax"></a>Синтаксис

```
ksetup /setrealm <DNSDomainName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Днсдомаиннаме>|Доменное имя DNS может иметь форму полного доменного имени или простого доменного имени.|

## <a name="remarks"></a>Примечания

Параметр доменного имени DNS следует вводить прописными буквами. В противном случае команда **ksetup** запросит подтверждение для продолжения.

Установка области Kerberos на контроллере домена не поддерживается. Попытка сделать это вызовет предупреждение и сбой команды.

## <a name="examples"></a>Примеры

Задайте для области этого компьютера определенное доменное имя, чтобы ограничить доступ неконтроллером домена только с областью Kerberos CONTOSO:
```
ksetup /setrealm CONTOSO
```

## <a name="additional-references"></a>Дополнительные ссылки

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Ksetup](ksetup.md)
-   [Ksetup:removerealm](ksetup-removerealm.md)