---
title: ksetup:addkpasswd
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d3196995-1b38-48ff-ba08-911cfab77317
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2a85eb6dfe30c33126504744a7659fe2cc573087
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59856825"
---
# <a name="ksetupaddkpasswd"></a>ksetup:addkpasswd



Добавляет адрес сервера пароль (Kpasswd) Kerberos для сферы. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addkpasswd <RealmName> [<KpasswdName>]
```

### <a name="parameters"></a>Параметры

Если области Kerberos, что рабочая станция проверки подлинности для поддержки Kerberos изменить протокол паролей, можно настроить клиентский компьютер под управлением ОС Windows, чтобы использовать сервер пароль Kerberos. Этот параметр настроен со стороны сферы.

|Параметр|Описание|
|---------|-----------|
|\<RealmName>|Имя области указывается как верхний регистр DNS-имя, например CORP. CONTOSO.COM и для них значение по умолчанию области или области = при **ksetup** выполняется.|
|\<KpasswdName >|Без учета регистра полное доменное имя, например mitkdc.microsoft.com указанное имя контроллера Kerberos-домена, для использования в качестве сервера пароль Kerberos. Если отсутствует имя KDC, DNS может использоваться для поиска KDC.|

## <a name="remarks"></a>Примечания

Если области Kerberos, что рабочая станция проверки подлинности для поддержки Kerberos изменить протокол паролей, можно настроить клиентский компьютер под управлением ОС Windows, чтобы использовать сервер пароль Kerberos.

Выполните команду **ksetup** для проверки имени контроллера Kerberos-домена. Если **kpasswd =** не отображается в выходных данных, сопоставление не настроен.

Одновременно можно добавить дополнительные одному имени контроллера Kerberos-домена.

## <a name="BKMK_Examples"></a>Примеры

Настроить область, CORP. CONTOSO.COM, так что он использует сервер KDC, отличных от Windows, mitkdc.contoso.com, сервер паролей:
```
ksetup /addkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```
Результатом на сервере Windows Kerberos пароль, который контролирует все пароли для проверки подлинности между ним и области.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [ksetup:delkpasswd](ksetup-delkpasswd.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)