---
ms.assetid: d562ef46-f240-48be-bbd4-fd88fc6bbbdc
title: Настройка интрасети на основе форм проверки подлинности для устройств, не поддерживающих WIA
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: cddc5d890114dec7e0053b16701db6f03c3cbbdf
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889855"
---
# <a name="configuring-intranet-forms-based-authentication-for-devices-that-do-not-support-wia"></a>Настройка интрасети на основе форм проверки подлинности для устройств, не поддерживающих WIA

>Область применения. Windows Server 2016, Windows Server 2012 R2

По умолчанию включена встроенная проверка подлинности Windows (WIA) в службах Active Directory Federation (AD FS) в Windows Server 2012 R2 для запросов проверки подлинности, возникающих в рамках организации внутренней сети (интрасети) для любого приложения, использующего браузер для его проверки подлинности. Например это могут быть браузерных приложений, использующих WS-Federation или SAML и протоколы приложений, использующих протокол OAuth. WIA предоставляет конечным пользователям простой вход в приложения без необходимости ввода учетных данных вручную. Тем не менее некоторые устройства и браузеры не поддерживает WIA, и в результате происходит сбой проверки подлинности запросов с этих устройств. Кроме того взаимодействие на некоторые обозреватели, согласование протокола NTLM является нежелательным. Рекомендуется использовать в качестве резервной проверки подлинности на основе форм для таких устройств и браузеров.

AD FS в Windows Server 2016 и Windows Server 2012 R2 предоставляет администраторам возможность настройки списка агентов пользователя, которые поддерживают переход на проверку подлинности на основе форм. Резервный вариант стало возможным благодаря две конфигурации:


- **WIASupportedUserAgentStrings** свойство `Set-ADFSProperties` командлета
- **WindowsIntegratedFallbackEnabled** свойство `Set-AdfsGlobalAuthenticationPolicy` командлета

**WIASupportedUserAgentStrings** определяет агенты пользователей, которые поддерживают WIA. Службы федерации Active Directory анализирует строку агента пользователя при выполнении входа в браузере или в элемент управления браузера. Если компонент строки агента пользователя не соответствует ни одному из компонентов строку агента пользователя, которые настраиваются в **WIASupportedUserAgentStrings** свойство, AD FS вернется к обеспечивает аутентификацию на основе форм при условии, что **WindowsIntegratedFallbackEnabled** флаг имеет значение True.

По умолчанию новая установка AD FS имеет набор создан совпадение агента пользователя. Тем не менее это могут быть устаревшими по сравнению с учетом изменений в браузерах и устройствах. В частности устройства Windows имеют подобные строки агента пользователя с помощью вспомогательных вариантов в маркерах. В следующем примере Windows PowerShell предоставляет лучшие рекомендации для текущего набора устройств, которые находятся на рынке, поддерживающих WIA простой:

    Set-AdfsProperties -WIASupportedUserAgents @("MSIE 6.0", "MSIE 7.0; Windows NT", "MSIE 8.0", "MSIE 9.0", "MSIE 10.0; Windows NT 6", "Windows NT 6.3; Trident/7.0", "Windows NT 6.3; Win64; x64; Trident/7.0", "Windows NT 6.3; WOW64; Trident/7.0", "Windows NT 6.2; Trident/7.0", "Windows NT 6.2; Win64; x64; Trident/7.0", "Windows NT 6.2; WOW64; Trident/7.0", "Windows NT 6.1; Trident/7.0", "Windows NT 6.1; Win64; x64; Trident/7.0", "Windows NT 6.1; WOW64; Trident/7.0", "MSIPC", "Windows Rights Management Client")

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

Чтобы разрешить переход к проверки подлинности на основе формы для агентов пользователя не указаны в строке WIASupportedUserAgents, задайте для флага WindowsIntegratedFallbackEnabled true

    Set-AdfsGlobalAuthenticationPolicy -WindowsIntegratedFallbackEnabled $true

Также убедитесь, что проверка подлинности на основе форм включена для интрасети.

## <a name="configuring-wia-for-chrome"></a>Настройка WIA для Chrome
Chrome или другие агенты пользователя можно добавить к конфигурации AD FS, которая поддерживает WIA. Это позволяет простого входа в приложения без необходимости вручную ввести учетные данные при доступе к ресурсам, защищенным AD FS. Выполните следующие действия, чтобы включить WIA в Chrome.

Добавьте строку агента пользователя для Chrome в конфигурации AD FS

    Set-AdfsProperties -WIASupportedUserAgents ((Get-ADFSProperties | Select -ExpandProperty WIASupportedUserAgents) + “Chrome”)
    
Убедитесь, что строка агента пользователя для Chrome теперь задается в свойствах AD FS

    Get-AdfsProperties | Select -ExpandProperty WIASupportedUserAgents

![Настройка проверки подлинности](media/Configure-intranet-forms-based-authentication-for-devices-that-do-not-support-WIA/chrome1.png) 

>[!NOTE]   
> Выпущены новые браузеры и устройства рекомендуется согласовать возможности этих агентов пользователя и соответствующим образом обновить конфигурацию AD FS для оптимизации процесса проверки подлинности пользователя, когда с помощью другой стороны, обозревателей и устройств. В частности, мы рекомендуем повторно оценить **WIASupportedUserAgents** задание в AD FS, при добавлении нового типа устройства или браузера в матрице поддержки для WIA.


