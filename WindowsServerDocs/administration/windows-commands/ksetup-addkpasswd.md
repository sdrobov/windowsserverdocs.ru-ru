---
title: 'ksetup: аддкпассвд'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d3196995-1b38-48ff-ba08-911cfab77317
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 73abfff54ecfcd31ebbd7469c12228fff850fbf1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841827"
---
# <a name="ksetupaddkpasswd"></a>ksetup: аддкпассвд



Добавляет адрес сервера пароля Kerberos (Кпассвд) для области. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addkpasswd <RealmName> [<KpasswdName>]
```

#### <a name="parameters"></a>Параметры

Если область Kerberos, в которой выполняется проверка подлинности на рабочей станции, поддерживает протокол Kerberos для изменения пароля, можно настроить клиентский компьютер под управлением операционной системы Windows для использования сервера паролей Kerberos. Этот параметр настраивается на стороне области.

|Параметр|Описание|
|---------|-----------|
|\<Реалмнаме >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM и указывается в качестве области по умолчанию или области = при запуске **ksetup** .|
|\<Кпассвднаме >|Имя KDC, которое будет использоваться в качестве сервера паролей Kerberos, указывается как полное доменное имя без учета регистра, например mitkdc.microsoft.com. Если имя KDC пропущено, для размещения Кдкс может использоваться DNS.|

## <a name="remarks"></a>Примечания

Если область Kerberos, в которой выполняется проверка подлинности на рабочей станции, поддерживает протокол Kerberos для изменения пароля, можно настроить клиентский компьютер под управлением операционной системы Windows для использования сервера паролей Kerberos.

Выполните команду **ksetup** , чтобы проверить имя KDC. Если **кпассвд =** не отображается в выходных данных, сопоставление не было настроено.

Можно добавить дополнительные имена KDC по одному.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Настройте область, CORP. CONTOSO.COM, чтобы в качестве сервера паролей использовался сервер, отличный от Windows KDC, mitkdc.contoso.com:
```
ksetup /addkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```
Это приводит к подлинности сервера паролей Kerberos, отличного от Windows, который управляет всеми паролями для аутентификации между ним и областью.

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup](ksetup.md)
-   [Ksetup:delkpasswd](ksetup-delkpasswd.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)