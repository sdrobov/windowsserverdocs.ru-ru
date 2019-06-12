---
title: Размещенный сервер Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fda5628c-ad23-49de-8d94-430a4f253802
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: dded002df4ed0bbd70c549a8841b769a77f2fd6a
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433543"
---
# <a name="hosted-windows-server-essentials"></a>Размещенный сервер Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Данный документ содержит информацию, предназначенную для поставщиков услуг размещения, которые намереваются развертывать Windows Server Essentials в своих лабораториях и предлагать своим клиентам Windows Server Essentials как услуга.  
  
## <a name="what-is-windows-server-essentials"></a>Что такое Windows Server Essentials?  
 Windows Server Essentials — это распределенное развертывание решения для малого бизнеса, где используется из лучших, 64-разрядной технологии позволяет получить серверную среду, хорошо подходит для подавляющего большинства предприятий малого бизнеса. Следующие технологии включены в Windows Server Essentials.  
  
 **Операционная система сервера:** Основой для Windows Server Essentials служат технологии Windows Server 2012. Дополнительные сведения см. на [веб-сайте Windows Server 2012](https://www.microsoft.com/en-us/server-cloud/products/windows-server-2012-r2/default.aspx#fbid=ZH0GD_CRAWh).  
  
 **Защита данных:** Windows Server Essentials реализованы некоторые новые функции, доступные в Windows Server 2012, обеспечивающие повышенный уровень данных защиты. [Новая функция управления дисковыми пространствами](https://technet.microsoft.com/library/hh831739.aspx) позволяет объединять физический объем памяти разрозненных жестких дисков, динамически добавлять жесткие диски и создавать тома данных с заданными уровнями устойчивости. Windows Server Essentials можно выполнять полную архивацию системы и восстанавливает исходное состояние системы сервера, сам, а также клиентских компьютеров, подключенных к сети? теперь с поддержкой томов, размер которых превышает 2 ТБ. Появилась новая для Windows Server 2012 служба [Windows Azure Online Backup](https://technet.microsoft.com/library/hh831419.aspx) , которую можно использовать для защиты файлов и папок в хранилище на основе облака, которым управляет корпорация Майкрософт. Windows Server Essentials также централизованно управляет и настраивает функцию ведения журнала файлов клиентов Windows 8.1, помогая пользователям восстанавливать из случайно удаленные или перезаписанные файлы без помощи администратора.  
  
 **Повсеместный доступ:** Удаленный веб-доступ обеспечивает упрощенное взаимодействие с браузером с поддержкой устройств сенсорного ввода для работы с приложениями и данными практически отовсюду, где имеется подключение к Интернету, и практически с любого устройства. Windows Server Essentials также предоставляет обновленное приложение Windows Phone и новое приложение для Windows 8.1 клиентских компьютеров, позволяя пользователям интуитивно подключиться, поиск по и доступ к файлам и папкам на сервере. Файлы также автоматически кэшируются для автономного доступа и синхронизируются при появлении подключения к серверу. Windows Server Essentials позволяет устанавливать виртуальную частную сеть (VPN) в безболезненным, управляемый мастером процесс из нескольких щелчков и упрощает управление доступом к VPN для пользователей. Клиентские компьютеры могут использовать подключение к VPN для удаленного входа в среду Windows SBS, находясь вне офиса.  
  
 **Гибкость рабочей нагрузки:** Windows Server Essentials разработан, чтобы дать пользователям возможность выбирать, какие приложения и службы запускать локально, а какие в облаке. В предыдущих версиях Windows Small Business Server Standard в качестве компонента был включен сервер Exchange Server, который был связан с дополнительными расходами и сложностями для клиентов, желавших использовать службы обмена сообщениями и совместной работы на основе облака. С Windows Server Essentials клиенты могут воспользоваться однотипных интегрированного управления ли они решили запустить его в локальной копии Exchange Server, подписаться на размещенную службу Exchange или Подпишитесь на Microsoft Office 365.  
  
 **Наблюдение за работоспособностью:** Windows Server Essentials контролирует собственное состояние работоспособности и состояние клиентских компьютеров под управлением Windows 8.1, Windows 7 и Mac OS X версии 10.5 и более поздних версий. Состояние работоспособности отображает различные проблемы, связанные с архивацией данных компьютера, хранилищем сервера, недостатком места на диске и пр.  
  
 **Расширяемость:** Windows Server Essentials создает модель расширяемости Windows SBS 2011 Essentials, которая позволяет прочим поставщикам программного обеспечения добавить возможности и функции в основной продукт и предоставляет новый набор API веб-служб. Кроме того, обеспечена совместимость с существующим [пакетом средств разработки программного обеспечения](https://msdn.microsoft.com/library/gg513958.aspx) (SDK) и [надстройками](https://pinpoint.microsoft.com/applications/search?fpt=300105&q=small+business+server+essentials) , предназначенными для Windows SBS 2011 Essentials.  
  
## <a name="how-can-i-customize-an-image"></a>Пользовательская настройка образа  
 Ссылаться на [Windows Server Essentials](https://go.microsoft.com/fwlink/p/?LinkID=249124), который является стандартный процесс выполнения sysprep Windows Server с дополнительными этапами настройки Windows Server Essentials. Для завершения настройки следуйте инструкциям, приведенным в разделах [Создание простого пользовательского образа](https://technet.microsoft.com/library/jj200117) и [Настройка образа](https://technet.microsoft.com/library/jj200161), а затем для выполнения записи окончательного образа следуйте инструкциям в разделе [Подготовка образа к развертыванию](https://technet.microsoft.com/library/jj200142) .  
  
 Обращайте внимание на следующие аспекты:  
  
1. Необходимо пропускать начальную настройку (IC); для этого нужно создать файл SkipIC.txt в корне любого диска. После установки сервера и перед IC нажмите комбинацию клавиш Shift+F10 для вызова окна cmd и создайте файл a SkipIC.txt на диске C:/. После настройки не забудьте удалить файл SkipIC.txt.  
  
2. Если необходимо выполнить развертывание Windows Server Essentials на диске объемом менее 90 ГБ, следует добавить раздел реестра, перед sysprep:  
  
   ```  
   %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\windows server\setup" /v HWRequirementChecks /t REG_DWORD /d 0 /f  
   ```  
  
   После sysprep можно воспользоваться образом диска, подготовленным командой sysprep, или запечатать его обратно в Install.wim для нового развертывания.  
  
   Если применяется диспетчер виртуальных машин, можно создать шаблон, используя запущенный экземпляр. При создании шаблона будет выполнена команда sysprep по отношению к запущенному экземпляру, и машина будет выключена. После сохранения в библиотеку можно загружать экземпляр в зависимости от конкретного случая.  
  
##  <a name="BKMK_automatedeployment"></a> Как автоматизировать развертывание?  
 После получения настроенного образа пользователь может выполнить развертывание с помощью своего собственного образа. Для выполнения полуавтоматической установки необходимо предоставить / развернуть файл unattend.xml для установки WinPE. Чтобы сделать полностью автоматической установки, необходимо также предоставить файл cfg.ini для начальной настройки Windows Server Essentials.  
  
1. Выполнение только автоматической установки WinPE. Будет выполнена автоматическая установка только WinPE, которая будет остановлена перед начальной настройкой, чтобы пользователи смогли ввести информацию об организации, домене и администраторе после RDP в сеанс сервера. Выполните указанные ниже действия.  
  
   1.  Предоставьте файл Windows unattend.xml. Выполните [Windows 8.1 ADK](https://go.microsoft.com/fwlink/?LinkId=248694) для создания файла и введите всю необходимую информацию, включая имя сервера, ключи продуктов и пароль администратора. В разделе "Microsoft-Windows-Setup" файла unattend.xml укажите приведенные ниже данные.  
  
       ```  
       <InstallFrom>  
                <MetaData>  
                    <Key>IMAGE/WINDOWS/EDITIONID</Key>  
                    <Value>ServerSolution</Value>  
                </MetaData>  
                <MetaData>  
                    <Key>IMAGE/WINDOWS/INSTALLATIONTYPE</Key>  
                    <Value>Server</Value>  
                </MetaData>  
          </InstallFrom>  
       ```  
  
   2.  Порт RDP 3389 должен быть открыт на общедоступный IP-адрес, таким образом, клиент может использовать администратора и пароль, указанный в файле unattend.xml для протокола удаленного рабочего СТОЛА на сервер, чтобы завершить первоначальную настройку.  
  
   > [!NOTE]
   >  Если не менять пароль, задаваемый по умолчанию, установка сервера будет приостановлена и появится окно с предложением ввести пароль.**Примечание** Конечные пользователи должны использовать существующую по умолчанию учетную запись администратора для входа на сервер и выполнения начальной настройки.  
  
   Если используется диспетчер виртуальных машин, можно задать пароль администратора в консоли при создании нового экземпляра из шаблона.  
  
2. Выполнение полностью автоматической установки и автоматической начальной настройки. Выполните указанные ниже действия.  
  
   1.  Если развертывание начинается с установки WinPE, создайте файл unattend.xml, как описано выше.  
  
   2.  См. раздел Windows Server Essentials ADK, озаглавленном [Создание файла Cfg.ini](https://technet.microsoft.com/library/jj200150), для создания файла cfg.ini.  
  
   3.  Предоставьте информацию в [InitialConfiguration].  
  
       ```  
       WebDomainName=yourdomainname  
       TrustedCertFileName=c:\cert\a.pfx  
       TrustedCertPassword=Enteryourpassword  
       EnableVPN=true  
       EnableRWA=true  
       ; Provide all information so that after setup is complete, your customer can use your domain name to visit the server directly with the admin/user information you provide in the [InitialConfiguration] section.  
  
       VpnIPv4StartAddress=<IPV4Address>  
       VpnIPv4EndAddress=<IPV4Address>  
       VpnBaseIPv6Address=<IPV6Address>  
       VpnIPv6PrefixLength=<number>  
       ; Provide this information. IPv4StartAddress and IPv4Endaddress are required so that your VPN client can acquire valid IP through this range.  
  
       IPv4DNSForwarder=<IPV4Address,IPV4Address,Â¦>  
       IPv6DNSForwarder=<IPV6Address,IPV6Address,Â¦>  
       ; Provide this information as needed according to your network environment settings.  
       ```  
  
   4.  Предоставьте информацию в [PostOSInstall].  
  
       ```  
       IsHosted=true   
       ; Must have, this will prevent Initial Configure webpage available for other computers under same subnet.  
  
       StaticIPv4Address=<IPV4Address>  
       StaticIPv4Gateway=<IPV4Address>  
       StaticIPv6Address=<IPV6Address>  
       StaticIPv6SubnetPrefixLength=<number>  
       StaticIPv6Gateway=<IPV6Address>  
       ; All these are optional if you have DHCP Server Service on the subnet, otherwise provide static IP here.  
       ```  
  
   5.  Если указать параметр WebDomainName, убедитесь, что запись DNS также обновляется для указания s общедоступный IP-адрес сервера.  
  
   6.  Если параметр WebDomainName не задается, необходимо открыть порт 3389, чтобы клиенты могли использовать RDP для подключения к серверу и завершения настройки VPN.  
  
> [!NOTE]
>  Убедитесь, что часовой пояс сервера узла виртуальной Машины и виртуальной Машины Windows Server Essentials не отличаются. В противном случае могут возникать различные ошибки (может произойти сбой начальной настройки при выполнении задач, связанных с сертификатом; сертификат может не работать в течение нескольких часов после установки; информация об устройстве может не обновляться надлежащим образом и пр.).  
  
 После развертывания проверьте ключ регистрации в папке HKLM\software\microsoft\windows server\setup на предмет завершения начальной настройки. Если параметр SetupStage == ICDone && ICStatus == 1, это означает, что начальная установка успешно завершена.  
  
## <a name="what-is-the-supported-network-topology"></a>Топология поддерживаемой сети  
 Чтобы использовать Windows Server Essentials с перемещаемого клиентского компьютера, необходимо активировать VPN. Рекомендуется для подключения SSTP VPN использовать порт 443. Если для удаленного веб-доступа или приложений веб-служб требуется функция сервера мультимедиа, необходимо также подключить порт 80.  
  
 Подключение к VPN можно выполнить во время автоматического развертывания с помощью сценария Windows PowerShell, либо же его можно установить с помощью мастера после начальной настройки.  
  

- Инструкции по подключению VPN во время автоматической настройки приведены в разделе [How do I automate the deployment?](Hosted-Windows-Server-Essentials.md#BKMK_automatedeployment) данного документа.  

- Инструкции по подключению VPN во время автоматической настройки приведены в разделе [How do I automate the deployment?](../install/Hosted-Windows-Server-Essentials.md#BKMK_automatedeployment) данного документа.  

  
- Чтобы подключить VPN с помощью сценария Windows PowerShell, выполните следующий командлет с правами администратора и предоставьте всю необходимую информацию.  
  
  ```  
  ##  
  ## To configure external domain and SSL certificate (if not yet done in unattended Initial Configuration).  
  ##  
  
  $myExternalDomainName = 'remote.contoso.com';   ## corresponds to A or AAAA DNS record(s) that can be resolved on Internet and routed to the server  
  $mySslCertificateFile = 'C:\ssl.pfx';   ## full path to SSL certificate file  
  $mySslCertificatePassword = ConvertTo-SecureString '******';   ## password for private key of the SSL certificate  
  $skipCertificateVerification = $true;   ## whether or not, skip verification for the SSL certificate  
  
  Add-Type -AssemblyName 'Wssg.Web.DomainManagerObjectModel';  
  [Microsoft.WindowsServerSolutions.RemoteAccess.Domains.DomainConfigurationHelper]::SetDomainNameAndCertificate($myExternalDomainName,$mySslCertificateFile,$mySslCertificatePassword,$skipCertificateVerification);  
  ##  
  ## To install VPN with static IPv4 pool (and allow all existing users to establish VPN).  
  ##  
  
  Install-WssVpnServer -IPv4AddressRange ('192.168.0.160','192.168.0.240') -ApplyToExistingUsers;  
  ```  
  
  Если установить подключение к VPN до передачи сервера клиентам невозможно, необходимо сделать порт сервера 3389 доступным по Интернету, чтобы конечные пользователи могли использовать RDP для подключения к серверу и самостоятельно выполнять настройку.  
  
  Ниже представлены две стандартные топологии сети сервера, а также способы настройки VPN/удаленного веб-доступа (RWA):  
  
- Топология 1 (рекомендуемая)  
  
  -   Сервер в отдельной виртуальной сети под устройством NAT.  
  
  -   Служба DHCP подключена в виртуальной сети, либо серверу присвоен статический IP-адрес.  
  
  -   Порт сервера 443 доступен с порта 443 общего IP-адреса.  
  
  -   Для порта 443 разрешен сквозной режим VPN.  
  
  -   Пул адресов IPv4 VPN должен располагаться в пределах одной подсети адреса сервера.  
  
  -   Каждую секунду серверу должен назначаться статический IP-адрес в пределах одной сети, но вне пула адресов VPN.  
  
- Топология 2  
  
  -   У сервера имеется частный IP-адрес.  
  
  -   Порт 443 на сервере доступен с общедоступного IP-адрес s порт 443.  
  
  -   Для порта 443 разрешен сквозной режим VPN.  
  
  -   Пул адресов IPv4 VPN должен располагаться в другом диапазоне адресов сервера.  
  
  Топология 2 не предусматривает сценарии со вторым сервером.  
  
## <a name="how-do-i-perform-common-tasks-via-windows-powershell"></a>Выполнение обычных задач посредством Windows PowerShell  
 **Включение удаленного веб-доступа**  
  
```  
Enable-WssRemoteWebAccess [-SkipRouter] [-DenyAccessByDefault] [-ApplyToExistingUsers]  
```  
  
 Пример.  
  
```  
$Enable-WssRemoteWebAccess  œDenyAccessByDefault  œApplyToExistingUsers  
```  
  
 Данная команда позволяет включить удаленный веб-доступ с помощью автоматически настроенного маршрутизатора и изменить установленные по умолчанию права доступа для всех существующих пользователей.  
  
 **Добавить пользователя**  
  
```  
Add-WssUser [-Name] <string> [-Password] <securestring> [-AccessLevel <string> {User | Administrator}] [-FirstName <string>] [-LastName <string>] [-AllowRemoteAccess] [-AllowVpnAccess]   [<CommonParameters>]  
```  
  
 Пример.  
  
```  
$password = ConvertTo-SecureString "Passw0rd!" -asplaintext  œforce  
$Add-WssUser -Name User2Test -Password $password -Accesslevel Administrator -FirstName User2 -LastName Test  
```  
  
 Данной команды происходит добавление администратора с именем "User2Test" с паролем Passw0rd!.  
  
 **Включение и отключение пользователя**  
  
 Пример.  
  
```  
$CurrentUser = get-wssuser  œname user2test  
$CurrentUser.UserStatus = 0  
$CurrentUser.Commit()  
```  
  
 Эта команда отключает пользователя с именем user2test. При установлении значения 1 для параметра UserStatus происходит включение этого пользователя.  
  
 **Добавление папки сервера**  
  
```  
Add-WssFolder [-Name] <string> [-Path] <string> [[-Description] <string>] [-KeepPermissions] [<CommonParameters>]  
```  
  
 Пример.  
  
```  
$Add-WssFolder -Name "MyTestFolder" -Path "C:\ServerFolders\MyTestFolder"  
```  
  
 Эта команда будет добавить папку сервера с именем MyTestFolder в указанном расположении.  
  
## <a name="how-do-i-add-a-second-server-to-the-windows-server-essentials-domain"></a>Как добавить второй сервер к домену Windows Server Essentials?  
 Так как Windows Server Essentials является контроллером домена, можно присоединить второй сервер к домену обычным способом.  
  
## <a name="which-email-solutions-can-be-integrated"></a>Интеграция служб электронной почты  
 Windows Server Essentials позволяет интегрировать две электронной почты без дополнительной настройки: Office 365 и локальную службу Exchange. Если вы используете собственное решение для хостинга электронной почты, будет необходимо разработать надстройку для интеграции Windows Server Essentials с вашей размещенной службой электронной почты.  
  
## <a name="how-do-i-migrate-on-premises-windows-sbs-201120082003-to-the-hosted-windows-server-essentials"></a>Как выполнить перенос локальных Windows SBS (2011/2008/2003) на размещенный Windows Server Essentials?  
 Руководства по миграции доступны для локальных Windows Small Business Server (Windows SBS) для миграции Windows Server Essentials. Некоторые этапы могут отличаться в различных условиях размещенной среды. Однако основные задачи и рабочие нагрузки при выполнении миграции должны быть такими же. Рекомендуем придерживаться [руководств по миграции](https://go.microsoft.com/fwlink/p/?LinkID=254292) и выполнять пользовательскую настройку в соответствии со средой размещения.  
  
 Кроме того, рекомендуется помещать исходный и целевой серверы в одной подсети. Если это невозможно, необходимо обеспечить выполнение следующих условий:  
  
-   Внутренние имена DNS исходного и целевого серверов должны быть доступны друг для друга.  
  
-   Все необходимые порты должны быть открыты.  
  
## <a name="how-can-i-upgrade-windows-server-essentials-to-windows-server-standard"></a>Как можно обновить Windows Server Essentials на Windows Server Standard?  
 Вы можете обновить Windows Server Essentials на Windows Server Standard. Удалите блокировки и ограничения и добавьте недостающие пакеты из Windows Server Standard. Для получения дополнительной информации [загрузите документ](https://go.microsoft.com/fwlink/p/?LinkID=253181).  
  
## <a name="what-are-the-native-tools-for-monitoring-and-management"></a>Основные инструменты для контроля и управления  
  
### <a name="group-policy-management"></a>Управление групповой политикой  
 Windows Server Essentials использует собственную поддержку групповой политики в Windows Server 2012 и предоставляет пользовательский интерфейс для настройки параметров перенаправления и безопасности папки.  
  
> [!NOTE]
>  Если в размещенной среде подключена функция перенаправления папок для профиля пользователя, это может увеличить время входа на сервер для конечных пользователей, если обрабатывается большой объем данных.  
  
### <a name="management-pack"></a>Пакет управления  
 Пакет управления Windows Server Essentials обеспечивает функцию контроля за системы оповещения о работоспособности в Windows Server Essentials, чтобы помочь поставщикам услуг размещения управлять большим количеством серверов Windows Server Essentials, посвященное различным небольшим компаниям. В данной версии контролировать можно только критические оповещения в системе.  
  
#### <a name="management-pack-scope"></a>Область применения пакета управления  
 Этот пакет управления помогает пользователю контролировать функции, относящиеся к Windows Server Essentials. Он не обеспечивает контроль функций, относящихся к операционной системе Windows Server 2012 Standard. Для мониторинга Windows Server Essentials, следует использовать пакет управления Windows Server Essentials и Management Pack для Windows Server 2012 Standard.  
  
#### <a name="mandatory-configuration"></a>Обязательная настройка  
 Прежде чем приступить к работе с пакетом управления необходимо выполнить следующие действия:  
  
1.  Установите Агент и настройте параметры доверия, используя доверие сертификата. Так как Windows Server Essentials предварительно настроен как контроллер домена и не может иметь отношение доверия с другими доменами или лесами, агент System Center Operations Manager должен быть установлен на Windows Server Essentials и настроить параметры доверия с помощью управления сервер, с помощью сертификатов.  
  
2.  Загрузите пакет управления. Мониторинг Windows Server Essentials с помощью Operations Manager 2007, необходимо сначала загрузить [пакет управления операционной системы Windows Server](https://connect.microsoft.com/WindowsServer/Downloads/DownloadDetails.aspx?DownloadID=45010) из каталога пакетов управления.  
  
3.  Импортируйте файл пакета управления. Если используется локализованная версия пакета управления, необходимо импортировать основной пакет управления и языковой пакет.  
  
#### <a name="files-in-this-monitoring-pack"></a>Файлы в пакете управления  
 Monitoring Pack для Windows Server Essentials включает следующие файлы:  
  
-   Microsoft.Windows.Server.2012.Essentials.mp  
  
-   Microsoft.Windows.Server.2012.Essentials. < языкового стандарта\>MP-файлы  
  
### <a name="back-up-and-restore"></a>Резервное копирование и восстановление  
 Windows Server Essentials позволяет создавать резервные копии сервера и клиента.  
  
#### <a name="back-up-the-server"></a>Архивация сервера  
 Windows Server Essentials поддерживает два типа архивации сервера: локальная Архивация и резервное копирование за пределами организации.  
  
 **Локальная архивация** позволяет регулярно выполнять добавочную архивацию на уровне блоков на отдельный диск. Как поставщик услуг можно подключить виртуальный диск к виртуальной Машине Windows Server Essentials и назначить выполнение архивации сервера на этот виртуальный диск. Виртуальный диск должен находиться на другом диске и виртуальная машина Windows Server Essentials.  
  
- Если у вас есть другой механизм архивации ВМ Windows Server Essentials, и ваши пользователи видели функцию внутренней архивации сервера Windows Server Essentials не требуется, можно отключить эту функцию и удалить все связанные пользовательского интерфейса из Windows Server Essentials Панель мониторинга. Дополнительные сведения см. в разделе Настройка архивации сервера [документа ADK](https://go.microsoft.com/fwlink/p/?LinkID=249124).  
  
  **Удаленная архивация** позволяет периодически архивировать данные сервера на облачную службу. Можно загрузить и установить Microsoft Azure Backup интеграции модуля для Windows Server Essentials использовать Azure Backup, предоставляемой корпорацией Майкрософт.  
  
  В случае если вы или ваши пользователи предпочитают другую облачную службу, необходимо выполнить следующие действия:  
  
1.  Обновите пользовательский интерфейс панели мониторинга Windows Server Essentials, чтобы на ней присутствовала ссылка в предпочтительный облачную службу, вместо значения по умолчанию Azure Backup. Дополнительные сведения см. в разделе "Настройка образа" [документа ADK](https://go.microsoft.com/fwlink/p/?LinkID=249124).  
  
2.  (Необязательно) Разработайте надстройку для панели мониторинга Windows Server Essentials, для настройки и управления облачной службой архивации.  
  
#### <a name="back-up-the-client"></a>Архивация данных клиента  
 Windows Server Essentials поддерживает два типа резервного копирования данных клиента: полная архивация данных клиента и журнала файлов.  
  
> [!NOTE]
>  Архивация данных клиента может повлиять на работоспособность системы, поскольку данные клиента передаются на сервер через VPN.  
  
 **Полная архивация данных клиента** выполняется по умолчанию для всех клиентских устройств, подключенных к сети Windows Server Essentials. В данном случае происходит добавочная архивация всего клиента (системы и данных) с поддержкой дедупликации данных. Резервные копии данных будет на сервере под управлением Windows Server Essentials. В случае сбоя данные клиента остаются на последнем успешном этапе архивации. Можно отключить эту функцию, выполнив действия, описанные в создание файла Cfg.ini части [документа ADK](https://technet.microsoft.com/library/jj200150).  
  
 При выполнении полной архивации данных клиента необходимо учитывать следующие аспекты:  
  
- Производительность: первоначальная архивация данных клиента может занять много времени в связи с большим объемом данных для загрузки.  
  
- Стабильность: иногда подключение к Интернету бывает нестабильным со стороны клиента. Архивация данных клиента является возобновляемым процессом, и контрольная точка по умолчанию — 40 ГБ (база данных архивации создает контрольную точку каждый раз, когда происходит архивация данных объемом 40 ГБ). Это значение можно уменьшить, если подключение к Интернету нестабильно.  
  
  -   Для выполнения манипуляций с контрольными точками на сервере необходимо установить для ключа регистрации HKLM\Software\Microsoft\Windows Server\Backup\GetCheckPointJobs значение 1.  
  
  -   Для изменения предельного значения контрольной точки на клиентском устройстве необходимо изменить значение HKLM\Software\Microsoft\Windows Server\Backup\CheckPointThreshold по умолчанию (40 ГБ).  
  
- Восстановление исходного состояния клиента: поскольку среда предустановки Windows не поддерживает VPN-подключения, функция восстановления исходного состояния клиента недоступна.  
  
  **История файлов** — это функция Windows 8.1 для архивации данных профиля (библиотеки, рабочий стол, контакты, Избранное) в общую сетевую папку. В Windows Server Essentials мы позволяет осуществлять централизованное управление параметрами истории файлов всех клиентов Windows 8.1, присоединенных к Windows Server Essentials. Данные архивации хранятся на сервере под управлением Windows Server Essentials. Можно отключить эту функцию, выполнив действия, описанные в создание файла Cfg.ini части [документа ADK](https://technet.microsoft.com/library/jj200150).  
  
### <a name="storage-management"></a>Управление хранилищами  
 [Новая функция управления дисковыми пространствами](https://technet.microsoft.com/library/hh831739.aspx) позволяет объединять физический объем памяти разрозненных жестких дисков, динамически добавлять жесткие диски и создавать тома данных с заданными уровнями устойчивости. Вы также можете присоединить диск iSCSI на Windows Server Essentials для увеличения хранилища.  
  
## <a name="what-are-the-main-scenarios-i-should-test"></a>Основные сценарии, требующие проверки  
 Для успешного размещения рекомендуется проверить следующие сценарии:  
  
 **Развертывание сервера**  
  
- Развертывание сервера Windows Server Essentials в лабораторной среде.  
  
- Настройка образа Windows Server Essentials при необходимости.  
  
- Автоматизация развертывания Windows Server Essentials с помощью файла автоматической и файл cfg.ini.  
  
- Перенос локальных Windows SBS на размещенный Windows Server Essentials.  
  
- Обновление с Windows Server Essentials в Windows Server 2012.  
  
  **Конфигурация сервера**  
  
- Настройте повсеместный доступ (VPN, удаленный веб-доступ, DirectAccess).  
  
- Настройте параметры хранилища и папки сервера.  
  
- (Если применимо) настройте параметры архивации сервера, оперативной архивации, архивации данных клиента, истории файлов.  
  
- (Если применимо) настройте и управляйте дисковыми пространствами.  
  
- (Если применимо) настройте интеграцию служб электронной почты (Office 365, размещенная служба Exchange и пр.).  
  
- (Если применимо) настройте сервер мультимедиа.  
  
  **Управление сервером**  
  
- Управляйте пользователями.  
  
- Настройте и получайте электронные уведомления для оповещений.  
  
- В случае ошибки / предупреждения запустите BPA.  
  
- Настройте пакет мониторинг System Center.  
  
- Настройте функцию восстановления сервера на случай повреждения.  
  
  **Взаимодействие с клиентом**  
  
- Развертывание клиентов через Интернет ((ПК или Mac OS).  
  
- С помощью панели запуска на клиентском компьютере войдите в общую папку.  
  
- Получите доступ к ресурсам сервера через службу удаленного веб-доступа с помощью различных устройств (ПК, телефон, планшет).  
  
- Приложение My Server для ОС Windows Phone.  
  
- (Если применимо) история файлов, архивация и восстановление данных клиента (без BMR), перенаправление папок.  
  
- (Если применимо) интеграция служб электронной почты.  
  
## <a name="where-can-i-get-more-support"></a>Дополнительная информация  
 С документами SDK и ADK можно ознакомиться, перейдя по следующим ссылкам:  
  
- [ПАКЕТ SDK](https://go.microsoft.com/fwlink/p/?LinkID=248648)  
  
- [ADK](https://go.microsoft.com/fwlink/p/?LinkID=249124)  
  
  Вы можете оставить отчет об ошибках в разделе Соединение. Для создания журналов необходимо заархивировать папку на сервере и на клиентах, подключенных к серверу: C:\ProgramData\Microsoft\Windows Server\Logs.
