---
title: "Развертывание Windows Server Essentials Experience в качестве размещенного сервера"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a455c6b4-b29f-4f76-8c6b-1578b6537717
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: c299d2b5f3d6b48693c473754a5205a7d26b5d6a
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="deploy-windows-server-essentials-experience-as-a-hosted-server"></a>Развертывание Windows Server Essentials Experience в качестве размещенного сервера

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Данный документ содержит информацию, предназначенную для поставщиков услуг размещения, которые намереваются развертывать Microsoft Windows Server 16 с ролью Windows Server Essentials Experience (Далее Windows Server Essentials в остальной части документа) устанавливается в своих лабораториях и предлагать своим клиентам Windows Server Essentials Experience как служба. Данный документ содержит следующие разделы:  
  

-   [Обзор Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_WSEEOverview)  
  
-   [Преимущества размещения Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Benefits)  
  
-   [Поддерживаемые варианты развертывания](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_SupportedDeployment)  
  
-   [Поддерживаемые топологии сети](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_SupportedToplogy)  
  
-   [Настройка образа роли Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_CustomizeImage)  
  
-   [Автоматизация развертывания Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_AutomateDeployment)  
  
-   [Перенос данных из Windows Small Business Server на Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Migrate)  
  
-   [Общие задачи, с помощью Windows PowerShell](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_PowerShell)  
  
-   [Интеграция электронной почты с Windows Server Essentials](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_EmailIntegration)  
  
-   [Мониторинг и управление с помощью стандартных средств](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Monitoring)  
  
-   [Сценарии тестирования](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Scenarios)  
  
-   [Сведения о поддержке](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Support)  

-   [Обзор Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_WSEEOverview)  
  
-   [Преимущества размещения Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Benefits)  
  
-   [Поддерживаемые варианты развертывания](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_SupportedDeployment)  
  
-   [Поддерживаемые топологии сети](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_SupportedToplogy)  
  
-   [Настройка образа роли Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_CustomizeImage)  
  
-   [Автоматизация развертывания Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_AutomateDeployment)  
  
-   [Перенос данных из Windows Small Business Server на Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Migrate)  
  
-   [Общие задачи, с помощью Windows PowerShell](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_PowerShell)  
  
-   [Интеграция электронной почты с Windows Server Essentials](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_EmailIntegration)  
  
-   [Мониторинг и управление с помощью стандартных средств](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Monitoring)  
  
-   [Сценарии тестирования](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Scenarios)  
  
-   [Сведения о поддержке](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Support)  

  
##  <a name="BKMK_WSEEOverview"></a>Обзор Windows Server Essentials Experience  
 Режим Windows Server Essentials — это роль сервера, который доступен в Windows Server 2012 R2 Standard и Windows Server 2012 R2 Datacenter. При установке роли Windows Server Essentials Experience на сервере под управлением Windows Server 2012 R2, пользователь может использовать преимущества всех компонентов, которые доступны в Windows Server Essentials без каких-либо блокировок и ограничений. Режим Windows Server Essentials включает следующие перекрестные решения для малого и среднего бизнеса:  
  
-   **Хранение и защита данных** можно хранить клиента» о данных в центральном расположении и защищать данные сервера и клиента путем создания резервной копии сервера и клиентских компьютеров (количеством не более 75) в сети.  
  
-   **Управление пользователями** можно управлять пользователей и группами пользователей через упрощенную панель мониторинга сервера. Кроме того интеграция с Microsoft Azure Active Directory (Azure AD) обеспечивает простой доступ данных служб Microsoft online Services (например, Office 365, Exchange Online и SharePoint Online) для пользователей, используя свои учетные данные домена.  
  
-   **Службы интеграции** можно интегрировать сервер с Microsoft online services (например, Office 365, SharePoint Online и Microsoft Azure Backup). Можно также интегрировать сервер с вашими службами и службами сторонних поставщиков.  
  
-   **Повсеместный доступ** клиент может получить доступ к сервера, компьютерам сети и данных из любой точки, где они есть подключение к Интернету и с помощью практически с любого устройства. Удаленный веб-доступ позволяет получить доступ к приложениям и данным с помощью упрощенный, сенсорные дисплеи браузерного интерфейса. Приложение My Server позволяет получать доступ к данным из Windows Phone или магазина Майкрософт.  
  
