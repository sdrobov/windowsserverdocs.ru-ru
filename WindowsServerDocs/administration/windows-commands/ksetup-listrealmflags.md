---
title: 'ksetup: листреалмфлагс'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa96e4da-6b98-4c05-bccf-73cbf33258c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8f103875dc10dfbf7b0c604a8e2060fe58ee7a92
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374967"
---
# <a name="ksetuplistrealmflags"></a>ksetup: листреалмфлагс



Список доступных флагов области, которые могут быть переданы по **ksetup**. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /listrealmflags
```

### <a name="parameters"></a>Параметры

Нет

## <a name="remarks"></a>Замечания

Флаги сферы определяют дополнительные возможности области Kerberos, отличной от Windows. Компьютеры под управлением Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2 могут использовать сервер Kerberos, не основанный на Windows, для администрирования проверки подлинности вместо использования домена под управлением операционной системы Windows Server. Эти системы принимают участие в сфере Kerberos вместо домена Windows. Эта запись устанавливает функции области. В следующей таблице описан каждый из них.

|Значение|Флаг области|Описание|
|-----|----------|-----------|
|0xF|Все|Заданы все флаги сферы.|
|0x00|Нет|Флаги области не заданы, а дополнительные функции не включены.|
|0x01|сендаддресс|IP-адрес будет включаться в билеты предоставления билетов.|
|0x02|ткпсуппортед|В этой области поддерживаются протоколы TCP и UDP (User Datagram Protocol).|
|0x04|Делегирование|Все пользователи в этой области являются доверенными для делегирования.|
|0x08|нксуппортед|Эта область поддерживает канонизации имен, что позволяет использовать стандарты именования DNS и областей.|
|0x80|RC4|Эта область поддерживает шифрование RC4 для включения доверительных отношений между сферами, что позволяет использовать TLS.|

Флаги сферы хранятся в реестре в **HKEY_LOCAL_MACHINE \систем\куррентконтролсет\контрол\лса\керберос\домаинс\\** <em>realm-Name</em>. Эта запись не существует в реестре по умолчанию. Для заполнения реестра можно использовать команду [Ksetup: аддреалмфлагс](ksetup-addrealmflags.md) .

## <a name="BKMK_Examples"></a>Примеров

Список известных флагов области на этом компьютере:
```
ksetup /listrealmflags
```
Установите флаги доступной области, которые **Ksetup** не знает, введя одну из следующих команд в командной строке:
```
ksetup /setrealmflags CORP.CONTOSO.COM sendaddress tcpsupported delete ncsupported
```
```
ksetup /setrealmflags CORP.CONTOSO.COM 0xF
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup:setrealmflags](ksetup-setrealmflags.md)
-   [Ksetup:addrealmflags](ksetup-addrealmflags.md)
-   [Ksetup:delrealmflags](ksetup-delrealmflags.md)
-   [Ksetup](ksetup.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)