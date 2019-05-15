---
title: Настройка браузеры для использования встроенной проверки подлинности Windows (WIA) с AD FS
description: В этом документе описывается настройка браузеров на использование WIA с AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.custom: it-pro
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: f71680bb721635bd37197dca9d3ae4726099525f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59845485"
---
# <a name="configure-browsers-to-use-windows-integrated-authentication-wia-with-ad-fs"></a>Настройка браузеры для использования встроенной проверки подлинности Windows (WIA) с AD FS

По умолчанию включена встроенная проверка подлинности Windows (WIA) в службах Active Directory Federation (AD FS) в Windows Server 2012 R2 для запросов проверки подлинности, возникающих в рамках организации внутренней сети (интрасети) для любого приложения, использующего браузер для его проверки подлинности.

AD FS 2016 теперь имеет улучшенную по умолчанию параметр, позволяющий браузер Microsoft Edge продолжить WIA, пока не также (неправильно) перехват исключений Windows Phone, а также:

    =~Windows\s*NT.*Edge

Указанное выше означает больше не нужно настроить строку агента отдельных пользователей для поддержки стандартных сценариев Microsoft Edge, несмотря на то, что они обновляются довольно часто.

Для других браузеров, настройте свойство AD FS **WiaSupportedUserAgents** добавить необходимые зависимости в браузерах, при использовании значения.  Можно использовать приведенные ниже процедуры.



### <a name="view-wiasupporteduseragent-settings"></a>Просмотр параметров WIASupportedUserAgent
**WIASupportedUserAgents** определяет агенты пользователей, которые поддерживают WIA. Службы федерации Active Directory анализирует строку агента пользователя при выполнении входа в браузере или в элемент управления браузера.

Вы можете просмотреть текущие параметры, используя следующий пример PowerShell:

```powershell
    $strings = Get-AdfsProperties | select -ExpandProperty WiaSupportedUserAgents
```

![Поддержка WIA](../operations/media/Configure-AD-FS-Browser-WIA/wiasupport.png)

### <a name="change-wiasupporteduseragent-settings"></a>Изменение параметров WIASupportedUserAgent
По умолчанию новая установка AD FS имеет набор создан совпадение агента пользователя. Тем не менее это могут быть устаревшими по сравнению с учетом изменений в браузерах и устройствах. В частности устройства Windows имеют подобные строки агента пользователя с помощью вспомогательных вариантов в маркерах. В следующем примере Windows PowerShell предоставляет лучшие рекомендации для текущего набора устройств, которые находятся на рынке, поддерживающих WIA простой:

```powershell
    Set-AdfsProperties -WIASupportedUserAgents @("MSIE 6.0", "MSIE 7.0; Windows NT", "MSIE 8.0", "MSIE 9.0", "MSIE 10.0; Windows NT 6", "Windows NT 6.3; Trident/7.0", "Windows NT 6.3; Win64; x64; Trident/7.0", "Windows NT 6.3; WOW64; Trident/7.0", "Windows NT 6.2; Trident/7.0", "Windows NT 6.2; Win64; x64; Trident/7.0", "Windows NT 6.2; WOW64; Trident/7.0", "Windows NT 6.1; Trident/7.0", "Windows NT 6.1; Win64; x64; Trident/7.0", "Windows NT 6.1; WOW64; Trident/7.0", "MSIPC", "Windows Rights Management Client")
```

Приведенная выше команда убедитесь, что AD FS для WIA охватывает только следующих случаях:

Агенты пользователя|Варианты использования|
-----|-----|
MSIE 6.0|IE 6.0|
MSIE 7.0; Windows NT|Internet Explorer 7, IE в зоне интрасети. Фрагмент «Windows NT» отправляется с рабочего стола операционной системы.|
MSIE 8.0|IE 8.0 (устройства не отправить, так что необходимо сделать более конкретным)|
MSIE 9.0|(Нет устройств, отправлять, поэтому вам не нужно сделать это более конкретным) 9.0 IE|
MSIE 10.0; Windows NT 6|10.0 IE для Windows XP и более новых версиях операционной системы</br></br>Устройств Windows Phone 8.0 (с помощью, настроенному для мобильных устройств), исключаются, так как они отправляют</br></br>Агент пользователя: Mozilla/5.0 (совместим с; MSIE 10.0; Windows Phone 8.0; Trident/6.0; IEMobile/10.0; ARM; Touch; NOKIA; Lumia 920)|
Windows NT 6.3; Trident/7.0</br></br>Windows NT 6.3; Win64; x64; Trident/7.0</br></br>Windows NT 6.3; WOW64; Trident/7.0| Настольной операционной системы Windows 8.1, разных платформ|
Windows NT 6.2; Trident/7.0</br></br>Windows NT 6.2; Win64; x64; Trident/7.0</br></br>Windows NT 6.2; WOW64; Trident/7.0|Настольной операционной системы Windows 8, разных платформ|
Windows NT 6.1; Trident/7.0</br></br>Windows NT 6.1; Win64; x64; Trident/7.0</br></br>Windows NT 6.1; WOW64; Trident/7.0|Настольной операционной системы Windows 7, разных платформ|
MSIPC| Microsoft Information Protection и клиента управления|
Клиент Windows Rights Management|Клиент Windows Rights Management|
