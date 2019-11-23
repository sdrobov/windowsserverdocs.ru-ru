---
title: 'ksetup: аддкпассвд'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 72c27cb6b068dc46cd58e753b4b08d68b39bfb20
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375190"
---
# <a name="ksetupaddkpasswd"></a>ksetup: аддкпассвд



Добавляет адрес сервера пароля Kerberos (Кпассвд) для области. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addkpasswd <RealmName> [<KpasswdName>]
```

### <a name="parameters"></a>Параметры

Если область Kerberos, в которой выполняется проверка подлинности на рабочей станции, поддерживает протокол Kerberos для изменения пароля, можно настроить клиентский компьютер под управлением операционной системы Windows для использования сервера паролей Kerberos. Этот параметр настраивается на стороне области.

|Параметр|Описание|
|---------|-----------|
|\<Реалмнаме >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM и указывается в качестве области по умолчанию или области = при запуске **ksetup** .|
|\<Кпассвднаме >|Имя KDC, которое будет использоваться в качестве сервера паролей Kerberos, указывается как полное доменное имя без учета регистра, например mitkdc.microsoft.com. Если имя KDC пропущено, для размещения Кдкс может использоваться DNS.|

## <a name="remarks"></a>Замечания

Если область Kerberos, в которой выполняется проверка подлинности на рабочей станции, поддерживает протокол Kerberos для изменения пароля, можно настроить клиентский компьютер под управлением операционной системы Windows для использования сервера паролей Kerberos.

Выполните команду **ksetup** , чтобы проверить имя KDC. Если **кпассвд =** не отображается в выходных данных, сопоставление не было настроено.

Можно добавить дополнительные имена KDC по одному.

## <a name="BKMK_Examples"></a>Примеров

Настройте область, CORP. CONTOSO.COM, чтобы в качестве сервера паролей использовался сервер, отличный от Windows KDC, mitkdc.contoso.com:
```
ksetup /addkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```
Это приводит к подлинности сервера паролей Kerberos, отличного от Windows, который управляет всеми паролями для аутентификации между ним и областью.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Ksetup:delkpasswd](ksetup-delkpasswd.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)