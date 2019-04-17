---
title: "Элементы управления устройства проверки подлинности в AD FS"
description: "В этом документе описывается включение проверки подлинности устройства в AD FS в Windows Server 2016 и 2012 R2"
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 11/09/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: d66cfde20060229844c34abeea85dd83b802ddad
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="device-authentication-controls-in-ad-fs"></a>Элементы управления устройства проверки подлинности в AD FS
Следующий документ показано, как включить элементы управления устройства проверки подлинности в Windows Server 2016 и 2012 R2.

## <a name="device-authentication-controls-in-ad-fs-2012-r2"></a>Элементы управления устройства проверки подлинности в AD FS 2012 R2
Изначально в AD FS 2012 R2, один из которых называется свойства глобальные проверки подлинности было `DeviceAuthenticationEnabled`проверки подлинности управляемого устройства.

Настройка параметров, `Set-AdfsGlobalAuthenticationPolicy`использовался командлет, как показано ниже:


``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationEnabled $true
```



Чтобы отключить проверку подлинности устройства, тот же командлет использовался для значение $false.

## <a name="device-authentication-controls-in-ad-fs-2016"></a>Элементы управления устройства проверки подлинности в AD FS 2016
Единственный тип проверки подлинности устройства, поддерживаемые в 2012 R2 была clientTLS.  В AD FS 2016 помимо clientTLS существует два новых типа проверки подлинности устройства для проверки подлинности современных устройствах.  Перечислены ниже.
- PKeyAuth
- PRT

Для управления новое поведение `DeviceAuthenticationEnabled`свойства используется в сочетании с новой свойство, которое называется `DeviceAuthenticationMethod`.  

Метод проверки подлинности устройства определяет тип проверки подлинности устройства, который будет выполняться: PRT, PKeyAuth clientTLS, или в сочетании.
Он имеет следующие значения:
 - SignedToken: Только PRT
 - PKeyAuth: PRT + PKeyAuth
 - ClientTLS: PRT + clientTLS 
 - Все: Все вышеперечисленное

Как видно, PRT является частью всех способов проверки подлинности устройств, делая в силу метод по умолчанию, которая всегда включена, когда `DeviceAuthenticationEnabled`имеет значение `$true`.

Пример: Чтобы настроить методы, используйте DeviceAuthenticationEnabled командлет как выше, а также новые свойства:

``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationEnabled $true
```
>[!NOTE]
> Включение проверки подлинности устройства (параметр `DeviceAuthenticationEnabled`для `$true`) означает `DeviceAuthenticationMethod`явным образом задают `SignedToken`, который соответствует **PRT **.


``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationMethod All
```
>[!NOTE]
>Метод проверки подлинности устройства по умолчанию —`SignedToken`.  Другие значения **PKeyAuth, *** ClientTLS,** и **все **.

Смысл `DeviceAuthenticationMethod`значения немного изменены с момента выпуска AD FS 2016.  См. в таблице ниже описание каждого из значений, в зависимости от уровня обновления:


|Версия AD FS|Значение DeviceAuthenticationMethod|Означает|
| ----- | ----- | ----- |
|2016 RTM|SignedToken|PRT + PkeyAuth|
||clientTLS|clientTLS|
||Все|PRT + PkeyAuth + clientTLS|
|2016 RTM + обновление с центра обновления Windows|SignedToken (измененное значение)|PRT (только)|
||PkeyAuth (Новинка)|PRT + PkeyAuth|
||clientTLS|PRT + clientTLS|
||Все|PRT + PkeyAuth + clientTLS|

## <a name="see-also"></a>См. также:
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
