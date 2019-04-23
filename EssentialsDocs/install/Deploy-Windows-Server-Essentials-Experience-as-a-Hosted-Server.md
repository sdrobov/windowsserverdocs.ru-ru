---
title: Развертывание режима Windows Server Essentials в качестве размещенного сервера
description: Описывает способ использования Windows Server Essentials
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
ms.openlocfilehash: b44b395a39a53194b73a0d503c2310edcbe53a2c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59876075"
---
# <a name="deploy-windows-server-essentials-experience-as-a-hosted-server"></a>Развертывание режима Windows Server Essentials в качестве размещенного сервера

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Данный документ содержит информацию, предназначенную для поставщиков услуг размещения, которые планируют развернуть Microsoft Windows Server 16 с Windows Server Essentials Experience (Далее Windows Server Essentials в оставшейся части документа) установленной ролью в своих лабораториях и Вы собираетесь предлагать своим клиентам Windows Server Essentials Experience как услуга. Данный документ содержит следующие разделы:  
  

-   [Обзор Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_WSEEOverview)  
  
-   [Преимущества размещения Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Benefits)  
  
-   [Поддерживаемые варианты развертывания](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_SupportedDeployment)  
  
-   [Поддерживаемые топологии сети](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_SupportedToplogy)  
  
-   [Настройка образа Windows Server Essentials Experience роли](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_CustomizeImage)  
  
-   [Автоматизация развертывания Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_AutomateDeployment)  
  
-   [Перенос данных из Windows Small Business Server на Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Migrate)  
  
-   [Общие задачи с помощью Windows PowerShell](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_PowerShell)  
  
-   [Интеграция электронной почты с Windows Server Essentials](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_EmailIntegration)  
  
-   [Мониторинг и управление им с помощью стандартных средств](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Monitoring)  
  
-   [Сценарии тестирования](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Scenarios)  
  
-   [Сведения о поддержке](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Support)  

-   [Обзор Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_WSEEOverview)  
  
-   [Преимущества размещения Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Benefits)  
  
-   [Поддерживаемые варианты развертывания](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_SupportedDeployment)  
  
-   [Поддерживаемые топологии сети](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_SupportedToplogy)  
  
-   [Настройка образа Windows Server Essentials Experience роли](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_CustomizeImage)  
  
-   [Автоматизация развертывания Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_AutomateDeployment)  
  
-   [Перенос данных из Windows Small Business Server на Windows Server Essentials Experience](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Migrate)  
  
-   [Общие задачи с помощью Windows PowerShell](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_PowerShell)  
  
-   [Интеграция электронной почты с Windows Server Essentials](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_EmailIntegration)  
  
-   [Мониторинг и управление им с помощью стандартных средств](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Monitoring)  
  
-   [Сценарии тестирования](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Scenarios)  
  
-   [Сведения о поддержке](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_Support)  

  
##  <a name="BKMK_WSEEOverview"></a> Обзор Windows Server Essentials Experience  
 Windows Server Essentials Experience — это роль сервера, который доступен в Windows Server 2012 R2 Standard и Windows Server 2012 R2 Datacenter. При установке роли Windows Server Essentials Experience на сервере под управлением Windows Server 2012 R2, клиент можно воспользоваться преимуществами все функции, доступные в Windows Server Essentials без ограничений и блокировок. Windows Server Essentials Experience позволяет следующие перекрестные решения для малого и среднего бизнеса:  
  
-   **Хранение и защита данных** можно хранить клиента «данных s™ в центральном расположении и защитить данные сервера и клиента путем создания резервной копии сервера и клиентских компьютеров (не более 75) в сети.  
  
-   **Управление пользователями**. Управление пользователями и группами пользователей осуществляется через упрощенную панель мониторинга сервера. Кроме того интеграция с Microsoft Azure Active Directory (Azure AD) обеспечивает простой доступ данных служб Microsoft online Services (например, Office 365, Exchange Online и SharePoint Online) для пользователей с помощью учетных данных домена.  
  
-   **Интеграция служб** можно интегрировать сервер с Microsoft online services (например, Office 365, SharePoint Online и Microsoft Azure Backup). Можно также интегрировать сервер с вашими службами и службами сторонних поставщиков.  
  