-   **Потоковая передача мультимедиа** Если установить пакет мультимедиа на сервере с Windows Server Essentials Experience включен, конечный пользователь может сохранять музыку, видео и фотографии в общих папках, а затем получить доступ к этим медиафайлам с компьютеров сети или удаленного веб-доступа.  
  
-   **Наблюдение за работоспособностью** можно отслеживать работоспособность сети и получать настраиваемые отчеты о работоспособности.  
  
##  <a name="BKMK_Benefits"></a>Преимущества размещения Windows Server Essentials Experience  
  Режим Windows Server Essentials — это роль в Windows Server, которая повторно использовать уже существующую платформу развертывания и управления в Windows Server для развертывания и настройки роли Windows Server Essentials Experience. Ролью режим Windows Server Essentials предоставляет следующие преимущества:  
  
-   **Упрощенная развертывания** путем простой активации роли Windows Server Essentials Experience, некоторые из наиболее часто используемые роли и компоненты включены и настроены с рекомендуемыми для малого и среднего бизнеса. Можно настроить функции Windows Server Essentials или скрыть некоторые локальные функции. Если вы используете Windows Azure Pack, можно скачать шаблон коллекции для Windows Server Essentials Experience в Windows Server 2012 R2.  
  
-   **Упрощенная панель мониторинга** панель мониторинга Windows Server Essentials упрощает выполнение общих задач, таких как управление папки сервера, хранилищем сервера, резервного копирования и восстановления, пользователя или учетные записи групп, устройства, удаленного доступа и электронной почты. Клиентам малого и среднего бизнеса выполнять повседневные задачи без необходимости обращения в службу технической поддержки технической поддержки.  
  
-   **Расширения** программное обеспечение панель мониторинга Windows Server Essentials и Windows Server Essentials Connector расширяемы. Можно добавить собственную фирменную символику и службы интеграции, так что все клиенты имели одну точку входа для всех серверов и служб.  
  
