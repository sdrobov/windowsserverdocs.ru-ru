---
title: "Настройка браузерами для использования встроенной проверки подлинности Windows (WIA) с AD FS"
description: "В этом документе описывается настройка браузеры, чтобы использовать WIA с AD FS"
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.custom: it-pro
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: f7d43931d1fe4958a539ff1b728e4cc154d06248
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="configure-browsers-to-use-windows-integrated-authentication-wia-with-ad-fs"></a>Настройка браузерами для использования встроенной проверки подлинности Windows (WIA) с AD FS

По умолчанию встроенной проверки подлинности Windows (WIA) включена в службах федерации Active Directory (AD FS) в Windows Server 2012 R2 для запросов проверки подлинности, возникающих в организации по внутренней сети (интрасети) для любого приложения, которое использует браузер для его проверки подлинности.

AD FS 2016 теперь имеет параметра улучшенные по умолчанию, который позволяет браузеру Edge делать WIA, пока не также (неправильно) перехватывать Windows Phone, а также:

    =~Windows\s*NT.*Edge

Средство выше, больше не нужно настраивать строки агента отдельного пользователя к полезными в распространенных сценариях Edge, несмотря на то, что довольно часто обновляются.

Для других браузеров, настройте свойства Служб федерации Active Directory **WiaSupportedUserAgents** добавить необходимые значения на основе в браузерах, которые вы используете.  Можно использовать описанные ниже процедуры.



### <a name="view-wiasupporteduseragent-settings"></a>Просмотр параметров WIASupportedUserAgent
**WIASupportedUserAgents** определяет агентов пользователя, поддерживающих WIA. AD FS анализирует строку агента пользователя, при выполнении входа в веб-обозревателе или управления браузера.

Можно просмотреть текущие параметры, в следующем примере PowerShell:

```powershell
    $strings = Get-AdfsProperties | select -ExpandProperty WiaSupportedUserAgents
```

![Поддержка WIA](../operations/media/Configure-AD-FS-Browser-WIA/wiasupport.png)

### <a name="change-wiasupporteduseragent-settings"></a>Изменение параметров WIASupportedUserAgent
По умолчанию новой установки Служб федерации Active Directory имеет ряд создан совпадение агента пользователя. Тем не менее это могут быть истек срок действия на основе изменений браузерах и устройствах. Особенно устройства Windows имеют аналогичные строки агента пользователя с небольшими отличиями в маркеров. Следующий пример Windows PowerShell предоставляет лучшие рекомендации для текущего набора устройств, которые находятся на рынке уже сегодня, поддерживающих WIA безупречное:

```powershell
    Set-AdfsProperties -WIASupportedUserAgents @("MSIE 6.0", "MSIE 7.0; Windows NT", "MSIE 8.0", "MSIE 9.0", "MSIE 10.0; Windows NT 6", "Windows NT 6.3; Trident/7.0", "Windows NT 6.3; Win64; x64; Trident/7.0", "Windows NT 6.3; WOW64; Trident/7.0", "Windows NT 6.2; Trident/7.0", "Windows NT 6.2; Win64; x64; Trident/7.0", "Windows NT 6.2; WOW64; Trident/7.0", "Windows NT 6.1; Trident/7.0", "Windows NT 6.1; Win64; x64; Trident/7.0", "Windows NT 6.1; WOW64; Trident/7.0", "MSIPC", "Windows Rights Management Client")
```

Указанной выше команды убедитесь, что службы федерации Active Directory для WIA охватывает только следующие варианты использования:

Агенты пользователя|Варианты использования|
-----|-----|
MSIE 6.0|IE 6.0|
MSIE 7.0; Windows NT|IE 7, IE в зону интрасети. Фрагмент «Windows NT» отправляется настольных операционных систем.|
MSIE 8.0|IE 8.0 (устройства не отправлять это, поэтому необходимо, чтобы более конкретные)|
MSIE 9.0|IE 9.0 (устройства не отправлять, не нужно сделать более конкретные)|
MSIE 10.0; Windows NT 6|10.0 IE для Windows XP и более новыми версиями операционных систем настольного компьютера</br></br>Устройства Windows Phone 8.0 (с, настроенному для мобильных устройств), исключаются, так как отправляют</br></br>Агент пользователя: Mozilla/5.0 (совместимо; MSIE 10.0; Windows Phone 8.0; Trident/6.0; IEMobile или 10.0; ARM; Сенсорного ввода; NOKIA; Lumia 920)|
Windows NT 6.3; Trident/7.0</br></br>Windows NT 6.3; Win64; x64; Trident/7.0</br></br>Windows NT 6.3; WOW64; Trident/7.0| Windows 8.1 операционных систем настольного компьютера, различных платформ|
Windows NT 6.2; Trident/7.0</br></br>Windows NT 6.2; Win64; x64; Trident/7.0</br></br>Windows NT 6.2; WOW64; Trident/7.0|Windows 8 операционная система различных платформ|
Windows NT 6.1; Trident/7.0</br></br>Windows NT 6.1; Win64; x64; Trident/7.0</br></br>Windows NT 6.1; WOW64; Trident/7.0|Windows 7 операционных систем настольного компьютера, другой platoforms|
MSIPC| Защита информации Microsoft и клиента управления|
Клиент управления правами Windows|Клиент управления правами Windows|
