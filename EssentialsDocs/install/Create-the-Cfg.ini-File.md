---
title: "Создание файла Cfg.ini"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 93a73556-22ef-402d-b8d4-582b74c22bcf
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 967db5f36ea27fb04eab9a6682a106ba0072d45d
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="create-the-cfgini-file"></a>Создание файла Cfg.ini

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Файл cfg.ini используется для автоматизации установки операционной системы в следующем сценарии:  
  
-   При тестировании работы конечного пользователя с помощью образа, предварительно установленного на целевом компьютере, раздел начальной настройки используется для пошагового выполнения установки в автоматическом или ручном режиме. Чтобы сделать это, в разделе [Создание раздела начальной настройки](Create-the-Cfg.ini-File.md#BKMK_CreateInit2).  
  
##  <a name="BKMK_CreateInit2"></a>Создание раздела начальной настройки  
 Используйте раздел Initial Configuration файла cfg.ini для пошагового выполнения установки в автоматическом или ручном режиме.  
  
#### <a name="to-define-the-initial-configuration-section"></a>Определение раздела начальной настройки  
  
1.  Откройте в блокноте файл cfg.ini, если он существует; в противном случае — создайте новый файл.  
  
2.  Добавьте следующий текст, чтобы создать раздел InitialConfiguration.  
  
    ```  
  
    [InitialConfiguration]  
    ;Optional, display language can only be one of the installed language  
    Language=en-us  
    ;Optional, The name of a script that runs after setupComplete.cmd but before the initial configuration begins.  
    ;Optional  
    Locale=en-us  
    ;Optional  
    Country=US  
    ;Optional  
    Keyboard=0409:00000409  
    AcceptEula=true  
    ;This is only required on a server where an OEM EULA has been specified   
    ;by using the OOBE.xml file  
    AcceptOEMEula=true  
    ;Optional. Example: My Company Name  
    CompanyName=EnterCompanyName  
    ServerName=EnterServerName  
    ; Example: CONTOSO  
    NetbiosName=EnterNetbiosDomainName  
    ; Example: contoso.local  
    DNSName=EnterDNSDomain   
    ; Used to set the user name for the domain admin  
    UserName=EnterDomainAdminUserName  
    ;The password has to be strong and at least 8 characters  
    PlainTextPassword=EnterAdminPassword  
    ;. Used to set the user name for the domain standard user account. Ignored in migration mode.  
    StdUserName=EnterDomainStandardUserName  
    ;. The password for the domain standard user account has to be strong and at least 8 characters  
    StdUserPlainTextPassword=EnterStandardUserPassword  
    ;Controls the Watson and automatic update settings  
    Settings=All or Updates or None  
    WebDomainName=www.abc.com  
    TrustedCertFileName=c:\cert\a.pfx  
    TrustedCertPassword=Enteryourpassword  
    EnableVPN=true  
    EnableRWA=true  
    IPv4DNSForwarder=<IPV4Address,IPV4Address,¦>  
    IPv6DNSForwarder=<IPV6Address,IPV6Address,¦>  
    VpnIPv4StartAddress=<IPV4Address>  
    VpnIPv4EndAddress=<IPV4Address>  
    VpnBaseIPv6Address=<IPV6Address>  
    VpnIPv6PrefixLength=<number>  
    ;All these section are optional.  
     [PostOSInstall]  
    ;Optional, The name of a script that runs after setupComplete.cmd but before the initial configuration begins.  
  
    IsHosted=true  
    StaticIPv4Address=<IPV4Address>  
    StaticIPv4Gateway=<IPV4Address>  
    StaticIPv4SubnetMask=<IPV4SubnetMask>   
    StaticIPv6Address=<IPV6Address>  
    StaticIPv6SubnetPrefixLength=<number>  
    StaticIPv6Gateway=<IPV6Address>  
    ClientBackupOn=true  
    FileHistoryOn=true  
    LaunchPadHiddenTasks=<Microsoft.LaunchPad.AdminDashboard,Microsoft.LaunchPad.Backup>  
  
    ```  
  
    > [!NOTE]
    >  Параметр для выбора другого языка во время начальной настройки не предусмотрен. При сбросе системы, язык операционной системы будет того, который изначально был установлен.  
  
    |Имя параметра|Описание параметра|  
    |--------------------|---------------------------|  
    |*AcceptEula*|Указывает, что пользователь принял условия лицензионного соглашения на использование программного обеспечения Майкрософт. Допустимые значения: True и False, но установка продолжается, только в том случае, если для этого параметра задано значение True.|  
    |*AcceptOEMEula*|(Необязательно) Указывает, что пользователь принял условия лицензии партнера. Допустимые значения: True и False. Это поле требуется только в том случае, если сервер был приобретен у партнера, который предоставил отдельное лицензионное соглашение.|  
    |*Название организации*|(Необязательно) Название компании. Название компании используется для связи сервера с конкретной компанией и настройки отчетов этой компании. Может содержать до 254 символов.|  
    |*Страны*|(Необязательно) Строка, представляющая требуемая Страна или регион. Пример: US для США.|  
    |*Имя сервера*|Имя сервера однозначно определяет сервер в сети. Имя сервера должно соответствовать следующим условиям:<br /><br /> -Может содержать до 15 символов.<br /><br /> -Может содержать буквы, цифры и дефисы (-).<br /><br /> -Не должно начинаться с дефиса.<br /><br /> -Не должно содержать пробелов.<br /><br /> -Не должно состоять из одних цифр.<br /><br /> Пример: ContosoServer.|  
    |*DNSName*|Внутренний домен группирует сервер и клиентские компьютеры для совместного использования общей базы данных имен пользователей, паролей и другой общей информации. Это имя отображается для пользователей при входе в систему на их компьютеры, но оно используется внутренней только и он не соответствует имени домена Интернета. Имя внутреннего домена должно удовлетворять тем же условиям, указанным для *имя_сервера*.<br /><br /> Пример: contoso.local.|  
    |*NetbiosName*|Имя NetBIOS используется для идентификации ресурсов, которые выполняются на сервере. Оно может содержать до 15 символов. Пример: Contoso.|  
    |*Язык*|(Необязательно) Задает язык интерфейса. Это может быть только один из установленных языков. Пример: en-us для английского языка в США.|  
    |*Языковой стандарт*|(Необязательно) Задает формат времени и денежных единиц с помощью *LocaleID* формат. Пример: en-us для времени и денежных единиц на английском языке и форматирования в соответствии с принятыми в США.|  
    |*Клавиатуры*|Клавиатуру можно в следующих форматах:<br /><br /> - **Макет клавиатуры: языка ввода.** Пример: 0409: 00000409, где 0409 перед **:** обозначает язык ввода, и **00000409** – раскладка клавиатуры. Список раскладок клавиатуры в разделе реестра можно найти **HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Keyboard Layouts**.<br /><br /> - **язык ввода: идентификатор IME.** Ниже приведен полный список идентификаторов IME.<br /><br /> -{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{8F96574E-C86C-4bd6-9666-3F7327D4CBE8} Амхарский метод ввода<br /><br /> -{81d4e9c9-1d3b-41bc-9e6c-4b40bf79e35e}{FA550B04-5AD7-411F-A5AC-CA038EC515D7} Майкрософт ПИН - инь – простая Быстрая (Китайская упрощенная)<br /><br /> -{531FDEBF-9B4C-4A43-A2AA-960E8FCDC732}{B2F9C502-1742-11D4-9790-0080C882687E} Китайская (традиционная) - новая фонетическая<br /><br /> -{531FDEBF-9B4C-4A43-A2AA-960E8FCDC732}{4BDF9F03-C7D3-11D4-B2AB-0080C882687E} Китайская (традиционная) - ChangJie<br /><br /> -{531FDEBF-9B4C-4A43-A2AA-960E8FCDC732}{6024B45F-5C54-11D4-B921-0080C882687E} Китайская (традиционная) – быстрая<br /><br /> -{E429b25a-e5d3-4d1f-9be3-0c608477e3a1}{d38eff65-aa46-4fd5-91a7-67845fb02f5b} Китайская традиционных<br /><br /> -{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{037B2C25-480C-4D7F-B027-D6CA6B69788A} Китайская традиционных DaYi<br /><br /> -{03B5835F-F03C-411B-9CE2-AA23E1171E36}{A76C93D9-5523-4E90-AAFA-4DB112F9AC76} Майкрософт IME (японская)<br /><br /> -{A028AE76-01B1-46C2-99C4-ACD9858AE02F}{B5FE1F02-D5F2-4445-9C03-C568F23C99A1} Майкрософт IME (корейская)<br /><br /> -{A1E2B86B-924A-4D43-80F6-8A820DF7190F}{B60AF051-257A-46BC-B9D3-84DAD819BAFB} старый хангыль IME (корейская)<br /><br /> -{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{409C8376-007B-4357-AE8E-26316EE3FB0D} Yi IME<br /><br /> -{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{3CAB88B7-CC3E-46A6-9765-B772AD7761FF} Tigrinya метод ввода|  
    |*Параметры*|Задает Выбор пользователя для обновления. Используйте одну из следующих значений:<br /><br /> **-Все** равняется использовать рекомендуемые параметры.<br /><br /> **-Обновления** означает устанавливать только важные обновления. только<br /><br /> **-Отсутствует** равно не проверять наличие обновлений.|  
    |*Имя пользователя*|-Имя новой учетной записи администратора, которая создается во время установки. Администратора и имена учетных записей обычного пользователя должны отвечать следующим критериям:<br /><br /> -Можно более 19 символов.<br /><br /> -Не должно содержать / \ [] & #124; < > + =;, ? *<br /><br /> -Не должны начинаться или заканчиваться точкой.<br /><br /> -Не должны содержать две точки подряд.<br /><br /> -Должна быть не так же, как имя сервера или внутреннее имя домена.<br /><br /> -Должна быть не совпадает с предопределенным именем пользователя, например администратора или гостя.|  
    |*PlainTextPassword*|Это пароль для новой учетной записи администратора, которая создается во время установки.<br /><br /> -Должна содержать по меньшей мере восемь символов.<br /><br /> -Должен содержать по крайней мере трех из следующих четырех категорий:<br /><br /> -Верхний регистр.<br /><br /> -Нижний регистр символов.<br /><br /> -Номера.<br /><br /> -Символы.|  
    |*StdUserName*|Имя новой учетной записи обычного пользователя, которая создается во время установки. В разделе *UserName* параметр требования.|  
    |*StdUserPlainTextPassword*|Пароль для учетной записи обычного пользователя, которая создается во время установки.|  
    |WebDomainName|(Необязательно) Настройка имени домена Интернета для сервера. Этот файл позволяет настраивать доменное имя аналогично тому методу, который использовался для ручной настройки в мастере настройки имени домена.|  
    |TrustedCertFileName|(Необязательно) Настройка доверенного сертификата для доменного имени. Это позволяет использовать. Сертификат PFX-ФАЙЛ, содержащий закрытый ключ.|  
    |TrustedCertPassword|(Необязательно) Пароль для импорта. PFX-ФАЙЛ.|  
    |EnableVPN|(Необязательно) Включение VPN по умолчанию.|  
    |VpnIPv4StartAddress|(Необязательно) Установка начального адреса VPN.|  
    |VpnIPv4EndAddress|(Необязательно) Задайте конечного адреса VPN.|  
    |VpnBaseIPv6Address|(Необязательно) Набор базового IPV6-адреса для VPN.|  
    |VpnIPv6PrefixLength|(Необязательно) Задание длины префикса IPv6-адреса VPN.|  
    |IsHosted|(Необязательно) Значение по умолчанию имеет значение false, если не указано. Задайте это значение, если установка выполняется в среде поставщика услуг размещения. Конфигурация маршрутизатора отключается.|  
    |StaticIPv4Address|(Необязательно) Укажите статический IP-адрес, если вы хотите настроить статический IP-адрес вместо динамического.|  
    |StaticIPv4Gateway|(Необязательно) Укажите адрес шлюза по умолчанию, если вы хотите настроить статический IP-адрес вместо динамического.|  
    |StaticIPv4SubnetMask|(Необязательно) Укажите маску подсети, если вы хотите настроить статический IP-адрес вместо динамического.|  
    |StaticIPv6Address|(Необязательно) Укажите IP-адрес по умолчанию, если вы хотите настроить статический IP-адрес вместо динамического.|  
    |StaticIPv6SubnetPrefixLength|(Необязательно) Укажите длину префикса подсети IPV6 по умолчанию, если вы хотите настроить статический IP-адрес вместо динамического.|  
    |StaticIPv6Gateway|(Необязательно) Укажите адрес шлюза по умолчанию, если вы хотите настроить статический IP-адрес вместо динамического.|  
    |ClientBackupOn|(Необязательно) Выключите клиента резервного копирования по умолчанию при подключении к серверу новых клиентов.|  
    |FileHistoryOn|(Необязательно) Отключите истории файлов резервного копирования по умолчанию новые клиенты под управлением Windows 8 Consumer Preview подключении к серверу.|  
    |EnableRWA|Активируется удаленный веб-доступ при установке Windows Server Essentials, но настройка маршрутизатора не выполняется. Поддерживается только при чистой установке продукта. Значение по умолчанию — false.|  
    |IPv4DNSForwarder|Установите сервер пересылки DNS-сервера IPv4.|  
    |IPv6DNSForwarder|Задайте IPv6 DNS-сервер пересылки.|  
    |LaunchPadHiddenTasks|-(Необязательно) можно скрыть записи резервного копирования или / и панель мониторинга администратора входа на панель запуска.<br /><br /> — Чтобы отключение панели администрирования: LaunchPadHiddenTasks=Microsoft.LaunchPad.AdminDashboard<br /><br /> -Порядок отключения архивации: LaunchPadHiddenTasks=Microsoft.LaunchPad.Backup<br /><br /> -Для отключения архивации и панели администрирования: LaunchPadHiddenTasks=Microsoft.LaunchPad.Backup,Microsoft.LaunchPad.AdminDashboard|  
  
3.  Сохраните файл. Убедитесь, что файл сохранен как cfg.ini, не cfg.ini.txt.  
  
    > [!NOTE]
    >  Можно сохранить файл на флэш-накопитель USB, который можно использовать на определенных этапах установки, или файл cfg.ini может быть расположен в корне любого жесткого диска на целевом сервере. Необходимо убедиться, что для файла выбрана кодировка ANSI или Юникод, кодировка UTF-8 не поддерживается.  
  
> [!IMPORTANT]
>  Раздел начальной настройки cfg.ini должен использоваться только конечным пользователем для персонализации сервера или партнером для тестирования работы пользователей сервера с помощью файла ответов автоматической установки. Этот раздел файла не предназначен для использования при создании образа.  
  
## <a name="see-also"></a>См. также:  

 [Начало работы с ADK Windows Server Essentials](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Начало работы с ADK Windows Server Essentials](../install/Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

