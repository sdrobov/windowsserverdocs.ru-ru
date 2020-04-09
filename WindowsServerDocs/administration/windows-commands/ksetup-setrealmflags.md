---
title: 'ksetup: сетреалмфлагс'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bcb2824e-fba7-4ebe-be62-e62b4fae5b17
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 29ef5de8130fa9b10ce6d999e16765b0aa2697a4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841287"
---
# <a name="ksetupsetrealmflags"></a>ksetup: сетреалмфлагс



Задает флаги области для указанной области. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /setrealmflags <RealmName> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Реалмнаме >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM.|
|Флаг области|Обозначает один из следующих флагов:</br>-Сендаддресс</br>-Ткпсуппортед</br>-Delegate</br>-Нксуппортед</br>-RC4|

## <a name="remarks"></a>Примечания

Флаги сферы определяют дополнительные возможности области Kerberos, которые не основаны на операционной системе Windows Server. Компьютеры под управлением Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2 могут использовать сервер Kerberos для администрирования проверки подлинности вместо использования домена под управлением операционной системы Windows Server, и эти системы участвуют в области Kerberos. Эта запись устанавливает функции области. В следующей таблице описан каждый из них.

|Значение|Флаг области|Описание|
|-----|----------|-----------|
|0xF|Все|Заданы все флаги сферы.|
|0x00|Нет|Флаги области не заданы, а дополнительные функции не включены.|
|0x01|сендаддресс|IP-адрес будет включаться в билеты предоставления билетов.|
|0x02|ткпсуппортед|В этой области поддерживаются протоколы TCP и UDP (User Datagram Protocol).|
|0x04|Делегат|Все пользователи в этой области являются доверенными для делегирования.|
|0x08|нксуппортед|Эта область поддерживает канонизации имен, что позволяет использовать стандарты именования DNS и областей.|
|0x80|RC4|Эта область поддерживает шифрование RC4 для включения доверительных отношений между сферами, что позволяет использовать TLS.|

Флаги сферы хранятся в реестре в разделе **HKEY_LOCAL_MACHINE \систем\куррентконтролсет\контрол\лса\керберос\домаинс\\** <em>реалмнаме</em>. Эта запись не существует в реестре по умолчанию. Для заполнения реестра можно использовать команду [Ksetup: аддреалмфлагс](ksetup-addrealmflags.md) .

Чтобы увидеть, какие флаги области доступны и задаются, просмотрите выходные данные **ksetup**.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Перечислите доступные и установленные флаги области для области CONTOSO:
```
ksetup
```
Установить два флага, которые сейчас не заданы:
```
ksetup /setrealmflags CONTOSO ncsupported delegate
```
Выполните команду **ksetup** , чтобы убедиться, что установлен флаг realm, просмотрев выходные данные и поиск **флагов области =** .

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup:listrealmflags](ksetup-listrealmflags.md)
-   [Ksetup:addrealmflags](ksetup-addrealmflags.md)
-   [Ksetup:delrealmflags](ksetup-delrealmflags.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)