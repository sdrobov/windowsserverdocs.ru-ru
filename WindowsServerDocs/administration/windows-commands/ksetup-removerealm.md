---
title: ksetup:removerealm
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 39f0c6f0-4c50-4781-941e-0893495405e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 579b0772e4642389b90aa370dad80a3eebea9d34
ms.sourcegitcommit: 08eba714d3ceb5f2dfb5486d6b990da1aa4dcbdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65564720"
---
# <a name="ksetupremoverealm"></a>ksetup:removerealm



Удаляет всю информацию для указанной области из реестра. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /removerealm <RealmName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<RealmName>|Имя области указывается как верхний регистр DNS-имя, например CORP. CONTOSO.COM и указана как область по умолчанию при **ksetup** выполняется.|

## <a name="remarks"></a>Примечания

Имя области хранится в двух местах в реестре: **HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001** и **\CurrentControlSet\Control\Lsa\Kerberos**.

Имя области по умолчанию нельзя удалить из контроллера домена, так как данная команда восстановит данные DNS, и его удаления может перестать работать контроллера домена.

## <a name="BKMK_Examples"></a>Примеры

Ошибочно присвоено имя области, сделав опечатку «.COM» на локальном компьютере CORP. CONTOSO. CON
```
ksetup /setrealm CORP.CONTOSO.CON
```
Удалите это имя ошибочные сферы с локального компьютера:
```
ksetup /removerealm CORP.CONTOSO.CON
```
Проверки удаления, запустив **ksetup** и просмотрите выходные данные.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Ksetup:setrealm](ksetup-setrealm.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)