---
title: "Размещенный сервер Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
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
ms.openlocfilehash: 23e586c22ca14af7b02550e2fa1c9522e379170c
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="hosted-windows-server-essentials"></a>Размещенный сервер Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Данный документ содержит информацию, предназначенную для поставщиков услуг размещения, которые намереваются развертывать Windows Server Essentials в своих лабораториях и предлагать своим клиентам Windows Server Essentials как служба.  
  
## <a name="what-is-windows-server-essentials"></a>Что такое Windows Server Essentials  
 Windows Server Essentials используется решение для малого бизнеса перекрестные, которое разработано с использованием лучших в классе 64-разрядные продукты и предназначено для обеспечения серверной среды, подходящей для подавляющего большинства небольших компаний. В Windows Server Essentials включаются следующие технологии.  
  
 **Операционная система сервера:** ядро Windows Server Essentials служат технологии Windows Server 2012. Дополнительные сведения см. на сайте [веб-сайта Windows Server 2012](https://www.microsoft.com/en-us/server-cloud/products/windows-server-2012-r2/default.aspx#fbid=ZH0GD_CRAWh).  
  
 **Защита данных:** Windows Server Essentials реализованы некоторые новые функции, доступные в Windows Server 2012, обеспечивающие повышенный уровень данных защиты. [Новая функция дисковых пространств](https://technet.microsoft.com/library/hh831739.aspx) позволяет объединять физический объем памяти разрозненных жестких дисков, динамически добавлять жесткие диски и создавать тома данных с заданными уровнями устойчивости. Windows Server Essentials может выполнять полную архивацию системы и восстановление исходного состояния системы сервера, себя, а также клиентские компьютеры, подключенные к сети? теперь с поддержкой томов объемом более 2 ТБ. Новые возможности Windows Server 2012 [Windows Azure Online Backup](https://technet.microsoft.com/library/hh831419.aspx) можно использовать для защиты файлов и папок в службе облачного хранилища, управление которой осуществляется корпорацией Майкрософт. Windows Server Essentials также централизованно управляет и настраивает функцию ведения журнала файлов клиентов Windows 8.1, помогая пользователям восстанавливать случайно удаленные или перезаписанные файлы без помощи администратора.  
  
 **Повсеместный доступ:** удаленный веб-доступ обеспечивает упрощенное сенсорного браузера для доступа к приложениям и данным практически из любого места у вас есть подключение к Интернету и практически с любого устройства. Windows Server Essentials также включает усовершенствованное приложение для Windows Phone и новое приложение для Windows 8.1 компьютеров, позволяя пользователям без труда подключаться к серверу, поиск и доступ к файлам и папкам на сервере. Файлы также автоматически кэшируются для автономного доступа и синхронизируются при появлении подключения к серверу. Windows Server Essentials позволяет с легкостью устанавливать виртуальную частную сеть (VPN) в процессе несколько щелчков мышки, управляемых с помощью мастера и упрощает управление доступом к VPN для пользователей. Клиентские компьютеры могут использовать подключение к VPN для удаленного входа в среду Windows SBS, находясь вне офиса.  
  
 **Гибкость рабочей нагрузки:** Windows Server Essentials был разработан, чтобы разрешить пользователям возможность выбирать, какие приложения и службы запускать локально, а также которой выполняются в облаке. В предыдущих версиях Windows Small Business Server Standard включен сервер Exchange Server как компонент продукта, который был расходов и сложностями для клиентов, желавших использовать службы обмена сообщениями и совместной работы, на основе облака. С Windows Server Essentials клиенты могут использовать тот же тип интегрированного управления ли они решили запускать локальную копию сервера Exchange Server, подпишутся на размещенную службу Exchange или на Microsoft Office 365.  
  
 **Мониторинг работоспособности:** Windows Server Essentials контролирует собственное состояние работоспособности и состояние клиентских компьютеров под управлением Windows 8.1, Windows 7 и Mac OS X версии 10.5 и более поздних версий. Состояние работоспособности отображает различные проблемы, связанные с архивацией данных компьютера, хранилищем сервера, недостатком места на диске и многое другое.  
  
 **Расширения:** Windows Server Essentials создает модель расширяемости Windows SBS 2011 Essentials, которая позволяет прочим поставщикам программного обеспечения для добавления возможностей и компонентов в основной продукт и предоставляет новый набор веб-служб API-интерфейсы. Кроме того, обеспечена совместимость с существующим [средств разработки программного обеспечения](https://msdn.microsoft.com/library/gg513958.aspx) (SDK) и [надстройки](https://pinpoint.microsoft.com/applications/search?fpt=300105&q=small+business+server+essentials) предназначенными для Windows SBS 2011 Essentials.  
  
## <a name="how-can-i-customize-an-image"></a>Настройка образа  
 Обратитесь к [Windows Server Essentials](https://go.microsoft.com/fwlink/p/?LinkID=249124), который является стандартный процесс выполнения sysprep Windows Server с дополнительными этапами настройки Windows Server Essentials. Для завершения настройки, следуйте инструкциям в [создание простого пользовательского образа](https://technet.microsoft.com/en-us/library/jj200117) и [настройка образа](https://technet.microsoft.com/en-us/library/jj200161), а затем следуйте инструкциям в [Подготовка образа для развертывания](https://technet.microsoft.com/en-us/library/jj200142) для выполнения записи окончательного образа.  
  
 Обращайте внимание на следующие аспекты:  
  
1.  Необходимо пропускать начальную настройку (IC), добавив файл SkipIC.txt в корне любого диска. После установки сервера и перед IC нажмите комбинацию клавиш Shift + F10 для вызова окна cmd и создайте файл SkipIC.txt C: / диска. После настройки не забудьте удалить файл SkipIC.txt.  
  
2.  Если вам требуется развернуть Windows Server Essentials на диске объемом менее 90 ГБ, следует добавить раздел реестра перед sysprep:  
  
    ```  
    %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\windows server\setup" /v HWRequirementChecks /t REG_DWORD /d 0 /f  
    ```  
  
 После sysprep можно воспользоваться образом диска, или запечатать его обратно в Install.wim для нового развертывания.  
  
 При использовании диспетчера виртуальных машин, можно создать шаблон, используя запущенный экземпляр. Создание шаблона будет экземпляру sysprep и завершить работу сервера. После его сохранения в библиотеку, можно загружать экземпляр по необходимости.  
  
##  <a name="BKMK_automatedeployment"></a>Как автоматизировать развертывание?  
 После получения настроенного образа, можно выполнить развертывание с помощью своего собственного образа. Для выполнения полуавтоматической установки, необходимо предоставить/развернуть файл unattend.xml для установки среды предустановки Windows. Для выполнения полностью автоматической установки, также необходимо предоставить файл cfg.ini для начальной настройки Windows Server Essentials.  
  
1.  Выполнение только автоматической установки WinPE. Это автоматизации только установки среды предустановки Windows и Установка остановлена перед начальной настройкой, чтобы пользователи могли предоставлять Corp, домена и администраторе сами по себе после RDP в сеанс сервера. Для этого:  
  
    1.  Предоставьте файл Windows unattend.xml. Выполните [Windows 8.1 ADK](https://go.microsoft.com/fwlink/?LinkId=248694) для создания файла и введите всю необходимую информацию, включая имя сервера, ключи к продуктам и пароль администратора. В разделе Microsoft-Windows-Setup файла unattend.xml укажите приведенные ниже.  
  
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
  
    2.  Порт RDP 3389 должен открыт на общем IP, чтобы клиент мог использовать администратора и пароль, указанный в файле unattend.xml протоколу удаленного рабочего стола на сервер для завершения начальной настройки.  
  
    > [!NOTE]
    >  Если не изменить пароль по умолчанию, установка сервера будет приостановлена окно с предложением ввести пароль. **Примечание** конечные пользователи должны использовать учетную запись администратора по умолчанию для входа сервер и выполнения начальной настройки.  
  
 При использовании диспетчера виртуальных машин, можно указать пароль администратора в консоли при создании нового экземпляра из шаблона.  
  
1.  Выполнение полностью автоматической установки, и автоматической начальной настройки. Для этого:  
  
    1.  Предоставьте файл unattend.xml, как описано выше, если развертывание начинается с установки WinPE.  
  
    2.  См. раздел Windows Server Essentials ADK, [Создание файла Cfg.ini](https://technet.microsoft.com/en-us/library/jj200150), чтобы создать файл.  
  
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
  
    5.  Если задается параметр WebDomainName, убедитесь, что запись DNS также обновлена для указания общего IP сервера s.  
  
    6.  Если вы не указали выше сведения WebDomainName, убедитесь, что необходимо открыть порт 3389, чтобы клиенты могли использовать RDP для подключения к серверу и завершения настройки VPN.  
  
> [!NOTE]
>  Убедитесь, что настройки часового пояса сервера узла виртуальной Машины и ВМ Windows Server Essentials совпадает с. В противном случае, могут возникать различные ошибки (начальной настройки не удается на задачи, связанные с сертификатом; сертификат может не работать для нескольких часов после установки; сведения об устройстве может не обновляться надлежащим образом и т. д).  
  
 После развертывания проверьте следующий раздел реестра в папке HKLM\software\microsoft\windows server\setup завершения, чтобы проверить успешность начальной настройки. Если SetupStage == ICDone & & ICStatus == 1, это означает, что начальная настройка успешно завершена.  
  
## <a name="what-is-the-supported-network-topology"></a>Топология поддерживаемой сети  
 Чтобы использовать Windows Server Essentials с перемещаемого клиентского компьютера, должна быть подключена VPN. Рекомендуется для подключения VPN SSTP использовать порт 443. Если для удаленного веб-доступа или веб-службы приложений требуется функция сервера мультимедиа, следует также включить порт 80.  
  
 Подключение к VPN можно выполнить во время автоматического развертывания с помощью сценария Windows PowerShell или его можно настроить с помощью мастера после начальной настройки.  
  

-   Чтобы включить VPN во время автоматического развертывания, в разделе [как автоматизировать развертывание? ](Hosted-Windows-Server-Essentials.md#BKMK_automatedeployment) в этом документе.  

-   Чтобы включить VPN во время автоматического развертывания, в разделе [как автоматизировать развертывание? ](../install/Hosted-Windows-Server-Essentials.md#BKMK_automatedeployment) в этом документе.  

  
-   Чтобы включить VPN с помощью сценария Windows PowerShell, выполните следующий командлет с правами администратора и введите всю необходимую информацию.  
  
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
  
 Если невозможно предоставить VPN-подключение до передачи сервера клиентам, убедитесь, что порт сервера 3389 доступным по Интернету, чтобы пользователи могли использовать RDP для подключения к серверу и самостоятельно выполнять конфигурацию.  
  
 Ниже представлены две стандартные топологии сети со стороны сервера, а также способы настройки VPN/удаленного веб доступа (RWA):  
  
-   Топология 1 (рекомендуемая)  
  
    -   Сервер в отдельной виртуальной сети под устройством NAT..  
  
    -   Служба DHCP подключена в виртуальной сети или серверу присвоен статический IP-адрес.  
  
    -   Порт сервера 443 доступен с порта 443 общего IP.  
  
    -   Для порта 443 разрешен сквозной режим VPN.  
  
    -   Пул адресов VPN IPv4 должен располагаться в одной подсети адреса сервера.  
  
    -   Каждую секунду серверу должен назначаться статический IP-адрес, в той же подсети, но вне пула адресов VPN.  
  
-   Топология 2:  
  
    -   Сервер имеет частный IP-адрес.  
  
    -   Порт 443 на сервере доступен из общедоступных IP-адрес s порт 443.  
  
    -   Для порта 443 разрешен сквозной режим VPN.  
  
    -   Пул адресов VPN IPv4 находится в другом диапазоне адресов сервера.  
  
 Сценарии второго сервера в топологии 2 не поддерживаются.  
  
## <a name="how-do-i-perform-common-tasks-via-windows-powershell"></a>Выполнение обычных задач посредством Windows PowerShell  
 **Включение удаленного веб-доступа**  
  
```  
Enable-WssRemoteWebAccess [-SkipRouter] [-DenyAccessByDefault] [-ApplyToExistingUsers]  
```  
  
 Пример:  
  
```  
$Enable-WssRemoteWebAccess  œDenyAccessByDefault  œApplyToExistingUsers  
```  
  
 Эта команда включения удаленного веб-доступа с помощью автоматически настроенного маршрутизатора и изменить заданные по умолчанию права доступа для всех существующих пользователей.  
  
 **Добавление пользователя**  
  
```  
Add-WssUser [-Name] <string> [-Password] <securestring> [-AccessLevel <string> {User | Administrator}] [-FirstName <string>] [-LastName <string>] [-AllowRemoteAccess] [-AllowVpnAccess]   [<CommonParameters>]  
```  
  
 Пример:  
  
```  
$password = ConvertTo-SecureString "Passw0rd!" -asplaintext  œforce  
$Add-WssUser -Name User2Test -Password $password -Accesslevel Administrator -FirstName User2 -LastName Test  
```  
  
 Эта команда происходит добавление администратора с именем "User2Test" и паролем Passw0rd!.  
  
 **Включение и отключение пользователя**  
  
 Пример:  
  
```  
$CurrentUser = get-wssuser  œname user2test  
$CurrentUser.UserStatus = 0  
$CurrentUser.Commit()  
```  
  
 Данной команды происходит отключение пользователя с именем user2test. 1 для параметра UserStatus происходит включение этого пользователя.  
  
 **Добавление папки сервера**  
  
```  
Add-WssFolder [-Name] <string> [-Path] <string> [[-Description] <string>] [-KeepPermissions] [<CommonParameters>]  
```  
  
 Пример:  
  
```  
$Add-WssFolder -Name "MyTestFolder" -Path "C:\ServerFolders\MyTestFolder"  
```  
  
 Данной команды происходит добавление папки сервера с именем MyTestFolder в указанном расположении.  
  
## <a name="how-do-i-add-a-second-server-to-the-windows-server-essentials-domain"></a>Как добавить второй сервер к домену Windows Server Essentials  
 Так как Windows Server Essentials является контроллером домена, можно присоединить второй сервер к домену обычным способом.  
  
## <a name="which-email-solutions-can-be-integrated"></a>Можно интегрировать электронной почты?  
 Windows Server Essentials позволяет интегрировать две службы электронной почты вне ящика: Office 365 и локальную службу Exchange. Если вы используете собственную размещенного электронной почты, необходимо разработать надстройку для интеграции Windows Server Essentials с вашей размещенной службой электронной почты.  
  
## <a name="how-do-i-migrate-on-premises-windows-sbs-201120082003-to-the-hosted-windows-server-essentials"></a>Как перенести локальными Windows SBS (2011/2008/2003) на размещенный Windows Server Essentials?  
 Руководства по миграции, доступных для локальной Windows Small Business Server (Windows SBS) на Windows Server Essentials. Некоторые действия могут не относиться точно так же, в различных условиях размещенной среды. Однако основные задачи и рабочие нагрузки, которые нужно перенести должны быть одинаковыми. Рекомендуется придерживаться [руководства по миграции](https://go.microsoft.com/fwlink/p/?LinkID=254292) и выполнять пользовательскую настройку в соответствии со средой размещения.  
  
 Рекомендуется размещать исходный сервер и конечный сервер в той же подсети. Если это невозможно, необходимо убедиться в том:  
  
-   Внутренние имена DNS исходного сервера и целевого серверов должны быть доступны друг для друга.  
  
-   Все необходимые порты открыты.  
  
## <a name="how-can-i-upgrade-windows-server-essentials-to-windows-server-standard"></a>Как обновить Windows Server Essentials на Windows Server Standard?  
 Windows Server Essentials можно обновить до Windows Server Standard. Удалите блокировки и ограничения и добавьте пакеты, которые отсутствуют в Windows Server Standard. Дополнительные сведения [Загрузите этот документ](https://go.microsoft.com/fwlink/p/?LinkID=253181).  
  
## <a name="what-are-the-native-tools-for-monitoring-and-management"></a>Что такое основные инструменты для контроля и управления  
  
### <a name="group-policy-management"></a>Управление групповой политикой  
 Windows Server Essentials использует инструмент управления групповой политики в Windows Server 2012 и предоставляет пользовательский интерфейс для настройки параметров перенаправления папок и безопасности.  
  
> [!NOTE]
>  В размещенной среде Если включено перенаправление папок для профиля пользователя, он может увеличить время конечные пользователи могут войти в систему, если обрабатывается большой объем данных.  
  
### <a name="management-pack"></a>Пакет управления  
 Пакет управления Windows Server Essentials обеспечивает функцию контроля за системой оповещений о работоспособности в Windows Server Essentials помогает поставщикам услуг размещения управлять большим количеством серверов Windows Server Essentials, предоставляемых различным небольшим компаниям. В данной версии контролировать можно только критических оповещений в системе.  
  
#### <a name="management-pack-scope"></a>Область применения пакета управления  
 Этот пакет управления помогает пользователю контролировать функции, относящиеся к Windows Server Essentials. Он не обеспечивает контроль функций, которые обычно возникают в операционной системе Windows Server 2012 Standard. Для слежения за Windows Server Essentials, необходимо использовать пакет управления Windows Server Essentials и Management Pack для Windows Server 2012 Standard.  
  
#### <a name="mandatory-configuration"></a>Обязательная настройка  
 Следующие шаги необходимо выполнить, прежде чем использовать пакет управления:  
  
1.  Установите агент и настройте параметры доверия, используя доверие сертификата. Поскольку Windows Server Essentials по умолчанию как контроллер домена и не может иметь доверия с другими доменами или лесами, агент System Center Operation Manager должен устанавливаться на Windows Server Essentials и настроить параметры доверия с сервером управления, используя сертификаты.  
  
2.  Загрузите пакет управления. Для слежения за Windows Server Essentials с помощью Operations Manager 2007, необходимо сначала загрузить [пакет управления операционной системы Windows Server](https://connect.microsoft.com/WindowsServer/Downloads/DownloadDetails.aspx?DownloadID=45010) из каталога пакетов управления.  
  
3.  Импортируйте файл пакета управления. Если используется локализованная версия пакета управления, необходимо импортировать файл пакета управления основной и языковой пакет.  
  
#### <a name="files-in-this-monitoring-pack"></a>Файлы в пакете управления  
 Пакет управления для Windows Server Essentials включает следующие файлы:  
  
-   Microsoft.Windows.Server.2012.Essentials.mp  
  
-   Microsoft.Windows.Server.2012.Essentials. < locale\ > .mp  
  
### <a name="back-up-and-restore"></a>Резервное копирование и восстановление  
 Windows Server Essentials позволяет архивировать и сервер и клиент.  
  
#### <a name="back-up-the-server"></a>Резервное копирование сервера  
 Windows Server Essentials поддерживает два типа архивации сервера: локальную резервного копирования и облачные.  
  
 **Локальной копии** позволяет выполнять добавочную архивацию на уровне блоков на регулярной основе, на отдельный диск. Как поставщик услуг размещения может подключить виртуальный диск к ВМ Windows Server Essentials и назначить выполнение архивации сервера для этого виртуального диска. Виртуальный диск должен находиться на том же физическом диске, чем ВМ Windows Server Essentials.  
  
-   Если у вас имеется другой механизм архивации ВМ Windows Server Essentials, и не хотите, чтобы ваши пользователи видели функцию внутренней архивации сервера Windows Server Essentials, можно отключить его и удалить все связанные пользовательский интерфейс из панели мониторинга Windows Server Essentials. Дополнительные сведения см. в разделе «Настройка архивации сервера» [документа ADK](https://go.microsoft.com/fwlink/p/?LinkID=249124).  
  
 **Резервное копирование Дистанционное** позволяет периодически архивировать данные сервера на облачную службу. Можно загрузить и установить Microsoft Azure Backup интеграции модуль для Windows Server Essentials для эффективного использования Azure Backup, предоставляемой корпорацией Майкрософт.  
  
 Если вы или ваши пользователи предпочитают другую облачную службу, необходимо выполнить следующие действия:  
  
1.  Обновите пользовательский интерфейс панели мониторинга Windows Server Essentials, чтобы на ней присутствовала ссылка на основной облачной службы, вместо значения по умолчанию Azure Backup. Дополнительные сведения см. Настройка разделе изображений [документа ADK](https://go.microsoft.com/fwlink/p/?LinkID=249124).  
  
2.  (Необязательно) Разработайте надстройку для панели мониторинга Windows Server Essentials, позволяющую настраивать и управлять облачной службой архивации.  
  
#### <a name="back-up-the-client"></a>Архивация данных клиента  
 Windows Server Essentials поддерживает два вида архивации данных клиента: полная архивация данных клиента и истории файлов.  
  
> [!NOTE]
>  Архивация данных клиента может повлиять на производительность, так как данные должны передаваться от клиента к серверу через VPN.  
  
 **Полная архивация данных клиента** включено по умолчанию для всех клиентских устройств, подключенных к сети Windows Server Essentials. Он данном случае происходит Добавочная архивация всего клиента (системы и данных) и поддерживает дедупликацию данных. Данные архивации помещаются на сервере под управлением Windows Server Essentials. Сбой клиента можно получить свои данные предыдущей точки восстановления. Можно отключить эту функцию, выполнив действия, описанные в создания файла Cfg.ini части [документа ADK](https://technet.microsoft.com/en-us/library/jj200150).  
  
 Ниже перечислены некоторые рекомендации по полная архивация данных клиента  
  
-   Производительность: резервное копирование первоначального клиента может занять продолжительное связи с большим объемом данных для загрузки.  
  
-   Стабильность: иногда подключение к Интернету может быть нестабильным на стороне клиента. Архивация данных клиента является возобновляемым, и контрольная точка по умолчанию — 40 ГБ (базы данных клиентской архивации создает контрольную точку каждый раз, когда резервное данных объемом 40 ГБ). Можно изменить это значение можно уменьшить, если подключение к Интернету нестабильно.  
  
    -   Чтобы включить задание контрольной точки на сервере, установите ключа регистрации HKLM\Software\Microsoft\Windows Server\Backup\GetCheckPointJobs значение 1.  
  
    -   Изменение порогового значения контрольной точки, на клиенте, измените значение HKLM\Software\Microsoft\Windows Server\Backup\CheckPointThreshold по умолчанию (40 ГБ).  
  
-   Восстановление исходного состояния клиента: поскольку среда предустановки Windows не поддерживает VPN-подключения, восстановления исходного состояния системы клиента не поддерживается.  
  
 **Файл журнала** — это функция Windows 8.1 для архивации данных профиля (библиотеки, рабочий стол, контакты, Избранное) в сетевую папку. В Windows Server Essentials позволяет осуществлять централизованное управление параметрами истории файлов всех клиентов Windows 8.1, подключенных к Windows Server Essentials. Данные архивации хранятся на сервере под управлением Windows Server Essentials. Можно отключить эту функцию, выполнив действия, описанные в создания файла Cfg.ini части [документа ADK](https://technet.microsoft.com/en-us/library/jj200150).  
  
### <a name="storage-management"></a>Управление хранилищем  
 [Новая функция дисковых пространств](https://technet.microsoft.com/library/hh831739.aspx) позволяет объединять физический объем памяти разрозненных жестких дисков, динамически добавлять жесткие диски и создавать тома данных с заданными уровнями устойчивости. Можно также подключить диск iSCSI для Windows Server Essentials для увеличения хранилища.  
  
## <a name="what-are-the-main-scenarios-i-should-test"></a>Что такое основные сценарии, требующие проверки  
 Для успешного размещения рекомендуется проверить следующие сценарии:  
  
 **Развертывание сервера**  
  
-   Развертывание сервера Windows Server Essentials в лабораторной среде.  
  
-   Настройка образа Windows Server Essentials при необходимости.  
  
-   Автоматизация развертывания Windows Server Essentials, добавив автоматический файл и файл cfg.ini.  
  
-   Миграция локальных Windows SBS на размещенный Windows Server Essentials.  
  
-   Обновление с Windows Server Essentials в Windows Server 2012.  
  
 **Конфигурация сервера**  
  
-   Настройте Повсеместный доступ (DirectAccess VPN, удаленный веб-доступ).  
  
-   Настройте хранилище и папки сервера.  
  
-   (Если применимо) Настройка архивации сервера, оперативной архивации, архивация данных клиента, истории файлов.  
  
-   (Если применимо) Настройка и управление дисковыми пространствами.  
  
-   (Если применимо) Настройте интеграцию служб электронной почты (Office 365, размещенного Exchange и т. д).  
  
-   (Если применимо) Настройте сервер мультимедиа.  
  
 **Управление сервером**  
  
-   Управление пользователями.  
  
-   Настройте и получайте электронные уведомления для оповещений.  
  
-   В случае ошибки/предупреждения запустите BPA.  
  
-   Настройте пакет мониторинг System Center.  
  
-   Настройте функцию восстановления сервера в случае повреждения.  
  
 **Взаимодействие с клиентом**  
  
-   Развертывание клиентов через Интернет (ПК или Mac OS).  
  
-   Использование панели запуска на клиенте в общую папку.  
  
-   Доступ к ресурсам сервера через службу удаленного доступа, с помощью различных устройств (ПК, телефон, планшет).  
  
-   Приложение My Server для Windows Phone.  
  
-   (Если применимо) История файлов, архивация данных клиента и восстановления (без BMR), перенаправление папок.  
  
-   (Если применимо) Интеграция служб электронной почты.  
  
## <a name="where-can-i-get-more-support"></a>Где получить дополнительную поддержку  
 Документами SDK и ADK можно ознакомиться с указанным ниже ссылкам:  
  
-   [ПАКЕТ SDK](https://go.microsoft.com/fwlink/p/?LinkID=248648)  
  
-   [ADK](https://go.microsoft.com/fwlink/p/?LinkID=249124)  
  
 Можно сообщить об ошибке группе функций через подключение. Для создания журналов необходимо заархивировать папку на сервере и клиентах, подключенных к серверу: C:\ProgramData\Microsoft\Windows Server\Logs.
