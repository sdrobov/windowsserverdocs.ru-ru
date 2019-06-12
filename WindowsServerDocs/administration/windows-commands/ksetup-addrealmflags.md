---
title: ksetup:addrealmflags
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: f097fc8268976cf038523de0d5fa33c1dd3c6901
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66438037"
---
# <a name="ksetupaddrealmflags"></a>ksetup:addrealmflags



Добавляет флаги дополнительные области для указанной области. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addrealmflags <RealmName> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Имя области|Имя области указывается как верхний регистр DNS-имя, например CORP. CONTOSO.COM.|

## <a name="remarks"></a>Примечания

Флаги сферы укажите дополнительные функции сферы Kerberos, не зависит от операционной системы Windows Server. Компьютеры под управлением Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2 можно использовать сервер Kerberos для администрирования проверку подлинности вместо использования домена под управлением операционной системы Windows Server, и эти системы участвовать в Область Kerberos. Эта запись устанавливает компоненты области. В следующей таблице описан каждый.

|Значение|Флаг сферы|Описание|
|-----|----------|-----------|
|0xF|Все|Установлены все флаги области.|
|0x00|Нет|Флаги сферы не установлены, и дополнительные компоненты не включены.|
|0x01|SendAddress|IP-адрес включается в билетов предоставления билетов.|
|0x02|TcpSupported|Протокол управления передачей (TCP) и протокола UDP (User Datagram) поддерживаются в этой сфере.|
|0x04|Делегирование|Всем пользователям в этой сфере доверена для делегирования.|
|0x08|NcSupported|Это область поддерживает канонизации имя, что DNS и сферы, стандарты именования.|
|0x80|RC4|Это область поддерживает шифрование RC4 для включения доверительные отношения между сферами, который позволяет использовать TLS.|

Флаги сферы хранятся в разделе реестра **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\\** <em>имени области</em>. Эта запись не существует в реестре по умолчанию. Можно использовать [Ksetup:addrealmflags](ksetup-addrealmflags.md) команду, чтобы добавить в реестр.

Можно узнать, какие флаги сферы доступны и установить, просмотрев выходные данные ksetup или ksetup /dumpstate.

## <a name="BKMK_Examples"></a>Примеры

Отображение списка доступных сферы флаги для сферы CONTOSO:
```
Ksetup /listrealmflags
```
Установите два флага сферы CONTOSO:
```
ksetup /setrealmflags CONTOSO ncsupported delegate
```
Добавьте один дополнительные флаг, который не находится в наборе:
```
ksetup /addrealmflags CONTOSO SendAddress
```
Запустите **ksetup** команду, чтобы проверить, что флаг сферы, просматривая выходные данные и ищет **флаги сферы =** .

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup:listrealmflags](ksetup-listrealmflags.md)
-   [Ksetup:setrealmflags](ksetup-setrealmflags.md)
-   [Ksetup:delrealmflags](ksetup-delrealmflags.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)