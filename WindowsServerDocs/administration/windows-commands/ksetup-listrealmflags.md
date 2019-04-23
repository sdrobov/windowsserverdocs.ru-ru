---
title: ksetup:listrealmflags
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 1bc4be8be747c31d60d75c90ad3aa831dd8dff93
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59838305"
---
# <a name="ksetuplistrealmflags"></a>ksetup:listrealmflags



Перечисляются доступные области флаги, которые могут возвратить **ksetup**. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /listrealmflags
```

### <a name="parameters"></a>Параметры

Нет

## <a name="remarks"></a>Примечания

Флаги сферы укажите дополнительные функции сферы Kerberos не под управлением Windows. Компьютеры под управлением Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2 можно использовать Kerberos не под управлением Windows server для администрирования проверку подлинности вместо использования домена под управлением операционной системы Windows Server. Эти системы участвовать в область Kerberos, а не в домене Windows. Эта запись устанавливает компоненты области. В следующей таблице описан каждый.

|Значение|Флаг сферы|Описание|
|-----|----------|-----------|
|0xF|Все|Установлены все флаги области.|
|0x00|Нет|Флаги сферы не установлены, и дополнительные компоненты не включены.|
|0x01|SendAddress|IP-адрес включается в билетов предоставления билетов.|
|0x02|TcpSupported|Протокол управления передачей (TCP) и протокола UDP (User Datagram) поддерживаются в этой сфере.|
|0x04|Делегирование|Всем пользователям в этой сфере доверена для делегирования.|
|0x08|NcSupported|Это область поддерживает канонизации имя, что DNS и сферы, стандарты именования.|
|0x80|RC4|Это область поддерживает шифрование RC4 для включения доверительные отношения между сферами, который позволяет использовать TLS.|

Флаги сферы хранятся в реестре в **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\*** сферы-name *. Эта запись не существует в реестре по умолчанию. Можно использовать [Ksetup:addrealmflags](ksetup-addrealmflags.md) команду, чтобы добавить в реестр.

## <a name="BKMK_Examples"></a>Примеры

Перечисление флагов известные области на этом компьютере:
```
ksetup /listrealmflags
```
Задать флаги доступных сферы, **Ksetup** не знает, введя одну из приведенных ниже команд в командной строке:
```
ksetup /setrealmflags CORP.CONTOSO.COM sendaddress tcpsupported delete ncsupported
```
```
ksetup /setrealmflags CORP.CONTOSO.COM 0xF
```

#### <a name="additional-references"></a>Дополнительная справка

-   [ksetup:setrealmflags](ksetup-setrealmflags.md)
-   [ksetup:addrealmflags](ksetup-addrealmflags.md)
-   [ksetup:delrealmflags](ksetup-delrealmflags.md)
-   [Ksetup](ksetup.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)