-   **Монитор** доступна новая версия пакета мониторинга системного центра для мониторинга и управления несколькими серверами под управлением Windows Server Essentials. Чтобы загрузить пакет управления, в разделе [System Center Management пакет для Windows Server Essentials](https://www.microsoft.com/download/details.aspx?id=40809).  
  
##  <a name="BKMK_SupportedDeployment"></a>Поддерживаемые варианты развертывания  
  Можно развернуть Windows Server Essentials Experience в качестве контроллера домена в новой среде Active Directory; или его можно развернуть в существующей среде Active Directory входит в домен.  
  
 Рекомендуется сначала развернуть Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter и последующая установка роли Windows Server Essentials Experience. С помощью такого метода развертывания можно получить все функциональные возможности выпуска Windows Server Essentials, без каких-либо блокировок и ограничений.  
  

 Дополнительные сведения об установке Windows Server 2012 R2 с ролью Windows Server Essentials Experience см. в разделе [Установка и настройка Windows Server Essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).  


  
##  <a name="BKMK_SupportedToplogy"></a>Поддерживаемые топологии сети  
 Чтобы использовать Windows Server Essentials Experience с мобильного клиента, должна быть подключена VPN. Чтобы включить удаленный доступ к серверу из клиентов в роуминге, необходимо открыть порт 443 и порт 80 на сервере.  
  
 Ниже представлены две стандартные топологии сети со стороны сервера, а также может настройки VPN и удаленного веб-доступа:  
  
-   **Топология 1** (Это предпочтительный метод топологии, и помещает все серверы и диапазон VPN IP-адресов в одной подсети.):  
  
    -   Настройка сервера в отдельной виртуальной сети под устройством преобразования сетевых адресов (NAT).  
  
    -   Включение службы DHCP в виртуальной сети, либо назначьте статический IP-адрес для сервера.  
  
    -   Переадресация общего IP-порта 443 маршрутизатора на сетевой адрес сервера.  
  
    -   Разрешение сквозного режима VPN для порта 443.  
  
    -   Задайте пул адресов VPN IPv4 в том же диапазоне подсети, что и адрес сервера.  
  
    -   Назначение вторичным серверам статического IP-адреса в той же подсети, но вне пула адресов VPN.  
  
-   **Топология 2**:  
  
    -   Назначение серверу частного IP-адреса.  
  
    -   Разрешение доступа порту 443 на сервере к открытому порту 443 IP-адреса.  
  
    -   Разрешение сквозного режима VPN для порта 443.  
  
    -   Назначение различных диапазонов для пул адресов VPN IPv4 и адрес сервера.  
  
 В топологии 2 сценарии второго сервера не поддерживается, поскольку невозможно добавить другой сервер в том же домене.  
  
 Можно включить VPN во время автоматического развертывания с помощью сценария Windows PowerShell или его можно настроить с помощью мастера после начальной настройки.  
  
 Чтобы включить VPN с помощью Windows PowerShell, выполните следующую команду с правами администратора на сервере под управлением Windows Server Essentials и введите всю необходимую информацию.  
  
```  
##  
## To configure external domain and SSL certificate (if not yet done in unattended Initial Configuration).  
##  
  
$myExternalDomainName = 'remote.contoso.com';   ## corresponds to A or AAAA DNS record(s) that can be resolved on Internet and routed to the server  
$mySslCertificateFile = 'C:\ssl.pfx';   ## full path to SSL certificate file  
$mySslCertificatePassword = ConvertTo-SecureString  œAsPlainText  œForce '******';   ## password for private key of the SSL certificate  
$skipCertificateVerification = $true;   ## whether or not, skip verification for the SSL certificate  
  
Set-WssDomainNameConfiguration  œDomainName $myExternalDomainName  œCertificatePath $mySslCertificateFile  œCertificateFilePassword $mySslCertificatePassword  œNoCertificateVerification  
##  
## To install VPN with static IPv4 pool (and allow all existing users to establish VPN).  
##  
  
Install-WssVpnServer -IPv4AddressRange ('192.168.0.160','192.168.0.240') -ApplyToExistingUsers;  
  
```  
  
> [!NOTE]
>  Если невозможно предоставить VPN-подключение, прежде чем клиент получит права доступа к серверу, убедитесь, что порт сервера 3389 доступен через Интернет, чтобы клиента можно использовать протокол удаленного рабочего стола для подключения к серверу и его настройки.  
  
##  <a name="BKMK_CustomizeImage"></a>Настройка образа роли Windows Server Essentials Experience  
 Перед настройкой роли Windows Server Essentials Experience можно настроить образ. Дополнительные сведения о стандартном процессе Windows Server Sysprep см. в разделе [комплект средств для развертывания и оценки Windows](https://msdn.microsoft.com/library/hh825420.aspx). После подготовки образа с помощью средства Sysprep можно его использовать или запаковать в Install.wim для нового развертывания.  
  
 При использовании диспетчера виртуальных машин, можно создать шаблон, используя запущенный экземпляр. Этот процесс использует Sysprep для подготовки экземпляра, и она завершает работу компьютера. После сохранения шаблона в библиотеку, его можно использовать в случае с случая.  
  
 После установки роли Windows Server Essentials Experience можно настроить компоненты в Windows Server Essentials. Одним из самых важных настроек является **IsHosted** раздел реестра: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\Deployment\IsHosted**.  
  
 Если этот раздел имеет значение 0x1, некоторые локальные компоненты изменят поведение системы. Эти изменения включают в себя:  
  
-   **Архивация данных клиента** Архивация данных клиента будет отключена по умолчанию для вновь присоединившихся клиентских компьютеров.  
  
-   **Служба восстановления клиентских данных** служба восстановления клиентских данных будет отключена, а пользовательский Интерфейс будет скрыт из панели мониторинга.  
  
-   **Файл журнала** параметры истории файлов для только что созданные учетные записи пользователей не будет автоматически управлять сервером.  
  
-   **Резервное копирование сервера** службы архивации данных сервера будет отключена, а пользовательский Интерфейс резервной копии сервера будет скрыт из панели мониторинга.  
  
-   **Дисковые пространства** пользовательский для создания и управления дисковыми пространствами будет скрыт из панели мониторинга.  
  
-   **Повсеместный доступ** маршрутизатора и VPN будет пропущена по умолчанию при запуске мастера настройки повсеместного доступа.  
  
 Если вы хотите управлять поведением всех компонентов, можно задать соответствующий раздел реестра для каждого из них. Сведения о настройке раздела реестра см. [Настройка и развертывание Windows Server Essentials в Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx)  
  
##  <a name="BKMK_AutomateDeployment"></a>Автоматизация развертывания Windows Server Essentials Experience  
 Для автоматизации развертывания необходимо сначала развернуть операционную систему и последующая установка роли Windows Server Essentials Experience.  
  
-   Чтобы автоматически развернуть Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter, следуйте инструкциям в [комплект средств для развертывания и оценки Windows](https://msdn.microsoft.com/library/hh825420.aspx).  
  
-   Чтобы узнать, как установка роли Windows Server Essentials Experience с помощью Windows PowerShell, в разделе [Установка и настройка Windows Server Essentials](https://technet.microsoft.com/library/dn281793.aspx).  
  
> [!NOTE]
>  Убедитесь, что настройки часового пояса узла виртуальной машины и Windows Server Essentials Experience совпадают. В противном случае могут возникнуть ошибки. К ним относятся: начальная настройка сервера может не подходить для задачи, связанные с сертификатами, сертификат не работают в течение нескольких часов после установки роли Windows Server Essentials Experience и сведения об устройстве не обновляется правильно.  
  
 После развертывания необходимо использовать командлет Windows PowerShell **Get-WssConfigurationStatus** Чтобы проверить успешность начальной настройки. Должен вернуться один из следующих статусов: **Notstarted**, **FinishedWithWarning**, **под управлением**, **завершен**, **сбой**, или **PendingReboot**.  
  
 Сервер будет перезагружен во время начальной настройки. Если вам необходимо предотвратить автоматический перезапуск, чтобы добавить раздел реестра перед запуском начальной настройки можно использовать следующую команду:  
  
```  
New-ItemProperty "HKLM:\Software\Microsoft\Windows Server\Setup"Ã‚Â  -Name "WaitForReboot" -Value 1 -PropertyType "DWord" -Force -Confirm:$false  
  
```  
  
 После запуска начальной настройки, вы можете использовать **Get-WssConfigurationStatus** для проверки статуса начальной настройки и статус **PendingReboot**, можно перезапустить сервер.  
  
##  <a name="BKMK_Migrate"></a>Перенос данных из Windows Small Business Server на Windows Server Essentials Experience  
 Можно перенести данные с серверов под управлением Windows Small Business Server 2011, Windows Small Business Server 2008, Windows Small Business Server 2003 или Windows Server Essentials на сервер под управлением Windows Server Essentials. Просмотрите [переход на Windows Server Essentials](../migrate/Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md) миграции руководство по 2migrations локальными и выполнять пользовательскую настройку в соответствии со средой размещения.  
  
> [!NOTE]
>  Рекомендуется размещать исходный сервер и конечный сервер в той же подсети. Если это невозможно, необходимо убедиться в том:  
>   
>  -   Исходный сервер и сервер назначения можно получить доступ к друг с другом «о s внутренние DNS-имена.  
> -   Все необходимые порты открыты.  
  
 После миграции можно обновить лицензию для снятия ограничений и блокировки. Дополнительные сведения см. в разделе [переход с Windows Server Essentials на Windows Server 2012 Standard](https://technet.microsoft.com/library/jj247582.aspx).  
  
##  <a name="BKMK_PowerShell"></a>Общие задачи, с помощью Windows PowerShell  
 В этом разделе описаны некоторые общие задачи, которые можно выполнить с помощью Windows PowerShell.  
  
### <a name="enable-remote-web-access"></a>Включение удаленного веб-доступа  
 **Синтаксис**:  
  
 Enable-WssRemoteWebAccess [-SkipRouter] [-DenyAccessByDefault] [-ApplyToExistingUsers]  
  
 **Пример**:  
  
 $Enable-WssRemoteWebAccess œDenyAccessByDefault œApplyToExistingUsers  
  
 Эта команда включения удаленного веб-доступа с помощью автоматически настроенного маршрутизатора и изменить заданные по умолчанию права доступа для всех существующих пользователей.  
  
### <a name="add-user"></a>Добавление пользователя  
 **Синтаксис**:  
  
 Add-WssUser [-Имя] < string\ > [-пароль] < securestring\ > [-AccessLevel < string\ > {пользователя & #124; Администратор}] [-FirstName < string\ >] [-LastName < string\ >] [-AllowRemoteAccess] [-AllowVpnAccess] [< CommonParameters\ >]  
  
 **Пример**:  
  
 $password = ConvertTo-SecureString «Passw0rd!» -asplaintext œforce$ Add-WssUser-User2Test имя-пароль $password - Accesslevel администратора - FirstName User2 - LastName тестирования  
  
 Эта команда происходит добавление администратора с именем "User2Test" и паролем Passw0rd!.  
  
### <a name="add-server-folder"></a>Добавление папки сервера  
 **Синтаксис**:  
  
 Add-WssFolder [-Имя] < string\ > [-Path] < string\ > [[-Description] < string\ >] [-KeepPermissions] [< CommonParameters\ >]  
  
 **Пример**:  
  
 $Add-WssFolder-«MyTestFolder» имя-пути «C:\ServerFolders\MyTestFolder»  
  
 Данной команды происходит добавление папки сервера с именем MyTestFolder в указанном расположении.  
  
##  <a name="BKMK_EmailIntegration"></a>Интеграция электронной почты с Windows Server Essentials  
 Можно интегрировать режим Windows Server Essentials с Office 365 или размещенного Exchange Server. Если вы хотите предоставить пользователю использовал размещенного электронной почты, необходимо разработать надстройку для интеграции Windows Server Essentials Experience с вашей размещенной службой электронной почты. Дополнительные сведения см. в разделе [пакет SDK Windows Server Essentials](https://msdn.microsoft.com/library/gg513877.aspx).  
  
##  <a name="BKMK_Monitoring"></a>Мониторинг и управление с помощью стандартных средств  
 В этом разделе рассматриваются основные инструменты, доступные в Windows Server 2012 R2 для мониторинга и управления сервером.  
  
### <a name="group-policy"></a>Групповая политика  
  Режим Windows Server Essentials использует инструмент управления групповой политики в Windows Server 2012 R2 и предоставляет пользовательский интерфейс для настройки параметров перенаправления папок и безопасности.  
  
> [!NOTE]
>  В среде сервера Если включено перенаправление папок для профиля пользователя, он может увеличить время для конечного пользователя для входа, если обрабатывается большой объем данных.  
  
### <a name="system-center-monitoring-pack"></a>Пакет мониторинга системного центра  
 Пакет мониторинг System Center для Windows Server Essentials Experience мониторов системы оповещения о работоспособности для управления большим количеством серверов под управлением Windows Server Essentials, которые предназначены для организаций малого бизнеса. Дополнительные сведения см. в разделе [System Center Management пакет для Windows Server Essentials](https://www.microsoft.com/download/details.aspx?id=40809).  
  
### <a name="backup-and-restore"></a>Резервное копирование и восстановление  
  Windows Server 2012 R2 с Windows Server Essentials Experience позволяет архивировать данные сервера и клиентских компьютеров в сети.  
  
#### <a name="server-backup"></a>Резервное копирование сервера  
 Windows Server Essentials поддерживает два типа архивации сервера: локальную резервного копирования и облачные. Вы можете настроить эти параметры, если необходимо развернуть собственное решение архивации сервера.  
  
-   **Локальной копии** позволяет выполнять добавочную архивацию на уровне блоков на регулярной основе, на отдельный диск. Как поставщик услуг размещения может подключить виртуальный жесткий диск к виртуальной машине под управлением Windows Server Essentials и затем настроить архивацию сервера для этого виртуального жесткого диска. Виртуальный жесткий диск должен находиться на том же физическом диске виртуальной машине под управлением Windows Server Essentials.  
  
    > [!NOTE]
    >  Если у вас есть другие решения для архивации для виртуальных машин и вашим пользователям, чтобы увидеть Стандартная функция архивации данных сервера Windows Server Essentials не требуется, можно отключить его и удалить соответствующий пользовательский интерфейс из панели мониторинга. Дополнительные сведения см. в разделе [Настройка архивации сервера](https://technet.microsoft.com/library/dn293413.aspx) раздел [Настройка и развертывание Windows Server Essentials в Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx).  
  
-   **Резервное копирование Дистанционное** позволяет периодически архивировать данные сервера облачной службы. Можно загрузить и установить Microsoft Azure Backup интеграции модуля для Windows Server Essentials для эффективного использования Azure Backup, которая предоставляется корпорацией Майкрософт.  
  
     Дополнительные сведения см. в разделе интеграции Windows Azure Backup с помощью Windows Server Essentials в разделе [Управление архивацией сервера](../manage/Manage-Server-Backup-in-Windows-Server-Essentials.md).  
  
     Если вы или ваши пользователи предпочитают другую облачную службу, необходимо учитывать следующее.  
  
    -   Обновите пользовательский интерфейс панели мониторинга, чтобы он связан с вашей предпочитаемую облачную службу вместо службы по по умолчанию Azure Backup.  
  
    -   (Необязательно) Разработайте надстройку для панели мониторинга настроить и управлять облачной службой архивации.  
  
#### <a name="client-computer-backup"></a>Резервное копирование клиентских компьютеров  
 Windows Server Essentials Experience поддерживает два вида архивации данных клиента: полная архивация данных клиента и истории файлов.  
  
> [!NOTE]
>  Архивация данных клиента может повлиять на производительность, так как данные должны передаваться от клиента к серверу через VPN.  
  
##### <a name="full-client-backup"></a>Полная архивация данных клиента  
 Полная архивация данных клиента включена по умолчанию для всех клиентских устройств, подключенных к сети Windows Server Essentials. Полное резервное копирование информации и данных клиента и поддерживает дедупликацию данных. Данные архивации будут сохраняться на сервере под управлением Windows Server Essentials. Это позволяет клиенту сбоя извлечения данных из предыдущей точки восстановления.  
  
 Ниже перечислены некоторые аспекты полной компьютера архивации данных клиента  
  
-   **Производительность** первоначальная Архивация данных клиента может занять продолжительное в связи с большим объемом данных для загрузки.  
  
-   **Стабильность** иногда подключение к Интернету может быть нестабильным на стороне клиента. Позволяет Архивация данных клиента возобновляется автоматически и базы данных клиентской архивации создает контрольную точку каждый раз, когда резервное 40 ГБ данных. Это значение можно изменить можно уменьшить, если ожидается, что подключение к Интернету нестабильно.  
  
    -   Чтобы включить задание контрольную точку: на сервере, установите ключ реестра **HKLM\Software\Microsoft\Windows Server\Backup\GetCheckPointJobs** 1.  
  
    -   Изменение порогового значения контрольной точки: на клиенте, изменить **HKLM\Software\Microsoft\Windows Server\Backup\CheckPointThreshold** значения по умолчанию 40 ГБ.  
  
-   **Восстановление исходного состояния клиента** поскольку среда предустановки Windows не поддерживает VPN-подключение, восстановление исходного состояния клиента не поддерживается. Следует скрытия задачи службы восстановления клиента, выполнив действия, описанные в [Настройка и развертывание Windows Server Essentials в Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx).  
  
##### <a name="file-history"></a>История файлов  
 История файлов — это функция в Windows 8.1 и Windows 8 для архивации данных профиля (библиотеки, рабочий стол, контакты, Избранное) в сетевую папку. Можно централизованно управлять параметрами истории файлов всех компьютеров под управлением Windows 8.1 или Windows 8, подключенных к сети Windows Server Essentials. Данные архивации хранятся на сервере под управлением Windows Server Essentials. Следует скрытия задачи службы восстановления клиента, выполнив действия, описанные в [Настройка и развертывание Windows Server Essentials в Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx)  
  
### <a name="storage-management"></a>Управление хранилищем  
 Дисковые пространства позволяет объединять физический объем памяти разрозненных жестких дисков, динамически добавлять жесткие диски и создавать тома данных с заданными уровнями устойчивости. Для этого на узле или на виртуальной машине. Если вы хотите скрыть этот компонент в виртуальной машине под управлением Windows Server Essentials, следуйте инструкциям в [Настройка и развертывание Windows Server Essentials в Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx).  
  
##  <a name="BKMK_Scenarios"></a>Сценарии тестирования  
 Для успешного размещения рекомендуется проверить следующие сценарии:  
  

-   [Развертывание сервера](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ServerDeploy)  
  
-   [Конфигурация сервера](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ServerConfig2)  
  
-   [Управление сервером](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ServerManage)  
  
-   [Взаимодействие с клиентом](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ClientXP)  

  
###  <a name="BKMK_ServerDeploy"></a>Развертывание сервера  
 Можно проверить следующие сценарии развертывания сервера:  
  
-   Развертывание сервера под управлением Windows Server 2012 R2 в качестве контроллера домена в лабораторной среде и последующая установка роли Windows Server Essentials Experience.  
  
-   Развертывание сервера под управлением Windows Server 2012 R2 в лабораторной среде, присоедините сервер к существующему домену и последующая установка роли Windows Server Essentials Experience.  
  
-   Настройка образа Windows Server Essentials при необходимости.  
  
-   Автоматизация развертывания Windows Server Essentials с помощью файла автоматической установки и Windows PowerShell.  
  
-   Миграция локальных серверов под управлением Windows Small Business Server на размещенные сервера под управлением Windows Server Essentials.  
  
###  <a name="BKMK_ServerConfig2"></a>Конфигурация сервера  
 Можно проверить следующие сценарии конфигурации сервера:  
  
-   Настройте Повсеместный доступ (виртуальной частной сети, удаленный веб-доступ и DirectAccess).  
  
-   Настройте хранилище и папки сервера.  
  
-   Включите BranchCache.  
  
-   (Если применимо) Настройка архивации сервера, оперативной архивации, архивация данных клиента и файлов журнала.  
  
-   (Если применимо) Настройка и управление дисковыми пространствами.  
  
-   (Если применимо) Настройте интеграцию служб электронной почты (Office 365 и размещенного сервера Exchange Server).  
  
-   (Если применимо) Настройка интеграции с другими Microsoft online services.  
  
-   (Если применимо) Настройте сервер мультимедиа.  
  
###  <a name="BKMK_ServerManage"></a>Управление сервером  
 Можно проверить следующие сценарии конфигурации сервера:  
  
-   Управление пользователями и группами.  
  
-   Настройте и получайте электронные уведомления для оповещений.  
  
-   Запустите анализатор соответствия рекомендациям не ли ошибки или предупреждения.  
  
-   Настройте пакет System Center Operations Manager.  
  
-   Настройте функцию восстановления сервера в случае сбоя в операционной системе.  
  
###  <a name="BKMK_ClientXP"></a>Взаимодействие с клиентом  
 Можно проверить следующие сценарии конечного пользователя:  
  
-   Развертывание клиентов через Интернет (ПК или Mac операционных систем).  
  
-   Используйте панель запуска на клиентском компьютере для доступа к общим папкам.  
  
-   Доступ к ресурсам сервера через службу удаленного доступа с помощью различных устройств (ПК, телефоне и планшете).  
  
-   Доступ к приложение My Server для Windows Phone.  
  
-   (Если применимо) Доступ к истории файлов, архивация данных клиента и восстановления и перенаправление папок.  
  
-   (Если применимо) Проверьте Интеграция служб электронной почты.  
  
##  <a name="BKMK_Support"></a>Сведения о поддержке  
 Можно загрузить Windows Server Essentials разработки программного обеспечения Kit (SDK) и оценки Windows Server Essentials и комплект средств для развертывания (ADK):  
  
-   [Пакет средств разработки программного обеспечения Windows Server Essentials](https://msdn.microsoft.com/library/gg513877.aspx)SDK  
  
-   [Настройка и развертывание Windows Server Essentials в Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx)  
  
## <a name="see-also"></a>См. также:  
  
-   [Новые возможности Windows Server Essentials](../get-started/what-s-new.md)  

-   [Установка Windows Server Essentials](Install-Windows-Server-Essentials.md)  

-   [Начало работы с Windows Server Essentials](../get-started/get-started.md)
