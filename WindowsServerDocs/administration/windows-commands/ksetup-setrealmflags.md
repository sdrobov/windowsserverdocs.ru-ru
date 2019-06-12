---
title: ksetup:setrealmflags
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bcb2824e-fba7-4ebe-be62-e62b4fae5b17
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 249eb82bb40890e071bd7d1eca3a0201064fa01e
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66437942"
---
# <a name="ksetupsetrealmflags"></a>ksetup:setrealmflags



Задает флаги сферы для указанной области. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /setrealmflags <RealmName> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<RealmName>|Имя области указывается как верхний регистр DNS-имя, например CORP. CONTOSO.COM.|
|Флаг сферы|Обозначает одно из следующих флагов:</br>-SendAddress</br>-TcpSupported</br>-Делегат</br>-NcSupported</br>— RC4|

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

Флаги сферы хранятся в разделе реестра **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\\** <em>RealmName</em>. Эта запись не существует в реестре по умолчанию. Можно использовать [Ksetup:addrealmflags](ksetup-addrealmflags.md) команду, чтобы добавить в реестр.

Можно узнать, какие флаги сферы доступны и установить, просмотрев выходные данные **ksetup**.

## <a name="BKMK_Examples"></a>Примеры

Перечисление флаги сферы доступна и задайте для области CONTOSO:
```
ksetup
```
Задайте двух флагов, которые не были заданы в настоящее время:
```
ksetup /setrealmflags CONTOSO ncsupported delegate
```
Запустите **ksetup** команду, чтобы проверить, что флаг сферы, просматривая выходные данные и ищет **флаги сферы =** .

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup:listrealmflags](ksetup-listrealmflags.md)
-   [Ksetup:addrealmflags](ksetup-addrealmflags.md)
-   [Ksetup:delrealmflags](ksetup-delrealmflags.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)