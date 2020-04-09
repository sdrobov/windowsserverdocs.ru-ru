---
title: 'ksetup: листреалмфлагс'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aa96e4da-6b98-4c05-bccf-73cbf33258c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 265f988d85deb7602e91677626d207bc3a7873ef
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841497"
---
# <a name="ksetuplistrealmflags"></a>ksetup: листреалмфлагс



Список доступных флагов области, которые могут быть переданы по **ksetup**. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /listrealmflags
```

#### <a name="parameters"></a>Параметры

Нет

## <a name="remarks"></a>Примечания

Флаги сферы определяют дополнительные возможности области Kerberos, отличной от Windows. Компьютеры под управлением Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2 могут использовать сервер Kerberos, не основанный на Windows, для администрирования проверки подлинности вместо использования домена под управлением операционной системы Windows Server. Эти системы принимают участие в сфере Kerberos вместо домена Windows. Эта запись устанавливает функции области. В следующей таблице описан каждый из них.

|Значение|Флаг области|Описание|
|-----|----------|-----------|
|0xF|Все|Заданы все флаги сферы.|
|0x00|Нет|Флаги области не заданы, а дополнительные функции не включены.|
|0x01|сендаддресс|IP-адрес будет включаться в билеты предоставления билетов.|
|0x02|ткпсуппортед|В этой области поддерживаются протоколы TCP и UDP (User Datagram Protocol).|
|0x04|Делегат|Все пользователи в этой области являются доверенными для делегирования.|
|0x08|нксуппортед|Эта область поддерживает канонизации имен, что позволяет использовать стандарты именования DNS и областей.|
|0x80|RC4|Эта область поддерживает шифрование RC4 для включения доверительных отношений между сферами, что позволяет использовать TLS.|

Флаги сферы хранятся в реестре в **HKEY_LOCAL_MACHINE \систем\куррентконтролсет\контрол\лса\керберос\домаинс\\** <em>realm-Name</em>. Эта запись не существует в реестре по умолчанию. Для заполнения реестра можно использовать команду [Ksetup: аддреалмфлагс](ksetup-addrealmflags.md) .

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

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

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup:setrealmflags](ksetup-setrealmflags.md)
-   [Ksetup:addrealmflags](ksetup-addrealmflags.md)
-   [Ksetup:delrealmflags](ksetup-delrealmflags.md)
-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)