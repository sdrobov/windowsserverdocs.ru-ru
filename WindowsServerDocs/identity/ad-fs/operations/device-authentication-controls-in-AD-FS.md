---
title: Элементы управления аутентификацией устройств в AD FS
description: В этом документе описано, как включить проверку подлинности устройства в AD FS для Windows Server 2016 и 2012 R2
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 11/09/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 87c011b18ad4a1d464072c1ea90b09a44e831378
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407368"
---
# <a name="device-authentication-controls-in-ad-fs"></a>Элементы управления аутентификацией устройств в AD FS
В следующем документе показано, как включить элементы управления проверки подлинности устройств в Windows Server 2016 и 2012 R2.

## <a name="device-authentication-controls-in-ad-fs-2012-r2"></a>Элементы управления аутентификацией устройств в AD FS 2012 R2
Первоначально в AD FS 2012 R2 было одно глобальное свойство проверки подлинности с именем `DeviceAuthenticationEnabled`, которое управляет проверкой подлинности устройства.

Чтобы настроить этот параметр, используется командлет `Set-AdfsGlobalAuthenticationPolicy`, как показано ниже.


``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationEnabled $true
```



Для отключения проверки подлинности устройства использовался тот же командлет, чтобы присвоить значение $false.

## <a name="device-authentication-controls-in-ad-fs-2016"></a>Элементы управления аутентификацией устройств в AD FS 2016
Единственным типом проверки подлинности устройств, поддерживаемым в 2012 R2, было проверка.  В AD FS 2016 в дополнение к проверка существует два новых типа проверки подлинности устройства для проверки подлинности современных устройств.  Эти особые значения приведены ниже.
- пкэйаус
- PRT

Для управления новым поведением свойство `DeviceAuthenticationEnabled` используется в сочетании с новым свойством с именем `DeviceAuthenticationMethod`.  

Метод проверки подлинности устройства определяет тип проверки подлинности устройства, которая будет выполнена: PRT, Пкэйаус, проверка или некоторое сочетание.
Он имеет следующие значения:
 - Сигнедтокен: Только PRT
 - Пкэйаус: PRT + Пкэйаус
 - Проверка PRT + проверка
 - Все: Все вышеперечисленное

Как видите, PRT является частью всех методов проверки подлинности устройства, что делает его действительным методом по умолчанию, который всегда включен, если `DeviceAuthenticationEnabled` имеет значение `$true`.

Пример. Чтобы настроить методы, используйте командлет Девицеаусентикатионенаблед, как описано выше, а также новое свойство:

``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationEnabled $true
```

>[!NOTE]
> В ADFS 2019 `DeviceAuthenticationMethod` можно использовать с командой `Set-AdfsRelyingPartyTrust`.

``` powershell
PS:\>Set-AdfsRelyingPartyTrust -DeviceAuthenticationMethod ClientTLS
```

>[!NOTE]
> Включение проверки подлинности устройства (установка `DeviceAuthenticationEnabled` в `$true`) означает, что `DeviceAuthenticationMethod` неявно имеет значение `SignedToken`, что соответствует **PRT**.


``` powershell
PS:\>Set-AdfsGlobalAuthenticationPolicy –DeviceAuthenticationMethod All
```
> [!NOTE]
> По умолчанию используется метод проверки подлинности устройства `SignedToken`.  Другие значения — **пкэйаус,** <strong>Проверка</strong> и **ALL**.

Значения `DeviceAuthenticationMethod` изменились немного с момента выпуска AD FS 2016.  Значения каждого из значений в зависимости от уровня обновления см. в таблице ниже.


|Версия AD FS|Значение Девицеаусентикатионмесод|Понимает|
| ----- | ----- | ----- |
|2016 RTM|сигнедтокен|PRT + Пкэйаус|
||Проверка|Проверка|
||Все|PRT + Пкэйаус + проверка|
|2016 RTM + в актуальном состоянии с Центр обновления Windows|Сигнедтокен (измененное значение)|PRT (только)|
||Пкэйаус (новое)|PRT + Пкэйаус|
||Проверка|PRT + проверка|
||Все|PRT + Пкэйаус + проверка|

## <a name="see-also"></a>См. также
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)
