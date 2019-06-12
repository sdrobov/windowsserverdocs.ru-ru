---
title: ksetup:delrealmflags
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 22053041-1eb4-47f5-bed9-3d5681bcde7d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fd2a3897a07a2eda4c05526b0ae8c55dda35e1e9
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66437988"
---
# <a name="ksetupdelrealmflags"></a>ksetup:delrealmflags



Удаляет флаги сферы из указанной области.  Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /delrealmflags <RealmName> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<RealmName>|Имя области указывается как верхний регистр DNS-имя, например CORP. CONTOSO.COM и для них область по умолчанию при **Ksetup** выполняется.|

## <a name="remarks"></a>Примечания

Флаги сферы укажите дополнительные функции сферы Kerberos, не зависит от операционной системы Windows Server. Компьютеры под управлением Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2 можно использовать сервер Kerberos для администрирования проверку подлинности вместо использования домена под управлением операционной системы Windows Server, и эти системы участвовать в Область Kerberos. Эта запись устанавливает компоненты области. В следующей таблице описан каждый.

|Значение|Флаг сферы|Описание|
|-----|----------|-----------|
|0xF|Все|Установлены все флаги области.|
|0x00|Нет|Флаги сферы не установлены, и дополнительные компоненты не включены.|
|0x01|SendAddress|IP-адрес включается в пределах--действия билетов предоставления билета.|
|0x02|TcpSupported|Протокол управления передачей (TCP) и протокола UDP (User Datagram) поддерживаются в этой сфере.|
|0x04|Делегирование|Всем пользователям в этой сфере доверена для делегирования.|
|0x08|NcSupported|Это область поддерживает канонизации имя, что DNS и сферы, стандарты именования.|
|0x80|RC4|Это область поддерживает шифрование RC4 для включения доверительные отношения между сферами, который позволяет использовать TLS.|

Флаги сферы хранятся в реестре в **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\\** <em>RealmName</em>. Эта запись не существует в реестре по умолчанию. Можно использовать [Ksetup:addrealmflags](ksetup-addrealmflags.md) команду, чтобы добавить в реестр.

Можно узнать, какие флаги сферы доступны и установить, просмотрев выходные данные **ksetup** или **ksetup /dumpstate**.

## <a name="BKMK_Examples"></a>Примеры

Отображение списка доступных сферы флаги для сферы CONTOSO:
```
Ksetup /listrealmflags
```
Удалите два флаги, используемые в данный момент в наборе:
```
ksetup /delrealmflags CONTOSO ncsupported delegate
```
Запустите **ksetup** команду, чтобы проверить, что флаг сферы, просматривая выходные данные и ищет **флаги сферы =** .

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup:listrealmflags](ksetup-listrealmflags.md)
-   [Ksetup:setrealmflags](ksetup-setrealmflags.md)
-   [Ksetup:addrealmflags](ksetup-addrealmflags.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)