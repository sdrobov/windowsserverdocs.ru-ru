---
title: 'ksetup: ремовереалм'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39f0c6f0-4c50-4781-941e-0893495405e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1465ce08c0cf45de828683324b29fb2df8d0e893
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841457"
---
# <a name="ksetupremoverealm"></a>ksetup: ремовереалм



Удаляет из реестра все сведения для указанной области. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /removerealm <RealmName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Реалмнаме >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM, и он указывается в качестве области по умолчанию при запуске **ksetup** .|

## <a name="remarks"></a>Примечания

Имя области хранится в двух местах реестра: **HKEY_LOCAL_MACHINE \system\controlset001** и **\куррентконтролсет\контрол\лса\керберос**.

Невозможно удалить имя сферы по умолчанию из контроллера домена, так как это приведет к сбросу данных DNS, и удаление может привести к невозможности использования контроллера домена.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

По ошибке задается имя области с ошибкой. COM на локальном компьютере в CORP. Компанией. ПАРАЛЛЕЛЬ
```
ksetup /setrealm CORP.CONTOSO.CON
```
Удалите это ошибочное имя области с локального компьютера:
```
ksetup /removerealm CORP.CONTOSO.CON
```
Проверьте удаление, выполнив **ksetup** , и проверьте выходные данные.

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup](ksetup.md)
-   [Ksetup:setrealm](ksetup-setrealm.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)