-   **Повсеместный доступ**. Клиент имеет доступ к серверу, компьютерам сети и данным с любого устройства и из любой точки, где есть доступ к Интернету. Удаленный веб-доступ позволяет получить доступ к приложениям и данным с помощью простого и оптимизированного под сенсорные дисплеи браузерного интерфейса. Приложение My Server позволяет получать доступ к данным из Windows Phone или приложения Microsoft Store.  
  
-   **Потоковая передача мультимедиа** Если установить пакет мультимедиа на сервере с Windows Server Essentials Experience включен, конечный пользователь может сохранять музыку, видео и фотографии в общих папках, а затем доступ к этим медиафайлам с сетевых компьютеров или Удаленный веб-доступ.  
  
-   **Наблюдение за работоспособностью системы**. Можно отслеживать работоспособность сети и получать настраиваемые отчеты.  
  
##  <a name="BKMK_Benefits"></a> Преимущества размещения Windows Server Essentials Experience  
  Windows Server Essentials Experience — это роль в Windows Server, можно повторно использовать уже существующую платформу развертывания и управления в Windows Server для развертывания и настройки роли Windows Server Essentials Experience. Где находится роль Windows Server Essentials Experience обеспечивает следующие преимущества:  
  
-   **Упрощенная схема развертывания** путем простой активации роли Windows Server Essentials Experience, некоторые из наиболее часто используемые роли и компоненты можно включить и настроить в соответствии с рекомендуемыми для малого и среднего бизнеса. Можно настроить функции Windows Server Essentials или скрыть некоторые локальные функции. Если вы используете пакет Windows Azure, можно скачать шаблон коллекции для Windows Server Essentials Experience в Windows Server 2012 R2.  
  
-   **Упрощенная панель мониторинга**. Панель мониторинга Windows Server Essentials упрощает выполнение общих задач, таких как управление серверными папками и их хранение, резервное копирование и восстановление, управление учетными записями пользователей или групп пользователей, удаленным доступом и электронной почтой. Это дает возможность клиентам малого и среднего бизнеса выполнять повседневные задачи без необходимости обращения в службу технической поддержки.  
  
-   **Расширяемость** . Панель мониторинга Windows Server Essentials и программное обеспечение Windows Server Essentials Connector расширяемы. Вы можете добавить свою собственную фирменную интеграцию, чтобы все клиенты имели одну точку входа для серверов и служб.  
  
