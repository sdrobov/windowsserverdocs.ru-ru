---
title: 'ksetup: аддреалмфлагс'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 80ca1e16-8871-494b-b9be-6bc9d63de860
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 543fcb8105d21020cc9a4ab5e5e8c1eca14a358b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375171"
---
# <a name="ksetupaddrealmflags"></a>ksetup: аддреалмфлагс



Добавляет дополнительные флаги сферы в указанную область. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addrealmflags <RealmName> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Имя области|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM.|

## <a name="remarks"></a>Замечания

Флаги сферы определяют дополнительные возможности области Kerberos, которые не основаны на операционной системе Windows Server. Компьютеры под управлением Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2 могут использовать сервер Kerberos для администрирования проверки подлинности вместо использования домена под управлением операционной системы Windows Server, и эти системы участвуют в Область Kerberos. Эта запись устанавливает функции области. В следующей таблице описан каждый из них.

|Значение|Флаг области|Описание|
|-----|----------|-----------|
|0xF|Все|Заданы все флаги сферы.|
|0x00|Нет|Флаги области не заданы, а дополнительные функции не включены.|
|0x01|сендаддресс|IP-адрес будет включаться в билеты предоставления билетов.|
|0x02|ткпсуппортед|В этой области поддерживаются протоколы TCP и UDP (User Datagram Protocol).|
|0x04|Делегирование|Все пользователи в этой области являются доверенными для делегирования.|
|0x08|нксуппортед|Эта область поддерживает канонизации имен, что позволяет использовать стандарты именования DNS и областей.|
|0x80|RC4|Эта область поддерживает шифрование RC4 для включения доверительных отношений между сферами, что позволяет использовать TLS.|

Флаги сферы хранятся в реестре в разделе **HKEY_LOCAL_MACHINE \систем\куррентконтролсет\контрол\лса\керберос\домаинс\\** <em>realm-Name</em>. Эта запись не существует в реестре по умолчанию. Для заполнения реестра можно использовать команду [Ksetup: аддреалмфлагс](ksetup-addrealmflags.md) .

Чтобы увидеть, какие флаги области доступны и установлены, просмотрите выходные данные ksetup или ksetup/думпстате.

## <a name="BKMK_Examples"></a>Примеров

Список доступных флагов области для области CONTOSO:
```
Ksetup /listrealmflags
```
Установите два флага в область CONTOSO:
```
ksetup /setrealmflags CONTOSO ncsupported delegate
```
Добавьте еще один флаг, который сейчас не находится в наборе:
```
ksetup /addrealmflags CONTOSO SendAddress
```
Выполните команду **ksetup** , чтобы убедиться, что установлен флаг realm, просмотрев выходные данные и поиск **флагов области =** .

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup:listrealmflags](ksetup-listrealmflags.md)
-   [Ksetup:setrealmflags](ksetup-setrealmflags.md)
-   [Ksetup:delrealmflags](ksetup-delrealmflags.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)