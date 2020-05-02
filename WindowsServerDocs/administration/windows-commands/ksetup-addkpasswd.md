---
title: 'ksetup: аддкпассвд'
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d3196995-1b38-48ff-ba08-911cfab77317
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c260c711ae87f88be8b9466e73afaf3fe1c83a1e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724738"
---
# <a name="ksetupaddkpasswd"></a>ksetup: аддкпассвд



Добавляет адрес сервера пароля Kerberos (Кпассвд) для области.

## <a name="syntax"></a>Синтаксис

```
ksetup /addkpasswd <RealmName> [<KpasswdName>]
```

#### <a name="parameters"></a>Параметры

Если область Kerberos, в которой выполняется проверка подлинности на рабочей станции, поддерживает протокол Kerberos для изменения пароля, можно настроить клиентский компьютер под управлением операционной системы Windows для использования сервера паролей Kerberos. Этот параметр настраивается на стороне области.

|Параметр|Описание|
|---------|-----------|
|\<Реалмнаме>|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM и указывается в качестве области по умолчанию или области = при запуске **ksetup** .|
|\<Кпассвднаме>|Имя KDC, которое будет использоваться в качестве сервера паролей Kerberos, указывается как полное доменное имя без учета регистра, например mitkdc.microsoft.com. Если имя KDC пропущено, для размещения Кдкс может использоваться DNS.|

## <a name="remarks"></a>Примечания

Если область Kerberos, в которой выполняется проверка подлинности на рабочей станции, поддерживает протокол Kerberos для изменения пароля, можно настроить клиентский компьютер под управлением операционной системы Windows для использования сервера паролей Kerberos.

Выполните команду **ksetup** , чтобы проверить имя KDC. Если **кпассвд =** не отображается в выходных данных, сопоставление не было настроено.

Можно добавить дополнительные имена KDC по одному.

## <a name="examples"></a>Примеры

Настройте область, CORP. CONTOSO.COM, чтобы в качестве сервера паролей использовался сервер, отличный от Windows KDC, mitkdc.contoso.com:
```
ksetup /addkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```
Это приводит к подлинности сервера паролей Kerberos, отличного от Windows, который управляет всеми паролями для аутентификации между ним и областью.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Ksetup](ksetup.md)
-   [Ksetup:delkpasswd](ksetup-delkpasswd.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)