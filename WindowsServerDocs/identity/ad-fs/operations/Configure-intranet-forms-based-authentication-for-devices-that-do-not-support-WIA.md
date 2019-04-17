---
ms.assetid: d562ef46-f240-48be-bbd4-fd88fc6bbbdc
title: "Настройка интрасети на основе форм проверки подлинности для устройств, не поддерживающих WIA"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: c78dc702cbff8eab487c6c077dfe57b0f0663342
ms.sourcegitcommit: 5012c078b410f59261edf0cc917393467243a5c7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="configuring-intranet-forms-based-authentication-for-devices-that-do-not-support-wia"></a>Настройка интрасети на основе форм проверки подлинности для устройств, не поддерживающих WIA

>Область применения: Windows Server 2016, Windows Server 2012 R2

По умолчанию встроенной проверки подлинности Windows (WIA) включена в службах федерации Active Directory (AD FS) в Windows Server 2012 R2 для запросов проверки подлинности, возникающих в организации по внутренней сети (интрасети) для любого приложения, которое использует браузер для его проверки подлинности. Например это могут быть на основе браузера приложения, использующие WS-Federation или SAML протоколов и приложений, использующих протокол OAuth. WIA позволяет конечным пользователям с помощью общего входа для приложений без необходимости вручную ввести свои учетные данные. Тем не менее некоторые устройства и браузеры, не поддерживают WIA, и в результате невозможна запросы на проверку подлинности с этих устройств. Кроме того процесс в некоторых браузерах, которые согласовать NTLM может быть нежелательно. Рекомендуется для возврата к проверке подлинности на основе форм для таких устройств и браузеров.

AD FS в Windows Server 2016 и Windows Server 2012 R2 предоставляет администраторам возможность настройки списку агентов пользователя, которые поддерживают резервный вариант для проверки подлинности на основе форм. Резервный вариант стало возможным благодаря две конфигурации:


- **WIASupportedUserAgentStrings** свойства `Set-ADFSProperties` командлетов для
- **WindowsIntegratedFallbackEnabled** свойства `Set-AdfsGlobalAuthenticationPolicy` commmandlet

**WIASupportedUserAgentStrings** определяет агентов пользователя, поддерживающих WIA. AD FS анализирует строку агента пользователя, при выполнении входа в веб-обозревателе или управления браузера. Если компонент строку агента пользователя не соответствует ни компонентов строки агента пользователя, которые настроены в **WIASupportedUserAgentStrings** свойства службы федерации Active Directory будет возвращаться к аутентификацию на основе форм, при условии, что **WindowsIntegratedFallbackEnabled** флаг установлен в значение True.

По умолчанию новой установки Служб федерации Active Directory имеет ряд создан совпадение агента пользователя. Тем не менее это могут быть истек срок действия на основе изменений браузерах и устройствах. Особенно устройства Windows имеют аналогичные строки агента пользователя с небольшими отличиями в маркеров. Следующий пример Windows PowerShell предоставляет лучшие рекомендации для текущего набора устройств, которые находятся на рынке уже сегодня, поддерживающих WIA безупречное:

    Set-AdfsProperties -WIASupportedUserAgents @("MSIE 6.0", "MSIE 7.0; Windows NT", "MSIE 8.0", "MSIE 9.0", "MSIE 10.0; Windows NT 6", "Windows NT 6.3; Trident/7.0", "Windows NT 6.3; Win64; x64; Trident/7.0", "Windows NT 6.3; WOW64; Trident/7.0", "Windows NT 6.2; Trident/7.0", "Windows NT 6.2; Win64; x64; Trident/7.0", "Windows NT 6.2; WOW64; Trident/7.0", "Windows NT 6.1; Trident/7.0", "Windows NT 6.1; Win64; x64; Trident/7.0", "Windows NT 6.1; WOW64; Trident/7.0", "MSIPC", "Windows Rights Management Client")

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
Windows NT 6.1; Trident/7.0</br></br>Windows NT 6.1; Win64; x64; Trident/7.0</br></br>Windows NT 6.1; WOW64; Trident/7.0|Windows 7 операционных систем настольного компьютера, различных платформ|
MSIPC| Защита информации Microsoft и клиента управления|
Клиент управления правами Windows|Клиент управления правами Windows|

Чтобы включить возврата к проверке подлинности на основе форм для агентов пользователя, кроме тех, указанный в строке WIASupportedUserAgents, установите флаг WindowsIntegratedFallbackEnabled значение true

    Set-AdfsGlobalAuthenticationPolicy -WindowsIntegratedFallbackEnabled $true

Также убедитесь, что проверка подлинности на основе форм включено для интрасети.

## <a name="configuring-wia-for-chrome"></a>Настройка WIA для Chrome
Конфигурацию AD FS, которая поддерживает WIA можно добавить Chrome или других агентов пользователя. Это позволяет общего входа для приложений без необходимости вручную ввести учетные данные при доступе к ресурсам, защищенным AD FS. Выполните следующие действия, чтобы включить WIA на Chrome.

Добавить строку агента пользователя для Chrome в конфигурации AD FS

    Set-AdfsProperties -WIASupportedUserAgents ((Get-ADFSProperties | Select -ExpandProperty WIASupportedUserAgents) + “Chrome”)
    
Убедиться, что строку агента пользователя для Chrome теперь значение в свойствах AD FS

    Get-AdfsProperties | Select -ExpandProperty WIASupportedUserAgents

![Настройка проверки подлинности](media/Configure-intranet-forms-based-authentication-for-devices-that-do-not-support-WIA/chrome1.png) 

>[!NOTE]   
> Выпущены новые браузерах и устройствах рекомендуется согласовать возможности этих агентов пользователя и соответствующим образом изменить конфигурацию AD FS для оптимизации пользователем проверки подлинности при с помощью сказал браузера и устройств. В частности, рекомендуется повторно оценить **WIASupportedUserAgents** параметр в AD FS, при добавлении нового типа устройства или браузера в вашей матрице поддержки для WIA.


