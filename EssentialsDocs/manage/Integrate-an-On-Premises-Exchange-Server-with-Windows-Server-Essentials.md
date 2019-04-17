---
title: "Интеграция локального сервера Exchange с Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b56a21e2-c9e3-4ba9-97d9-719ea6a0854b
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: c2020e08b94800a9750f095a2f772afb14ba5f0b
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="integrate-an-on-premises-exchange-server-with-windows-server-essentials"></a>Интеграция локального сервера Exchange с Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Это руководство содержит сведения и основные инструкции по настройке и интеграции локального сервера, на котором работает Exchange Server с сервером, на котором работает Windows Server Essentials.  
  
 В этом руководстве необходимо ознакомиться, прежде чем приступать к развертыванию локального сервера, на котором работает Exchange Server в сети Windows Server Essentials.  
  
> [!NOTE]
>  Exchange Server 2010 не поддерживает установку на компьютерах, работающих под управлением Windows Server 2012.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Прежде чем установить Exchange Server в сети Windows Server Essentials, убедитесь, что, необходимо выполнить действия, описанные в этом разделе.  
  
-   [Настройка сервера под управлением Windows Server Essentials](Integrate-an-On-Premises-Exchange-Server-with-Windows-Server-Essentials.md#BKMK_SetUpSBS8)  
  
-   [Подготовка второго сервера, на котором будет установлен Exchange Server](Integrate-an-On-Premises-Exchange-Server-with-Windows-Server-Essentials.md#BKMK_SecondServer)  
  
-   [Настройка имени домена Интернета](Integrate-an-On-Premises-Exchange-Server-with-Windows-Server-Essentials.md#BKMK_DomainNames)  
  
###  <a name="BKMK_SetUpSBS8"></a>Настройка сервера под управлением Windows Server Essentials  
 Сервер, на котором работает Windows Server Essentials уже должен быть настроен. Это будет контроллера домена для сервера, на котором работает Exchange Server. Сведения о настройке Windows Server Essentials см. в разделе [Установка Windows Server Essentials](../install/Install-Windows-Server-Essentials.md).  
  
###  <a name="BKMK_SecondServer"></a>Подготовка второго сервера, на котором будет установлен Exchange Server  
 Необходимо установить Exchange Server на втором сервере, который работает под управлением версии операционной системы Windows Server, официально поддерживающей Exchange Server 2010 или Exchange Server 2013. Затем нужно присоединить второй сервер к домену Windows Server Essentials.  
  
 Сведения о присоединении второго сервера к домену Windows Server Essentials см. в разделе присоединение второго сервера к сети в [подключайтесь](../use/Get-Connected-in-Windows-Server-Essentials.md).  
  
> [!NOTE]
>  Корпорация Майкрософт не поддерживает установку Exchange Server на сервере под управлением Windows Server Essentials.  
  
###  <a name="BKMK_DomainNames"></a>Настройка имени домена Интернета  
 Чтобы интегрировать локальный сервер, на котором работает Exchange Server с Windows Server Essentials, то должно быть зарегистрированное действительное имя домена Интернета для вашей организации (например, *contoso.com*). Вы также должны совместно с поставщиком имени домена создать записи ресурсов DNS, необходимые для сервера Exchange Server.  
  
 Например, если имя домена Интернета вашей организации является contoso.com и вы хотите использовать полное доменное имя (FQDN) из *mail.contoso.com* для ссылки вашего локального сервера, на котором работает Exchange Server, вместе с поставщиком имени домена создайте записи ресурсов DNS в следующей таблице.  
  
|Имя записи ресурса|Тип записи|Параметры записи|Описание|  
|--------------------------|-----------------|--------------------|-----------------|  
|почта|узел (A)|Адрес =*общедоступный IP-адрес, назначенный поставщиком услуг Интернета*|Сервер Exchange Server будет получать почту, адресованную на mail.contoso.com.<br /><br /> Можно использовать другое имя по своему выбору.|  
|MX|Почтовый обменник (MX)|Имя узла = @<br /><br /> Адрес = mail.contoso.com<br /><br /> Предпочтения = 0|Обеспечивает маршрутизацию сообщений электронной почты для email@contoso.comдефектные вашего локального сервера, на котором работает Exchange Server.|  
|SPF|текст (TXT)|V = spf1 mx ~ все|Запись ресурса, что помогает предотвратить электронные сообщения, отправленные с вашего сервера идентифицировать как спам.|  
|Autodiscover._tcp|службы (SRV)|Службы: _autodiscover<br /><br /> Протокол: _tcp<br /><br /> Приоритет: 0<br /><br /> Вес: 0<br /><br /> Порт: 443<br /><br /> Целевой узел: mail.contoso.com|Настраивает Microsoft Office Outlook и мобильные устройства на автоматическое обнаружение вашего локального сервера, на котором работает Exchange Server.<br /><br /> **Примечание:** можно также настроить запись ресурса узла (A) автообнаружения и указывала на общий IP-адрес вашего локального сервера, на котором работает Exchange Server. Тем не менее, если вы реализуете этот параметр, необходимо также указать альтернативное имя СУБЪЕКТА сертификат SSL для субъекта, поддерживающий mail.contoso.com и autodiscover.contoso.com имени домена.|  
  
> [!NOTE]
>  -   Замените вхождения *contoso.com* в этом примере именем домена Интернета, которое вы зарегистрировали.  
  
 Вы должны выбрать такое полное доменное имя для вашего локального сервера, на котором работает Exchange Server с полным доменным ИМЕНЕМ сервера, на котором работает Windows Server Essentials. Например, вы можете использовать *remote.contoso.com* полное доменное имя, которое компьютеры будут использовать для доступа к серверу под управлением Windows Server Essentials из Интернета. Можно использовать *mail.contoso.com* полное доменное имя, которое используется для перенаправления электронной почты на локальный сервер, на котором работает Exchange Server.  
  
## <a name="install-exchange-server"></a>Установка сервера Exchange Server  
 Функция интеграции Exchange Server на Windows Server Essentials поддерживает следующие версии Exchange Server:  
  
-   Exchange Server 2013  
  
-   Exchange Server 2010 с пакетом обновления 1 (SP1)  
  
 Прежде чем установить Exchange Server на втором сервере, необходимо добавить учетную запись текущего администратора в **администраторов предприятия** группы.  
  
#### <a name="to-add-the-current-administrator-account-to-the-enterprise-admins-group"></a>Чтобы добавить учетную запись текущего администратора в группу "Администраторы предприятия"  
  
1.  Войдите на Windows Server Essentials с правами администратора.  
  
2.  Запустите Windows PowerShell с правами администратора.  
  
3.  В командной строке Windows PowerShell введите **˜Enterprise Add-ADGroupMember администраторов $env: имя пользователя**, и нажмите клавишу ВВОД.  
  
#### <a name="to-install-exchange-server"></a>Установка сервера Exchange Server  
  
1.  Войдите на второй сервер с правами администратора.  
  
2.  Откройте браузер и перейдите к [Exchange помощника по развертыванию сервера](https://go.microsoft.com/fwlink/p/?LinkID=249163) веб-сайта.  
  
3.  Нажмите кнопку **локальной только**.  
  
4.  Выберите новый вариант установки для версии Exchange Server, которую вы собираетесь установить.  
  
    > [!NOTE]
    >  Если вы проводите миграцию с помощью установки Windows Small Business Server, следует выбрать подходящий вариант обновления, включающий процесс миграции.  
  
5.  На следующей странице, примите параметры по умолчанию и нажмите кнопку **Далее**.  
  
    > [!NOTE]
    >  Если вы планируете использовать общедоступные папки в новой установке Exchange Server, измените значение этого параметра на **Да**.  
  
6.  Следуйте пошаговым инструкциям в контрольном списке для развертывания Exchange Server.  
  
     Exchange Server помощника по развертыванию также позволяет:  
  
    -   Распечатайте копию контрольного списка.  
  
    -   Отправьте копию контрольного списка по электронной почте.  
  
    -   Загрузите контрольный список в виде PDF-файла.  
  
> [!NOTE]
>  -   Необходимо всегда выбирать установить средства управления на сервере, на котором работает Exchange Server. Средства управления требуются функции интеграции сервера Exchange Server в Windows Server Essentials.  
> -   Если необходимо настроить виртуальные каталоги, рекомендуется также задать **InternalUrl** свойство тот же URL-адрес как **ExternalUrl** свойство для каждого виртуального каталога. Дополнительные сведения см. в разделе [управление доступом виртуальными каталогами сервера клиентского](https://go.microsoft.com/fwlink/p/?LinkId=251058) online сайте справки Exchange Server 2010.  
> -   Если вы хотите получить доступ к Outlook Web Access (OWA) с сайта удаленного веб-доступа в Windows Server Essentials, необходимо задать свойство External URL для OWA.  
  
 При установке в случае чистой установки Exchange Server 2010 можно также использовать следующие сценарии для настройки сервера Exchange Server.  
  
#### <a name="to-use-scripts-to-set-up-exchange-server"></a>Чтобы использовать сценарии для настройки сервера Exchange Server  
  
1.  Откройте Блокнот и вставьте следующий сценарий в новый файл:  
  
     `Import-Module ServerManager`  
  
     `Add-WindowsFeature NET-Framework,RSAT-ADDS,Web-Server,Web-Basic-Auth,Web-Windows-Auth,Web-Metabase,Web-Net-Ext,Web-Lgcy-Mgmt-Console,WAS-Process-Model,RSAT-Web-Server,Web-ISAPI-Ext,Web-Digest-Auth,Web-Dyn-Compression,NET-HTTP-Activation,Web-Asp-Net,Web-Client-Auth,Web-Dir-Browsing,Web-Http-Errors,Web-Http-Logging,Web-Http-Redirect,Web-Http-Tracing,Web-ISAPI-Filter,Web-Request-Monitor,Web-Static-Content,Web-WMI,RPC-Over-HTTP-Proxy  �Restart`  
  
2.  Сохраните файл как **InstallDependencies.ps1**.  
  
3.  Скопируйте сертификат SSL для Exchange в расположении на сервере.  
  
4.  Откройте новый файл в Блокноте и скопируйте следующий текст в файл:  
  
     `param (`  
  
     `[string]`  
  
     `[Parameter(Mandatory=$true, HelpMessage = "The path to your Certificate file, must be a *.pfx format")]`  
  
     `$CertPath = "c:\certificates\ExchangeCertificate.pfx",`  
  
     `[Security.SecureString]`  
  
     `[Parameter(Mandatory=$true, HelpMessage = "The password of your cert")]`  
  
     `$CertPassword = $null,`  
  
     `[string]`  
  
     `[Parameter(Mandatory=$true, HelpMessage = "Domain Name, eg. contoso.com")]`  
  
     `$DomainName = "contoso.com",`  
  
     `[string]`  
  
     `[Parameter(Mandatory=$true, HelpMessage = "Server IP Address, eg. 192.168.0.1")]`  
  
     `$ServerIpAddress = "192.168.0.1",`  
  
     `[string]`  
  
     `[Parameter(Mandatory=$true, HelpMessage = "Internal Ip Range, eg. 192.168.0.0-192.168.0.255")]`  
  
     `$InternalIpRange = "192.168.0.0-192.168.0.255"`  
  
     `)`  
  
     `#Import Exchange Certificate, and Enable it for POP IIS IMAP SMTP services.`  
  
     `Import-ExchangeCertificate  �FileData ([Byte[]]$(Get-content -Path $CertPath  �Encoding byte  �ReadCount 0)) -Password:$CertPassword -Force | Enable-ExchangeCertificate -Services 'POP, IIS, IMAP, SMTP' -Force`  
  
     `#New AcceptedDomain and set it to default`  
  
     `New-AcceptedDomain  �Name "official name"  �DomainName $domainname`  
  
     `Set-AcceptedDomain  �Identity "official name"  �MakeDefault $true`  
  
     `#New EmailAddress Policy`  
  
     `$address = "%m@" + $DomainName`  
  
     `New-EmailAddressPolicy -Name "Windows Server Essentials Email Address Policy" -IncludedRecipients AllRecipients -EnabledPrimarySMTPAddressTemplate $address`  
  
     `#Set owa and ecp VirtualDirectory ExternalUrl`  
  
     `$hostname = "mail." + $DomainName`  
  
     `$owa = "https://" + $hostname + "/owa"`  
  
     `$ecp = "https://" + $hostname + "/ecp"`  
  
     `$activesync = "https://" + $hostname + "/Microsoft-Server-ActiveSync"`  
  
     `$oab = "https://" + $hostname + "/OAB"`  
  
     `$ews = "https://" + $hostname + "/EWS/Exchange.asmx"`  
  
     `Get-OwaVirtualDirectory | Set-OwaVirtualDirectory  �ExternalUrl $owa  �InternalUrl $owa`  
  
     `Get-EcpVirtualDirectory | Set-EcpVirtualDirectory  �ExternalUrl $ecp  �InternalUrl $ecp`  
  
     `Get-ActiveSyncVirtualDirectory | Set-ActiveSyncVirtualDirectory -ExternalUrl $activesync  �InternalUrl $activesync`  
  
     `Get-OABVirtualDirectory | Set-OABVirtualDirectory -ExternalUrl $oab -InternalUrl $oab -RequireSSL:$true`  
  
     `Get-WebServicesVirtualDirectory | Set-WebServicesVirtualDirectory -ExternalUrl $ews -InternalUrl $ews -BasicAuthentication:$True -Force`  
  
     `#Enable outlook Anywhere`  
  
     `Enable-OutlookAnywhere  �ClientAuthenticationMethod:Basic  �ExternalHostname:$hostname  �SSLOffloading:$false`  
  
     `#new receive/send connector`  
  
     `$machinename = get-content env:computername`  
  
     `$bindingIpaddress = $ServerIpAddress + ":25"`  
  
     `$RecevieConnectorName = $machinename + "\Default " + $machinename`  
  
     `Set-ReceiveConnector $RecevieConnectorName -RemoteIPRanges $InternalIpRange`  
  
     `New-ReceiveConnector -Name "WSE Internet Receive Connector" -Usage "Internet" -Bindings $bindingIpaddress -Fqdn $hostname -Enabled $true -Server $machinename -AuthMechanism Tls,BasicAuth,BasicAuthRequireTLS,Integrated`  
  
     `New-SendConnector -Name "WSE Internet SendConnector" -Usage "Internet" -AddressSpaces 'SMTP:*;1' -IsScopedConnector $false -DNSRoutingEnabled $true -UseExternalDNSServersEnabled $true -SourceTransportServers $machinename`  
  
5.  Задайте параметры в начале сценария в соответствии со своей сетевой средой.  
  
6.  Сохраните файл как **ConfigureExchange.ps1**.  
  
7.  Запустите Windows PowerShell с правами администратора.  
  
8.  В командной строке Windows PowerShell введите **Set-ExecutionPolicy RemoteSigned**, и нажмите клавишу ВВОД.  
  
9. Запустите сценарий **InstallDependencies.ps1**.  
  
10. Перезапустите сервер, а затем запустите Windows PowerShell от имени администратора.  
  
11. В командной строке Windows PowerShell выполните следующий сценарий:  
  
     `E:\setup.com /mode:install /roles:mb,ht,ca /OrganizationName:"First Organization"`  
  
    > [!NOTE]
    >  Убедитесь, что введите правильный путь к программе установки Exchange Server.  
  
12. По завершении установки Exchange Server откройте командную консоль Exchange от имени администратора.  
  
13. В командной строке консоли Exchange введите **Set-ExecutionPolicy RemoteSigned**, и нажмите клавишу ВВОД.  
  
14. Запустите сценарий **ConfigureExchange.ps1**.  
  
15. Перезапустите сервер.  
  
> [!NOTE]
>  Если вы решили использовать общедоверенный сертификат SSL вместо самостоятельно выданного сертификата, может следуйте инструкциям в руководстве по установке, можно создать запрос сертификата и отправить его в центр сертификации по своему выбору. Можно также использовать командлетом Exchange PowerShell для создания запроса сертификата. Ниже приведен пример.  
>   
>  `New-ExchangeCertificate -GenerateRequest -SubjectName "C=US, S=Washington, L=Redmond, O=contoso, OU=contoso, CN=mail.contoso.com" -DomainName mail.contoso.com -PrivateKeyExportable $true | Set-Content -path "c:\Docs\MyCertRequest.req"`  
>   
>  Настройте параметры сценария в соответствии с вашей сетевой средой.  
  
## <a name="post-installation-tasks"></a>Задачи после Post-installation  
 В этом разделе описаны задачи по настройке сервера, возможно, придется выполнить после установки. Здесь приведены сведения, касающиеся настройки локального сервера, на котором работает Exchange Server в сети Windows Server Essentials.  
  
### <a name="add-the-public-email-domain-and-configure-the-email-address-policies"></a>Добавление общедоступного почтового домена и Настройка политик адресов электронной почты  
  
> [!NOTE]
>  Это обязательная задача при выполнении чистой установки. Этот шаг можно пропустите, если вы проводите миграцию с Windows Small Business Server.  
  
 Необходимо указать домен вашей электронной почты в качестве обслуживаемого домена по умолчанию и затем настроить политику адресов электронной почты.  
  
##### <a name="to-add-your-email-domain-as-the-default-accepted-domain"></a>Добавление домена электронной почты по умолчанию обслуживаемого домена  
  
1.  Следуйте инструкциям статьи о сервере Exchange Server [созданию обслуживаемого домена](https://go.microsoft.com/fwlink/p/?LinkId=249174) для добавления обслуживаемого домена.  
  
2.  Войдите на второй сервер с правами администратора, откройте консоль управления Exchange и перейдите к **транспортный** вкладке **Конфигурация организации**.  
  
3.  В рабочей области консоли управления Exchange правой кнопкой мыши щелкните новый обслуживаемый домен и нажмите кнопку **по умолчанию**.  
  
4.  Следуйте инструкциям статьи о сервере Exchange Server [Создание политику адресов электронной почты](https://go.microsoft.com/fwlink/p/?LinkId=249179) для создания новой политики адресов электронной почты. Вы можете принять все значения по умолчанию, кроме адреса электронной почты. Адрес электронной почты укажите свой общедоступный почтовый домен.  
  
### <a name="create-smtp-send-and-receive-connectors"></a>Создание отправки SMTP соединителей и получения  
  
> [!NOTE]
>  Это обязательная задача.  
  
 Необходимо настроить соединитель отправки SMTP и соединитель получения SMTP для передачи исходящих и входящих сообщений электронной почты.  
  
 Чтобы создать соединитель отправки SMTP, выполните инструкции из статьи о сервере Exchange [Создание соединителя отправки SMTP](https://technet.microsoft.com/library/aa997285.aspx).  
  
 Чтобы создать соединитель получения SMTP, выполните инструкции из статьи о сервере Exchange [создать соединитель получения SMTP](https://technet.microsoft.com/library/bb125159.aspx).  
  
 В качестве альтернативы можно воспользоваться сценарием, ранее в этом документе, для создания отправки и получения соединители при помощи командлетов Exchange PowerShell.  
  
### <a name="configure-the-network-router"></a>Настройка сетевого маршрутизатора  
  
> [!NOTE]
>  Это обязательная задача при выполнении чистой установки. Если вы проводите миграцию с Windows Small Business Server, см. раздел [миграция данных сервера на Windows Server Essentials](../migrate/Migrate-Server-Data-to-Windows-Server-Essentials.md) инструкции по настройке сети.  
  
 Как минимум необходимо настроить следующие параметры портов на маршрутизаторе:  
  
|Порт маршрутизатора|Конечный IP|Порт назначения|Примечание|  
|-----------------|--------------------|----------------------|----------|  
|25 (SMTP)|Внутренний IP-адрес локального сервера, на котором работает Exchange Server.|25||  
|80 (HTTP)|Внутренний IP-адрес сервера, на котором работает Windows Server Essentials|80||  
|443 (HTTPS)|Внутренний IP-адрес сервера, на котором работает Windows Server Essentials|443||  
  
 Если требуется поддержка POP3 или IMAP, протоколы сети обмена сообщениями, необходимо также настроить перенаправление портов для этих протоколов. For-related сведения см. в разделе **серверах клиентского доступа** раздела [Справочник по сетевым портам Exchange](https://go.microsoft.com/fwlink/p/?LinkId=250773) в технической библиотеке Exchange Server.  
  
> [!NOTE]
>  -   Рекомендуется настроить статические IP-адреса для сервера, на котором работает Windows Server Essentials и для второго сервера под управлением Exchange Server. Инструкции по настройке статического IP-адреса на компьютере под управлением Windows Server 2003 или Windows Server 2008 R2 см. в разделе [настроить статический IP-адрес](https://technet.microsoft.com/library/cc754203\(v=ws.10\).aspx) в технической библиотеке Windows Server  
>   
>      **Примечание:** параметр DNS-сервера должен всегда указывать на IP-адрес сервера, на котором работает Windows Server Essentials.  
> -   Убедитесь, что IP-адреса сервера, на котором работает Windows Server Essentials и сервера, на котором работает Exchange Server либо зарезервированы, либо находиться вне диапазона адресов DHCP IP на маршрутизаторе.  
> -   Конфигурация маршрутизатора, приведенная в этом разделе предполагается, что имеется только один общий IP-адрес с вашего поставщика услуг Интернета (ISP). Если у вас есть несколько общих IP-адресов, можно назначить другой IP-адрес сервера, на котором работает Windows Server Essentials и сервера, на котором работает Exchange Server и затем создать перенаправление портов на основе общих IP-адресов.  
  
### <a name="enable-on-premises-exchange-server-integration-on-windows-server-essentials"></a>Включить интеграцию локального сервера Exchange Server на Windows Server Essentials  
  
> [!NOTE]
>  Если вы переносите из установки Windows Small Business Server, рекомендуется пропустить этот шаг и выполнить его после удаления предыдущей установки Exchange Server на исходном сервере.  
  
 После установки и настройки сервера, на котором работает Exchange Server, необходимо включить интеграцию локального сервера Exchange Server, на сервере под управлением Windows Server Essentials.  
  
##### <a name="to-enable-on-premises-exchange-server-integration-from-the-dashboard"></a>Чтобы включить интеграцию локального сервера Exchange Server с помощью панели мониторинга  
  
1.  Войдите сервер под управлением Windows Server Essentials с правами администратора и откройте панель мониторинга.  
  
2.  На **Главная** щелкните **подключение к службе электронной почты**, а затем нажмите кнопку **интеграции сервера Exchange**.  
  
3.  В области сведений щелкните **настройки интеграции сервера Exchange**.  
  
4.  Следуйте инструкциям мастера.  
  
### <a name="configure-a-reverse-proxy"></a>Настройка обратного прокси-сервера  
  
> [!NOTE]
>  Это обязательная задача, если у вас есть только одно подключение от вашего поставщика услуг Интернета.  
  
 Windows Server Essentials и Exchange Server поддерживают несколько сценариев удаленного доступа для пользователей сети. Например включив Повсеместный доступ на сервере под управлением Windows Server Essentials, можно удаленно обращаться к сайту удаленного веб-доступа или использовать виртуальную частную сеть (VPN) для удаленного подключения к сети Windows Server Essentials. Для удаленного доступа к сообщениям электронной почты, необходимо использовать мобильный Outlook, Outlook Web Access (OWA) или ActiveSync.  
  
 Если Windows Server Essentials и серверу Exchange Server подключены к тому же маршрутизатору и существует только одно входящее Интернет-подключение из ваш поставщик услуг Интернета для маршрутизатора, необходимо использовать решение обратного прокси-сервера для перенаправления различных типов запросов удаленного доступа из Интернета, на основе имен узлов назначения. Мы рекомендуем использовать Microsoft поддерживается расширения IIS Маршрутизация запросов приложений () в качестве решения обратного прокси-сервера. Дополнительные сведения о маршрутизации запросов приложений IIS, посетите [веб-сайт маршрутизации запросов приложений](https://go.microsoft.com/fwlink/p/?LinkId=249181).  
  
##### <a name="to-install-and-configure-application-request-routing"></a>Установка и настройка модуля маршрутизации запросов приложений  
  
1.  Войдите на Windows Server Essentials с правами администратора.  
  
2.  Откройте браузер и перейдите к [веб-сайт маршрутизации запросов приложений](https://go.microsoft.com/fwlink/p/?LinkId=249181).  
  
3.  На веб-сайт маршрутизации запросов Приложений нажмите кнопку **установить**, а затем следуйте инструкциям по установке ARR.  
  
    > [!NOTE]
    >  Во время установки необходимо выбрать модуль переопределения URL-адрес.  
    >   
    >  Может возникнуть ошибка в конце установки, не удалось установить КБ 2589179 для ARR 2.5. Эту ошибку можно игнорировать.  
  
4.  По завершении установки модуля маршрутизации запросов Приложений перезапустите **шлюза удаленных рабочих столов** службы, если он не работает.  
  
    > [!NOTE]
    >  После установки модуля маршрутизации запросов Приложений, **шлюза удаленных рабочих столов** служба может быть остановлена. Чтобы вручную перезапустить службу, откройте **службы** средство администрирования, а затем перезапустить **шлюза удаленных рабочих столов** службы.  
  
5.  [Загрузите исправление KB 2732764 для модуля маршрутизации запросов Приложений версии 2.5](https://go.microsoft.com/fwlink/?LinkID=258302), а затем установите обновление на сервере под управлением Windows Server Essentials.  
  
6.  Скопируйте файл сертификата SSL для Exchange Server на сервер под управлением Windows Server Essentials. Файл сертификата должен содержать закрытый ключ, и должен быть в формате PFX.  
  
    > [!NOTE]
    >  Если вы используете самостоятельно выданный сертификат, следуя инструкциям из статьи о сервере Exchange Server [Экспорт сертификата Exchange](https://technet.microsoft.com/library/dd351274.aspx) для экспорта сертификата.  
  
7.  В зависимости от того, какая версия Windows Server Essentials выполняется выполните одно из следующих действий.  
  
    -   В Windows Server Essentials: Откройте командное окно от имени администратора, а затем откройте каталог %ProgramFiles%\Windows Server\Bin  
  
    -   В Windows Server Essentials: Откройте командное окно от имени администратора и затем откройте каталог %Windir%\System32\Essentials.  
  
8.  В зависимости от варианта установки выполните один из следующих шагов для настройки маршрутизации запросов Приложений:  
  
    -   При выполнении чистой установки выполните следующую команду:  
  
         ** ARRConfig config cert ** *путь к файлу сертификата* ** имена узлов ** *имена узлов для Exchange Server* ****  
  
        > [!NOTE]
        >  Например, для ** ARRConfig config cert ***c:\temp\certificate.pfx*** hostnames *** mail.contoso.com ***  
        >   
        >  Замените *mail.contoso.com* на имя вашего домена, который защищен с помощью сертификата.  
  
    -   В случае миграции с Windows Small Business Server, выполните следующую команду:  
  
         ** ARRConfig config cert ** *путь к файлу сертификата* ** имена узлов ** *имена узлов для Exchange Server* ** targetserver ** *имя сервера Exchange Server* ****  
  
         Например, для ** ARRConfig config cert ***c:\temp\certificate.pfx*** hostnames ***mail.contoso.com*** targetserver *** ExchangeSvr ***  
  
         Замените *mail.contoso.com* на имя вашего домена. Замените *ExchangeSvr* с именем сервера, на котором работает Exchange Server.  
  
9. При появлении запроса введите пароль для сертификата.  
  
> [!NOTE]
>  -   Имена узлов, которые вы предоставляете должны содержаться в сертификате SSL, приобретенном для Exchange Server.  
> -   Если у вас несколько имен узлов, используйте запятую (,), чтобы разделить их.  
  
 Чтобы убедиться, что конфигурация подходит, пытаются получить доступ к веб-сайт OWA для вашего сервера, на котором работает Exchange Server (https://mail. *имя_домена*.com/owa) с компьютера, который не является членом домена. Для устранения неполадок подключения, можно также использовать online [анализатор удаленных подключений Майкрософт](https://go.microsoft.com/fwlink/p/?LinkId=249455) средство.  
  
### <a name="configure-split-dns-for-exchange-server"></a>Настройка разделения DNS для сервера Exchange Server  
  
> [!NOTE]
>  Это рекомендуемая задача.  
  
 Разделение DNS позволяет настроить разные IP-адреса в DNS для одного имени узла, в зависимости от источника DNS-запрос. Если клиентский компьютер находится в интрасети, DNS-запрос разрешается в IP-адрес интрасети. Если клиентский компьютер находится в Интернете, DNS-запрос разрешается в IP-адрес. Этот процесс прозрачен для пользователей.  
  
 Рекомендуется настроить разделение DNS таким образом, который позволяет пользователям всегда использовать то же имя узла для доступа к Exchange Server, службам, независимо от их расположения.  
  
##### <a name="to-configure-split-dns-for-exchange-server"></a>Настройка разделения DNS для сервера Exchange Server  
  
1.  Войдите в Windows Server Essentials с правами администратора и откройте диспетчер DNS.  
  
2.  В дереве консоли диспетчера DNS щелкните правой кнопкой мыши сервер и нажмите кнопку **новая зона**. **Мастера создания новой зоны** отображается.  
  
3.  На **тип зоны** страницу мастера, примите параметр по умолчанию и нажмите кнопку **Далее**.  
  
4.  На **область репликации зоны в Active Directory** примите параметр по умолчанию и нажмите кнопку **Далее**.  
  
5.  На **зона прямого или обратного просмотра** примите или выберите **зону прямого просмотра**, а затем нажмите кнопку **Далее**.  
  
6.  На **имя зоны** введите полное доменное имя сервера, на котором работает Exchange Server (например, для *mail.contoso.com*), а затем нажмите кнопку **Далее**.  
  
7.  На **динамическое обновление**, не изменяя заданное по умолчанию значение, нажмите кнопку **Далее**, а затем нажмите кнопку **Готово**.  
  
8.  В дереве консоли диспетчера DNS щелкните правой кнопкой мыши новую зону прямого просмотра, а затем нажмите кнопку **новый узел (A или AAAA)**.  
  
9. На **новый узел** оставьте **имя** пустым, введите IP-адрес сервера, на котором работает Exchange Server, интрасети и нажмите кнопку **добавить узел **.  
  
    > [!NOTE]
    >  Если оставить **имя** пустым, сервер будет использовать имя родительского домена по умолчанию.  
  
10. На **новый узел** щелкните **сделать **.  
  
> [!NOTE]
>  Если вы используете ActiveSync, но не можете синхронизировать электронную почту для некоторых учетных записей, определите, являются ли эти учетные записи членами одной или нескольких защищенных групп, таких как Администраторы домена. For-related сведения, которые могут помочь устранить эту проблему, см. [Exchange ActiveSync вернула ошибку HTTP 500](https://technet.microsoft.com/library/dd439375\(EXCHG.80\).aspx).  
  
## <a name="related-topics"></a>Связанные разделы  
 Дополнительные сведения об интеграции локального сервера Exchange см. в следующих разделах.  
  
### <a name="what-happens-if-i-disable-exchange-integration"></a>Что произойдет, если отключить интеграцию Exchange?  
 Отключение интеграции с локальным сервером Exchange, больше не можно использовать панель мониторинга Windows Server Essentials для просмотра, создания и управления почтовыми ящиками Exchange Server.  
  
### <a name="what-do-i-need-to-know-about-email-accounts"></a>Что нужно знать об учетных записях электронной почты?  
 Хостинг электронной почты настраивается на сервере. Учетные записи электронной почты отдельных решения от провайдера хостинга электронной почты, например Microsoft Office 365, можно обеспечить пользователей сети. При запуске добавления мастер создания учетной записи пользователя в Windows Server Essentials, чтобы создать учетную запись пользователя, мастер пытается добавить учетную запись пользователя с помощью доступных размещенного электронной почты. В то же время мастер назначает пользователю имя (псевдоним) электронной почты и задает максимальный размер почтового ящика (квоту). Максимальный размер почтового ящика зависит от выбранного поставщика электронной почты. После добавления учетной записи пользователя, могут продолжать управлять данные псевдоним и квота почтового ящика на странице свойств для пользователя. Полное управление учетными записями пользователей и службой хостинга электронной почты используйте консоль управления поставщика размещенного. В зависимости от вашего поставщика вы доступ к консоли управления из веб-портал или через закладку в панели мониторинга сервера.  
  
 Псевдоним, который можно предоставить при запуске добавления мастер создания учетной записи пользователя отправляется провайдеру как предлагаемое имя для псевдонима пользователя. Например, если псевдоним пользователя *FrankM*, может быть адрес электронной почты пользователя s *FrankM@Contoso.com*.  
  
 Кроме того пароль, который задан для пользователя в учетную запись пользователя мастер добавления будет исходного пароля пользователя в хостинге электронной почты.  
  
 Наконец Если удалить пользователя с помощью мастера удаления мастер создания учетной записи пользователя на сервере, мастер также отправляет запрос провайдеру также удалить пользователя из системы. Провайдер может удалить учетную запись пользователя s и электронной почты, который связан с учетной записью.  
  
 Дополнительные сведения о настройке клиентского программного обеспечения требуется электронной почты и как получить доступ к учетной записи электронной почты см. в справочной документации, предоставляемой провайдером хостинга электронной почты.  
  
### <a name="what-is-a-mailbox-quota"></a>Что такое Квота электронной почты?  
 Объем дискового пространства, выделенного для s данных почтового ящика Exchange пользователя сети называется квота почтового ящика.  
  
 При запуске **настройки интеграции сервера Exchange** задачи на панели мониторинга мастер добавляет страницу мастера добавления пользователей учетной записи, вы можете выбрать, нужно ли вводить квоты почтовых ящиков и устанавливать размер квот. По умолчанию **вводить квоты почтовых ящиков** установлен (включен) и почтовых ящиков пользователей предоставляется 2 ГБ дискового пространства. Администраторы Exchange могут настраивать размер квоты почтовых ящиков в соответствии с потребностями бизнеса.  
  
## <a name="see-also"></a>См. также:  
  
-   [Требования к системе для Windows Server Essentials](../get-started/system-requirements.md)  
  
-   [Управление интеграцией со службой электронной почты](Manage-Email-Service-Integration-in-Windows-Server-Essentials.md)  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)
