---
title: Элементы управления проверки подлинности устройств в AD FS
description: В этом документе описывается, как включить проверку подлинности устройств в AD FS для Windows Server 2016 и 2012 R2
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 11/09/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: f52d3d237573e4ed0028e228ff80273862a0aaf2
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66444643"
---
# <a name="device-authentication-controls-in-ad-fs"></a>Элементы управления проверки подлинности устройств в AD FS
Следующий документ показано, как включить элементы управления проверки подлинности устройства в Windows Server 2016 и 2012 R2.

## <a name="device-authentication-controls-in-ad-fs-2012-r2"></a>Элементы управления проверки подлинности устройств в AD FS 2012 R2
Изначально в AD FS 2012 R2 было одно свойство, глобальные проверки подлинности, называемую `DeviceAuthenticationEnabled` , проверку подлинности устройство.

Настройка параметров, `Set-AdfsGlobalAuthenticationPolicy` командлет использовался, как показано ниже:


``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationEnabled $true
```



Чтобы отключить проверку подлинности устройств, тот же командлет использовался присвоено значение $false.

## <a name="device-authentication-controls-in-ad-fs-2016"></a>Элементы управления проверки подлинности устройств в AD FS 2016
Это единственный тип проверки подлинности устройства, поддерживаемые в 2012 R2 был clientTLS.  В AD FS 2016 в дополнение к clientTLS существует два новых типа проверки подлинности устройства для проверки подлинности для современных устройств.  Эти особые значения приведены ниже.
- PKeyAuth
- PRT

Для управления поведением новой, `DeviceAuthenticationEnabled` свойство используется в сочетании с новое свойство с именем `DeviceAuthenticationMethod`.  

Метод проверки подлинности устройства определяет тип проверки подлинности устройства, который будет выполняться. PRT, PKeyAuth, clientTLS или сочетания.
Он имеет следующие значения:
 - SignedToken: Только PRT
 - PKeyAuth: PRT + PKeyAuth
 - ClientTLS: PRT + clientTLS
 - Все: Все вышеперечисленное

Как вы видите, PRT является частью всех способов проверки подлинности устройства, делая его в силу метод по умолчанию, которая всегда включена, когда `DeviceAuthenticationEnabled` присваивается `$true`.

Пример. Чтобы настроить метод или методы, используйте DeviceAuthenticationEnabled командлет как выше, а также новое свойство:

``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationEnabled $true
```

>[!NOTE]
> В ADFS 2019 `DeviceAuthenticationMethod` может использоваться с `Set-AdfsRelyingPartyTrust` команды.

``` powershell
PS:\>Set-AdfsRelyingPartyTrust -DeviceAuthenticationMethod ClientTLS
```

>[!NOTE]
> Включение проверки подлинности устройства (параметр `DeviceAuthenticationEnabled` для `$true`) означает, что `DeviceAuthenticationMethod` неявно устанавливается значение `SignedToken`, которое соответствует **PRT**.


``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationMethod All
```
> [!NOTE]
> Метод проверки подлинности устройства по умолчанию — `SignedToken`.  Другие значения: **PKeyAuth,** <strong>ClientTLS,</strong> и **все**.

Они означают `DeviceAuthenticationMethod` значения были немного изменены с момента выпуска AD FS 2016.  См. в таблице ниже значение каждого значения в зависимости от уровня обновления:


|Версии AD FS|Значение DeviceAuthenticationMethod|Означает, что|
| ----- | ----- | ----- |
|2016 RTM|SignedToken|PRT + PkeyAuth|
||clientTLS|clientTLS|
||Все|PRT + PkeyAuth + clientTLS|
|2016 RTM + вверх до даты с центром обновления Windows|SignedToken (измененные значения)|PRT (только)|
||PkeyAuth (новое)|PRT + PkeyAuth|
||clientTLS|PRT + clientTLS|
||Все|PRT + PkeyAuth + clientTLS|

## <a name="see-also"></a>См. также
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
