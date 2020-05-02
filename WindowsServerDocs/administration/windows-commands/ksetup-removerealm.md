---
title: 'ksetup: ремовереалм'
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39f0c6f0-4c50-4781-941e-0893495405e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bb7bf4663594a6c164d6495a9ba4cd81942afb79
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724608"
---
# <a name="ksetupremoverealm"></a>ksetup: ремовереалм



Удаляет из реестра все сведения для указанной области.

## <a name="syntax"></a>Синтаксис

```
ksetup /removerealm <RealmName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Реалмнаме>|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM, и он указывается в качестве области по умолчанию при запуске **ksetup** .|

## <a name="remarks"></a>Примечания

Имя области хранится в двух местах реестра: **HKEY_LOCAL_MACHINE \system\controlset001** и **\куррентконтролсет\контрол\лса\керберос**.

Невозможно удалить имя сферы по умолчанию из контроллера домена, так как это приведет к сбросу данных DNS, и удаление может привести к невозможности использования контроллера домена.

## <a name="examples"></a>Примеры

По ошибке задается имя области с ошибкой. COM на локальном компьютере в CORP. Компанией. ПАРАЛЛЕЛЬ
```
ksetup /setrealm CORP.CONTOSO.CON
```
Удалите это ошибочное имя области с локального компьютера:
```
ksetup /removerealm CORP.CONTOSO.CON
```
Проверьте удаление, выполнив **ksetup** , и проверьте выходные данные.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Ksetup](ksetup.md)
-   [Ksetup:setrealm](ksetup-setrealm.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)