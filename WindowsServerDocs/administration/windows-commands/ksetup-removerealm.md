---
title: 'ksetup: ремовереалм'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 11858d8a24d4f125c83b3e4092ac48f336a9ef0b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374954"
---
# <a name="ksetupremoverealm"></a>ksetup: ремовереалм



Удаляет из реестра все сведения для указанной области. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /removerealm <RealmName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Реалмнаме >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM, и он указывается в качестве области по умолчанию при запуске **ksetup** .|

## <a name="remarks"></a>Замечания

Имя области хранится в двух местах реестра: **HKEY_LOCAL_MACHINE \system\controlset001** и **\куррентконтролсет\контрол\лса\керберос**.

Невозможно удалить имя сферы по умолчанию из контроллера домена, так как это приведет к сбросу данных DNS, и удаление может привести к невозможности использования контроллера домена.

## <a name="BKMK_Examples"></a>Примеров

По ошибке задается имя области с ошибкой ". COM" на локальном компьютере в CORP. Компанией. ПАРАЛЛЕЛЬ
```
ksetup /setrealm CORP.CONTOSO.CON
```
Удалите это ошибочное имя области с локального компьютера:
```
ksetup /removerealm CORP.CONTOSO.CON
```
Проверьте удаление, выполнив **ksetup** , и проверьте выходные данные.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Ksetup:setrealm](ksetup-setrealm.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)