-   **Мониторинг**. Новая версия пакета мониторинга системного центра позволяет управлять несколькими серверами под управлением Windows Server Essentials. Чтобы загрузить пакет управления, см. в разделе [System Center Management Pack для Windows Server Essentials](https://www.microsoft.com/download/details.aspx?id=40809).  
  
##  <a name="BKMK_SupportedDeployment"></a> Поддерживаемые варианты развертывания  
  Можно развернуть Windows Server Essentials Experience в качестве контроллера домена в новой среде Active Directory; или его можно развернуть в существующей среде Active Directory входит в домен.  
  
 Рекомендуется сначала развернуть Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter и последующая установка роли Windows Server Essentials Experience. Этот метод развертывания обеспечивает все функциональные возможности Windows Server Essentials без каких-либо ограничений и блокировки.  
  

 Дополнительные сведения об установке Windows Server 2012 R2 с ролью Windows Server Essentials Experience см. в разделе [Установка и настройка Windows Server Essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).  


  
##  <a name="BKMK_SupportedToplogy"></a> Поддерживаемые топологии сети  
 Чтобы использовать режим Windows Server Essentials с перемещаемого клиентского компьютера, необходимо активировать VPN. Чтобы включить удаленный доступ к серверу для мобильных клиентов, необходимо открыть на сервере порт 443 и порт 80.  
  
 Ниже представлены две стандартные топологии сети на стороне сервера, а также настройки VPN и удаленного веб-доступа.  
  
-   **Топология 1** (это предпочтительный метод топологии, который помещает все серверы и диапазон IP-адресов VPN в одной подсети).  
  
    -   Настройка сервера в отдельной виртуальной сети с помощью устройства преобразования сетевых адресов (NAT).  
  
    -   Включение службы DHCP в виртуальной сети, либо назначение статического IP-адреса для сервера.  
  
    -   Переадресация общего IP-порта 443 маршрутизатора на сетевой адрес сервера.  
  
    -   Разрешение сквозного режима VPN для порта 443.  
  
    -   Установка пула IPv4-адресов VPN в том же диапазоне подсети, что и адрес сервера.  
  
    -   Назначение вторичным серверам статического IP-адреса в том же диапазоне подсети, но вне пула VPN-адресов.  
  
-   **Топология 2**.  
  
    -   Назначение серверу частного IP-адреса.  
  
    -   Разрешение доступа порту 443 на сервере к открытому порту 443 IP-адреса.  
  
    -   Разрешение сквозного режима VPN для порта 443.  
  
    -   Назначение различных диапазонов IPv4-адресов для VPN и для адреса сервера.  
  
 В топологии 2 не поддерживаются функции вторичного сервера, поскольку невозможно добавить другой сервер в том же домене.  
  
 Можно включить VPN во время автоматического развертывания с помощью сценария Windows PowerShell , либо настроить его с помощью мастера настройки после начальной установки параметров.  
  
 Чтобы включить VPN с помощью Windows PowerShell, выполните следующую команду с правами администратора на сервере под управлением Windows Server Essentials и введите все необходимые сведения.  
  
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
>  Если невозможно предоставить VPN-подключение до того как клиент получит права доступа к серверу, убедитесь в том, что порт сервера 3389 открыт для доступа через Интернет, чтобы клиент смог использовать протокол удаленного доступа к рабочему столу для подключения к серверу и его настройки.  
  
##  <a name="BKMK_CustomizeImage"></a> Настройка образа Windows Server Essentials Experience роли  
 Перед настройкой роли Windows Server Essentials Experience можно выполнить настройку ее образа. Дополнительные сведения о стандартном процессе Windows Server Sysprep см. в разделе [Комплект средств для развертывания и оценки Windows](https://msdn.microsoft.com/library/hh825420.aspx). После подготовки образа с помощью средства Sysprep можно его использовать или запаковать в файл Install.wim для последующего развертывания.  
  
 При использовании диспетчера виртуальных машин можно создать шаблон на основе запущенного сервера. Для подготовки работающей копии используется Sysprep, который завершает работу компьютера. После сохранения шаблона в библиотеку можно использовать его при необходимости.  
  
 После установки роли Windows Server Essentials Experience, можно настроить компоненты в Windows Server Essentials. Одной из самых важных настроек является раздел реестра **IsHosted**: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\Deployment\IsHosted**.  
  
 Если этот раздел имеет значение 0x1, некоторые локальные компоненты изменят поведение системы. Такие изменения включают в себя следующее:  
  
-   **Архивация данных клиента** . По умолчанию архивация данных клиента отключена для вновь присоединившихся клиентских компьютеров.  
  
-   **Служба восстановления клиентских данных** Служба восстановления клиентских данных will be disabled, and the UI will be hidden from the Dashboard.  
  
-   **История файлов**. Настройки истории файлов для учетных записей новых пользователей не будут автоматически управляться сервером.  
  
-   **Архивация данных сервера** Архивация данных сервера service will be disabled, and the Архивация данных сервера UI will be hidden from the Dashboard.  
  
-   **Дисковые пространства**. Пользовательский интерфейс службы управления дисковыми пространствами будет скрыт из панели мониторинга.  
  
-   **Повсеместный доступ**. Установка параметров маршрутизатора и VPN будет по умолчанию пропущена при запуске мастера настройки повсеместного доступа.  
  
 Если вам необходимо управлять поведением всех компонентов, вы можете установить для каждого из них соответствующий раздел реестра. Дополнительные сведения о настройке раздела реестра см. в разделе [Настройка и развертывание Windows Server Essentials в Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx).  
  
##  <a name="BKMK_AutomateDeployment"></a> Автоматизация развертывания Windows Server Essentials Experience  
 Чтобы автоматизировать развертывание, необходимо сначала развернуть операционную систему, а затем установить роль Windows Server Essentials Experience.  
  
-   Чтобы автоматически развернуть Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter, следуйте инструкциям в [Windows Assessment and Deployment Kit](https://msdn.microsoft.com/library/hh825420.aspx).  
  
-   Чтобы узнать, как установка роли Windows Server Essentials Experience с помощью Windows PowerShell, см. в разделе [Установка и настройка Windows Server Essentials](https://technet.microsoft.com/library/dn281793.aspx).  
  
> [!NOTE]
>  Убедитесь, что настройки часового пояса узла виртуальной машины и Windows Server Essentials Experience совпадают. В противном случае могут возникнуть ошибки, К ним относятся: начальной настройки сервера может не подходить для сертификатов связанных задач, сертификат может не работать в течение нескольких часов после установки роли Windows Server Essentials Experience, а не обновит сведения об устройстве правильно.  
  
 После развертывания необходимо использовать командлет Windows PowerShell **Get-WssConfigurationStatus** , чтобы проверить успешность начальной настройки. Должен вернуться один из следующих статусов: **Notstarted**, **FinishedWithWarning**, **Running**, **Finished**, **Failed** либо **PendingReboot**.  
  
 Во время начальной настройки сервер будет перезапущен. Если необходимо предотвратить автоматический перезапуск сервера, перед запуском начальной настройки можно использовать следующую команду для добавления раздела реестра:  
  
```  
New-ItemProperty "HKLM:\Software\Microsoft\Windows Server\Setup"Ã‚Â  -Name "WaitForReboot" -Value 1 -PropertyType "DWord" -Force -Confirm:$false  
  
```  
  
 После запуска начальной настройки можно использовать **Get-WssConfigurationStatus** для проверки статуса начальной настройки; как только вы получите статус **PendingReboot**, можно перезапустить сервер.  
  
##  <a name="BKMK_Migrate"></a> Перенос данных из Windows Small Business Server на Windows Server Essentials Experience  
 Можно перенести данные с серверов под управлением Windows Small Business Server 2011, Windows Small Business Server 2008, Windows Small Business Server 2003 или Windows Server Essentials на сервер под управлением Windows Server Essentials. Просмотрите [миграции на Windows Server Essentials](../migrate/Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md) миграции руководить для локальной 2migrations и выполнять пользовательскую настройку в соответствии с имеющейся средой внешнего размещения.  
  
> [!NOTE]
>  Рекомендуется размещать исходный сервер и сервер назначения в одной подсети. Если это невозможно, необходимо обеспечить выполнение следующих условий:  
>   
>  -   Исходный сервер и конечный сервер могут обращаться друг к другу «™ s внутренние DNS-имена.  
> -   Все необходимые порты должны быть открыты.  
  
 После переноса данных можно обновить лицензию для снятия ограничений и блокировки. Дополнительные сведения см. в разделе [переход с Windows Server Essentials на Windows Server 2012 Standard](https://technet.microsoft.com/library/jj247582.aspx).  
  
##  <a name="BKMK_PowerShell"></a> Общие задачи с помощью Windows PowerShell  
 В данном разделе описаны некоторые общие задачи, которые можно выполнять с помощью Windows PowerShell.  
  
### <a name="enable-remote-web-access"></a>Подключение удаленного веб-доступа  
 **Синтаксис**:  
  
 Enable-WssRemoteWebAccess [-SkipRouter] [-DenyAccessByDefault] [-ApplyToExistingUsers]  
  
 **Пример**:  
  
 $Enable-WssRemoteWebAccess  œDenyAccessByDefault  œApplyToExistingUsers  
  
 Данная команда позволяет включить удаленный веб-доступ с помощью автоматически настроенного маршрутизатора и изменить установленные по умолчанию права доступа для всех существующих пользователей.  
  
### <a name="add-user"></a>Добавить пользователя  
 **Синтаксис**:  
  
 Add-WssUser [-имя] < строка\> [-пароль] < securestring\> [-AccessLevel < строка\> {пользователя &#124; администратора}] [-FirstName < строка\>] [-LastName < строка\>] [- AllowRemoteAccess] [-AllowVpnAccess] [< CommonParameters\>]  
  
 **Пример**:  
  
 $password = ConvertTo-SecureString "Passw0rd!" -asplaintext  œforce$Add-WssUser -Name User2Test -Password $password -Accesslevel Administrator -FirstName User2 -LastName Test  
  
 Данной команды происходит добавление администратора с именем "User2Test" с паролем Passw0rd!.  
  
### <a name="add-server-folder"></a>Добавление папки сервера  
 **Синтаксис**:  
  
 Add-WssFolder [-имя] < строка\> [-путь] < строка\> [[-Описание] < строка\>] [-KeepPermissions] [< CommonParameters\>]  
  
 **Пример**:  
  
 $Add-WssFolder -Name "MyTestFolder" -Path "C:\ServerFolders\MyTestFolder"  
  
 Эта команда будет добавить папку сервера с именем MyTestFolder в указанном расположении.  
  
##  <a name="BKMK_EmailIntegration"></a> Интеграция электронной почты с Windows Server Essentials  
 Вы можете интегрировать Windows Server Essentials Experience с Office 365 или размещенный сервер Exchange Server. Если требуется, чтобы клиент использовал услуги размещенной службы электронной почты, необходимо выполнить надстройку для интеграции Windows Server Essentials Experience с размещенной службой электронной почты. Дополнительные сведения см. в статье [Пакет SDK для Windows Server](https://msdn.microsoft.com/library/gg513877.aspx).  
  
##  <a name="BKMK_Monitoring"></a> Мониторинг и управление им с помощью стандартных средств  
 В этом разделе рассматриваются основные инструменты, доступные в Windows Server 2012 R2 для отслеживания и управления сервером.  
  
### <a name="group-policy"></a>Групповая политика  
  Windows Server Essentials Experience использует собственную поддержку групповой политики в Windows Server 2012 R2 и предоставляет пользовательский интерфейс для настройки перенаправления папок и параметров безопасности.  
  
> [!NOTE]
>  Если в размещенной среде подключена функция переадресации папок для профиля пользователя, большой объем обрабатываемых данных может увеличить время вхождения на сервер для конечного пользователя.  
  
### <a name="system-center-monitoring-pack"></a>Пакет мониторинга системного центра  
 System Center Monitoring Pack для Windows Server Essentials Experience мониторов системы оповещения о работоспособности, которые помогают управлять большим количеством серверов под управлением Windows Server Essentials, предназначены для организаций малого бизнеса. Дополнительные сведения см. в разделе [System Center Management Pack для Windows Server Essentials](https://www.microsoft.com/download/details.aspx?id=40809).  
  
### <a name="backup-and-restore"></a>Резервное копирование и восстановление  
  Windows Server 2012 R2 с Windows Server Essentials Experience позволяет архивировать сервер и клиентские компьютеры в сети.  
  
#### <a name="server-backup"></a>Архивация данных сервера  
 Windows Server Essentials поддерживает два типа архивации сервера: локальную и удаленную. Если необходимо развернуть собственное решение архивации сервера, вы можете изменить настройки этих параметров.  
  
-   **Локальная архивация** . Позволяет выполнить регулярную инкрементную архивацию на уровне блока на отдельный диск. В качестве поставщика услуг размещения вы можете подключить виртуальный жесткий диск к виртуальной машине под управлением Windows Server Essentials, а затем настроить архивацию сервера для этого виртуального жесткого диска. Виртуальный жесткий диск должен располагаться на физическом жестком диске, на котором не запущена виртуальная машина под управлением Windows Server Essentials.  
  
    > [!NOTE]
    >  Если у вас имеются другие средства резервного копирования для виртуальных машин и вашим пользователям не требуется стандартная функция архивации данных сервера Windows Server Essentials, вы можете отключить ее и удалить соответствующий пользовательский интерфейс из панели мониторинга. Дополнительные сведения см. в подразделе [Настройка архивации сервера](https://technet.microsoft.com/library/dn293413.aspx) раздела [Настройка и развертывание Windows Server Essentials в Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx).  
  
-   **Удаленная архивация** . Позволяет регулярно архивировать данные сервера через использование облачной службы. Можно загрузить и установить Microsoft Azure Backup интеграции модуля для Windows Server Essentials использовать резервное копирование Azure, предоставляемой корпорацией Майкрософт.  
  
     Дополнительные сведения см. в разделе интеграции Windows Azure Backup с помощью Windows Server Essentials раздел [Manage Server Backup](../manage/Manage-Server-Backup-in-Windows-Server-Essentials.md).  
  
     Если вы или ваши пользователи пользуются службами других поставщиков облачных услуг, необходимо выполнить следующие действия:  
  
    -   Обновите пользовательский интерфейс панели мониторинга, поэтому, чтобы указать предпочитаемую облачную службу вместо службы по умолчанию Azure Backup.  
  
    -   (Необязательно.) Разработать надстройку для панели мониторинга, необходимую для настройки облачной службы архивации и управления ею.  
  
#### <a name="client-computer-backup"></a>Архивация клиентских компьютеров  
 Windows Server Essentials Experience поддерживает два вида архивации данных компьютера клиента: полная архивация данных и история файлов.  
  
> [!NOTE]
>  Архивация данных клиента может повлиять на работоспособность системы, поскольку данные клиента передаются на сервер через VPN.  
  
##### <a name="full-client-backup"></a>Полная архивация данных клиента  
 Полная архивация данных включена по умолчанию для всех клиентских устройств, подключенных к сети Windows Server Essentials. Этот вид архивации выполняет полное резервное копирование информации и данных клиента и поддерживает дедупликацию данных. Резервные копии данных будут храниться на сервере под управлением Windows Server Essentials. Это позволяет клиенту восстановить данные из предыдущей точки восстановления при возникновении сбоя в системе.  
  
 Ниже представлена некоторая важная информация касательно полной архивации данных клиентского компьютера:  
  
-   **Производительность** . Первоначальная архивация данных клиента может занять продолжительное время в связи с большим объемом данных для загрузки.  
  
-   **Стабильность** . Иногда подключение к Интернету со стороны клиента может быть нестабильным. Архивация данных клиента предназначен возобновляется автоматически, и базы данных клиентской архивации создает контрольную точку каждый раз создается резервная копия 40 ГБ данных. Это значение можно уменьшить, если подключение к Интернету нестабильно.  
  
    -   Включение процесса создания контрольной точки На сервере в разделе реестра **HKLM\Software\Microsoft\Windows Server\Backup\GetCheckPointJobs** задайте значение 1.  
  
    -   Изменение порогового значения контрольной точки На стороне клиента, измените **HKLM\Software\Microsoft\Windows Server\Backup\CheckPointThreshold** со значения по умолчанию в 40 ГБ.  
  
-   **Восстановление исходного состояния клиентского компьютера** . Поскольку среда предустановки Windows не поддерживает VPN-подключение, восстановление исходного состояния клиентского компьютера невозможно. Для скрытия задачи службы восстановления данных клиента необходимо выполнить действия, описанные в разделе [Настройка и развертывание Windows Server Essentials на Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx).  
  
##### <a name="file-history"></a>История файлов  
 История файлов — это функция ОС Windows 8.1 и Windows 8, позволяющая архивировать данные профиля (библиотеки, рабочий стол, контакты, избранное) в общую сетевую папку. Можно централизованно управлять параметрами истории файлов всех компьютеров под управлением Windows 8.1 или Windows 8, подключенных к сети Windows Server Essentials. Данные архивации хранятся на сервере под управлением Windows Server Essentials. Для скрытия задачи службы восстановления данных клиента необходимо выполнить действия, описанные в разделе [Настройка и развертывание Windows Server Essentials на Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx).  
  
### <a name="storage-management"></a>Управление хранилищами  
 Дисковые пространства позволяют объединить физический объем памяти разрозненных жестких дисков, динамически добавлять жесткие диски и создавать тома данных с заданными уровнями устойчивости. Можно выполнять это на ведущем узле или на виртуальной машине. Если вы хотите скрыть этот компонент в виртуальной машине под управлением Windows Server Essentials, следуйте инструкциям в разделе [Настройка и развертывание Windows Server Essentials в Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx).  
  
##  <a name="BKMK_Scenarios"></a> Сценарии тестирования  
 Для успешного размещения рекомендуется провести проверку следующих сценариев:  
  

-   [Развертывание сервера](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ServerDeploy)  
  
-   [Конфигурация сервера](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ServerConfig2)  
  
-   [Управление сервером](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ServerManage)  
  
-   [Взаимодействие с клиентом](Deploy-Windows-Server-Essentials-Experience-as-a-Hosted-Server.md#BKMK_ClientXP)  

  
###  <a name="BKMK_ServerDeploy"></a> Развертывание сервера  
 Можно проверить следующие сценарии развертывания сервера:  
  
-   Развертывание сервера под управлением Windows Server 2012 R2 в качестве контроллера домена в лабораторной среде и последующая установка роли Windows Server Essentials Experience.  
  
-   Развертывание сервера под управлением Windows Server 2012 R2 в лабораторной среде, присоединить этот сервер к существующему домену и последующая установка роли Windows Server Essentials Experience.  
  
-   Настройка образа Windows Server Essentials при необходимости.  
  
-   Автоматизация развертывания Windows Server Essentials с помощью файла установки и Windows PowerShell.  
  
-   Миграция локальных серверов под управлением Windows Small Business Server на размещенные сервера под управлением Windows Server Essentials.  
  
###  <a name="BKMK_ServerConfig2"></a> Конфигурация сервера  
 Можно проверить следующие сценарии конфигурации сервера:  
  
-   Настройте повсеместный доступ (к виртуальной частной сети, удаленный веб-доступ и DirectAccess).  
  
-   Настройте хранилище и папки сервера.  
  
-   Включите BranchCache.  
  
-   (Если применимо.) Настройте параметры архивации сервера, веб-архивации, архивации данных клиента и истории файлов.  
  
-   (Если применимо) настройте и управляйте дисковыми пространствами.  
  
-   (Если применимо) Настройте интеграцию служб электронной почты (Office 365 и размещенного сервера Exchange).  
  
-   (Если применимо.) Настройте интеграции с другими интернет-службами Майкрософт.  
  
-   (Если применимо) настройте сервер мультимедиа.  
  
###  <a name="BKMK_ServerManage"></a> Управление сервером  
 Можно проверить следующие сценарии конфигурации сервера:  
  
-   Управление пользователями и группами.  
  
-   Настройте и получайте электронные уведомления для оповещений.  
  
-   Запустите анализатор соответствия рекомендациям и убедитесь в отсутствии ошибок и предупреждений.  
  
-   Настройте пакет управления системным центром.  
  
-   Настройте функцию восстановления сервера в случае сбоя в операционной системе.  
  
###  <a name="BKMK_ClientXP"></a> Взаимодействие с клиентом  
 Можно проверить следующие сценарии взаимодействия с конечным пользователем:  
  
-   Развертывание клиентских компьютеров через Интернет (ПК или Mac).  
  
-   Использование панели запуска на клиентском компьютере для доступа к общим папкам.  
  
-   Доступ к ресурсам сервера через службу удаленного доступа с помощью различных устройств (ПК, телефон, планшет).  
  
-   Доступ к приложению "Мой сервер" для Windows Phone.  
  
-   (Если применимо.) Доступ к истории файлов, архивации и восстановлению данных клиента, переадресации папок.  
  
-   (Если применимо.) Проверка интеграции служб электронной почты.  
  
##  <a name="BKMK_Support"></a> Сведения о поддержке  
 Можно загрузить Windows Server Essentials Software Development Kit (SDK) и Windows Server Essentials и оценки Deployment Kit (ADK):  
  
-   [Пакет средств разработки программного обеспечения Windows Server Essentials](https://msdn.microsoft.com/library/gg513877.aspx)SDK  
  
-   [Настройка и развертывание Windows Server Essentials в Windows Server 2012 R2](https://technet.microsoft.com/library/dn293241.aspx)  
  
## <a name="see-also"></a>См. также  
  
-   [Новые возможности в Windows Server Essentials](../get-started/what-s-new.md)  

-   [Установка Windows Server Essentials](Install-Windows-Server-Essentials.md)  

-   [Начало работы с Windows Server Essentials](../get-started/get-started.md)
