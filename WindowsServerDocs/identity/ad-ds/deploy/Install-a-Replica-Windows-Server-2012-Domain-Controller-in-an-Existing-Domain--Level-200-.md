---
ms.assetid: e6da5984-d99d-4c34-9c11-4a18cd413f06
title: "Установка контроллера домена реплики Windows Server 2012 в существующем домене (уровень 200)"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: e3151a8beee2870ecc747a64241df9d562ad4cc2
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="install-a-replica-windows-server-2012-domain-controller-in-an-existing-domain-level-200"></a>Установка контроллера домена реплики Windows Server 2012 в существующем домене (уровень 200)

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе рассматриваются действия, необходимые для обновления существующего леса или домена до Windows Server 2012 с помощью диспетчера сервера или Windows PowerShell. Здесь показано, как добавить контроллеры домена под управлением Windows Server 2012 в существующий домен.  
  
-   [Реплика процесс обновления и](../../ad-ds/deploy/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-.md#BKMK_Workflow)  
  
-   [Обновление и Добавление реплики Windows PowerShell](../../ad-ds/deploy/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-.md#BKMK_PS)  
  
-   [Развертывания](../../ad-ds/deploy/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-.md#BKMK_Dep)  
  
## <a name="BKMK_Workflow"></a>Реплика процесс обновления и  
Схеме ниже показан процесс настройки доменных служб Active Directory, если вы ранее установили роль Доменных служб Active Directory и запустили Active Directory мастер настройки доменных служб с помощью диспетчера сервера для создания нового контроллера домена в существующем домене.  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/adds_forestupgrade.png)  
  
## <a name="BKMK_PS"></a>Обновление и Добавление реплики Windows PowerShell  
  
|||  
|-|-|  
|**Командлет ADDSDeployment**|Аргументы (**Полужирный** требуются аргументы. *Курсивом* аргументов можно указать с помощью Windows PowerShell или мастера настройки AD DS.)|  
|Install-AddsDomainController|-SkipPreChecks<br /><br />***-DomainName***<br /><br />*-SafeModeAdministratorPassword*<br /><br />*-SiteName*<br /><br />*-ADPrepCredential*<br /><br />-ApplicationPartitionsToReplicate<br /><br />*-AllowDomainControllerReinstall*<br /><br />-Подтверждения<br /><br />*-CreateDNSDelegation*<br /><br />***-Credential***<br /><br />-CriticalReplicationOnly<br /><br />*-DatabasePath*<br /><br />*-DNSDelegationCredential*<br /><br />-Force<br /><br />*-InstallationMediaPath*<br /><br />*-InstallDNS*<br /><br />*-LogPath*<br /><br />-MoveInfrastructureOperationMasterRoleIfNecessary<br /><br />-NoDnsOnNetwork<br /><br />*-NoGlobalCatalog*<br /><br />-Norebootoncompletion<br /><br />*-ReplicationSourceDC*<br /><br />-SkipAutoConfigureDNS<br /><br />-SiteName<br /><br />*-SystemKey*<br /><br />*-SYSVOLPath*<br /><br />*-UseExistingAccount*<br /><br />*-Whatif*|  
  
> [!NOTE]  
> **-Credential** только требуется, если вы уже вошли на является членом группы "Администраторы предприятия" и "Администраторы схемы" (при обновлении леса) или группы администраторов домена (Если вы добавляете новый контроллер домена в существующий домен).  
  
## <a name="BKMK_Dep"></a>Развертывания  
  
### <a name="deployment-configuration"></a>Конфигурация развертывания  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeDeployConfig.png)  
  
Диспетчер серверов начинает повышение роли каждого контроллера домена с **конфигурации развертывания** страницы. Оставшиеся параметры и обязательные поля меняются на этой странице и последующих страницах в зависимости от того, какая операция развертывания выбрана.  
  
Чтобы обновить существующий лес или добавить контроллер домена с возможностью записи в существующий домен, щелкните **добавить контроллер домена в существующий домен** и нажмите кнопку **выберите** для **указать сведения о домене для данного домена**. Диспетчер серверов запрашивает действующие учетные данные при необходимости.  
  
Обновление леса требуются учетные данные, которые включают членство в группах "Администраторы схемы" и "Администраторы предприятия" в Windows Server 2012. Мастер настройки доменных служб Active Directory предлагает позже, если у текущих учетных данных нет соответствующих разрешений или членства в группах.  
  
Автоматическое выполнение процесса Adprep — это единственное различие между добавлением контроллера домена в существующий домен Windows Server 2012 и домен, где контроллеры домена работают под управлением более ранней версии Windows Server.  
  
Командлет ADDSDeployment конфигурации развертывания и аргументы приведены ниже.  
  
```  
Install-AddsDomainController  
-domainname <string>  
-credential <pscredential>  
```  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeCreds.png)  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeSelectDomain.png)  
  
На каждой странице, некоторые из которых проводятся повторно позднее как отдельные проверки предварительных требований выполняются определенные тесты. Например если выбранный домен не соответствует минимальному режиму работы, у вас переходить приемлемом повышения роли до проверки готовности к установке, чтобы узнать:  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeFFLError.png)  
  
### <a name="domain-controller-options"></a>Параметры контроллера домена  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeDCOptions.png)  
  
**Параметры контроллера домена** страницы указывает возможности контроллера домена для нового контроллера домена. Возможности контроллера домена настраивается являются **DNS-сервер**, **глобального каталога**, и **контроллера домена только для чтения**. Корпорация Майкрософт рекомендует, чтобы все контроллеры домена предоставляли службы DNS и глобального Каталога для обеспечения высокой доступности в распределенных средах. Глобальный Каталог всегда выбран по умолчанию и DNS-сервер выбран по умолчанию, если текущего домена размещены службы DNS на контроллерах домена на основе запроса начальной записи. **Параметры контроллера домена** страницы также можно выбрать соответствующий Active Directory логических **имя сайта** из конфигурации леса. По умолчанию выбирается сайт с наиболее подходящей подсетью. Если имеется только один сайт, он выбирается автоматически.  
  
> [!NOTE]  
> Если сервер не входит в подсеть Active Directory и имеется несколько сайтов Active Directory, выбор не производится и **Далее** кнопка недоступна, пока не будет выбран сайт из списка.  
  
Указанный **пароль режима восстановления служб каталогов** должен соответствовать политике паролей, действующей для сервера. Всегда выбирайте надежный, сложный пароль, предпочтительно парольную фразу.  
  
**Параметры контроллера домена** аргументы ADDSDeployment:  
  
```  
-InstallDNS <{$false | $true}>  
-NoGlobalCatalog <{$false | $true}>  
-sitename <string>  
-SafeModeAdministratorPassword <secure string>  
```  
  
> [!IMPORTANT]  
> Имя сайта уже должно существовать на момент ввода в качестве аргумента для **- sitename**. **Install-AddsDomainController** командлет не создает сайты. Можно использовать командлет **новый adreplicationsite** для создания сайтов.  
  
**SafeModeAdministratorPassword** аргумента действует особым:  
  
-   Если *не указан* аргумента, командлет предлагает ввести и подтвердить Скрытый пароль. Это предпочтительный вариант использования при интерактивном выполнении командлета.  
  
    Например чтобы создать дополнительный контроллер домена в домене treyresearch.net с выводом запроса на ввод и подтверждение скрытого пароля:  
  
    ```  
    Install-ADDSDomainController "DomainName treyresearch.net "credential (get-credential)  
    ```  
  
-   Если указан *со значением*, значение должно быть защищенной строкой. Это не является предпочтительным при интерактивном выполнении командлета.  
  
Например, можно вручную ввести запрос пароля с помощью **Read-Host** командлету предложить пользователю ввести защищенную строку:  
  
```  
-safemodeadministratorpassword (read-host -prompt "Password:" -assecurestring)  
```  
  
> [!WARNING]  
> Поскольку в предыдущем варианте пароль не подтверждается, соблюдайте повышенную осторожность: пароль невидим.  
  
Можно также ввести защищенную строку в переменной с преобразованным открытым текстом, хотя это не рекомендуется.  
  
```  
-safemodeadministratorpassword (convertto-securestring "Password1" -asplaintext -force)  
  
```  
  
Наконец можно сохранить Скрытый пароль в файле и затем использовать его повторно, никогда не отображая пароль открытым текстом. Например:  
  
```  
$file = "c:\pw.txt"  
$pw = read-host -prompt "Password:" -assecurestring  
$pw | ConvertFrom-SecureString | Set-Content $file  
  
-safemodeadministratorpassword (Get-Content $File | ConvertTo-SecureString)  
  
```  
  
> [!WARNING]  
> Ввод или хранение пароля в виде открытого или скрытого текста не рекомендуется. Любой пользователь, выполняющий эту команду в сценарии или заглядывающий через ваше плечо, сможет узнать пароль DSRM этого доменного контроллера.  Все, кто имеет доступ к файлу, сможет восстановить Скрытый пароль. Зная пароль они могут войти в контроллер домена запущен в режиме DSRM и персонифицировать сам контроллер домена, повысив уровень собственных привилегий самый высокий уровень в лесу Active Directory. Дополнительный набор действия, используя **System.Security.Cryptography** для шифрования текстового файла данных рекомендуется, но вне области действия. Рекомендуется полностью отказаться от хранения паролей.  
  
Командлет ADDSDeployment предлагает дополнительную возможность пропустить автоматическую настройку параметров DNS-клиента, серверов пересылки и корневых ссылок. При использовании диспетчера сервера пропустить эту настройку нельзя. Этот аргумент имеет значение только в том случае, если установлена роль DNS-сервера до настройки контроллера домена:  
  
```  
-SkipAutoConfigureDNS  
```  
  
**Параметры контроллера домена** страницы предупреждает о том, что нельзя создать контроллеры домена для чтения только, если существующие контроллеры домена Windows Server 2003. Это ожидаемое поведение, и предупреждение можно проигнорировать.  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeDCOptionsError.png)  
  
### <a name="dns-options-and-dns-delegation-credentials"></a>Параметры DNS и учетные данные для делегирования DNS  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeDNSOptions.png)  
  
**Параметры DNS** странице можно настроить делегирование DNS, если вы выбрали **DNS-сервер** вариант на *параметры контроллера домена* страницы и указана зона, в которой разрешено делегирование DNS. Может потребоваться указать альтернативные учетные данные пользователя, который является членом **Администраторы DNS** группы.  
  
**Параметры DNS** аргументы командлета ADDSDeployment:  
  
```  
-creatednsdelegation   
-dnsdelegationcredential <pscredential>  
```  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeCreds.png)  
  
Дополнительные сведения о необходимости создания делегирования DNS см. в разделе [общее представление о делегировании зоны](https://technet.microsoft.com/library/cc771640.aspx).  
  
### <a name="additional-options"></a>Дополнительные параметры  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeAdditionalOptions.png)  
  
**Дополнительные параметры** страницы приводится параметр конфигурации, чтобы имя контроллера домена в качестве источника репликации, или можно использовать любой контроллер домена в качестве источника репликации.  
  
Также можно установить контроллер домена с помощью архивированных носителей, использовав параметр установки с носителя (IFM). **Установки с носителя** флажок предоставляет возможность выбора, и вам необходимо щелкнуть **проверка** чтобы убедиться, что предоставленный путь является действительным носителем. Носители, используемые параметром IFM создается с помощью архивации данных Windows Server или Ntdsutil.exe только из другого существующего Windows Server 2012 компьютера; Windows Server 2008 R2 или предыдущей версии операционной системы нельзя использовать для создания носителей для контроллера домена Windows Server 2012. Дополнительные сведения об изменениях в IFM см. в разделе [приложение: упрощенное администрирование](../../ad-ds/deploy/Simplified-Administration-Appendix.md). Если носители защищены SYSKEY, диспетчер сервера запрашивает пароль образа во время проверки.  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_NtdsutilIFM.png)  
  
**Дополнительные параметры** аргументы командлета ADDSDeployment:  
  
```  
-replicationsourcedc <string>  
-installationmediapath <string>  
-syskey <secure string>  
```  
  
### <a name="paths"></a>Пути  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradePaths.png)  
  
**Пути** страницы позволяет переопределить расположение папок по умолчанию для базы данных AD DS, журналов транзакций базы данных и общего доступа к SYSVOL. Расположение по умолчанию, всегда в подкаталогах % systemroot %.  
  
Ниже перечислены аргументы командлета ADDSDeployment пути Active Directory  
  
```  
-databasepath <string>  
-logpath <string>  
-sysvolpath <string>  
```  
  
### <a name="preparation-options"></a>Параметры подготовки  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradePrepOptions.png)  
  
**Параметры подготовки** страницы предупреждает, что конфигурация Доменных службах Active Directory включает в себя расширение схемы (forestprep) и обновление домена (domainprep).  Только вы видите эту страницу, если лес и домен не были подготовлены с предыдущей установки контроллера домена Windows Server 2012 или путем запуска Adprep.exe вручную. Например мастер настройки доменных служб Active Directory подавляет эту страницу, при добавлении нового контроллера домена в существующий корневой домен леса Windows Server 2012.  
  
Расширение схемы и обновление домена не производятся после нажатия **Далее**. Эти операции выполняются только во время этапа установки. На этой странице просто сообщается о событиях, которые будут происходить позднее в ходе установки.  
  
На этой странице также проверяется, учетные данные текущего пользователя, члены групп "Администраторы схемы" и "Администраторы предприятия", необходимо членство в этих группах для расширения схемы и подготовки домена. Нажмите кнопку **изменение** для предоставления учетных данных пользователя, если на странице указано, что текущие учетные данные не дают необходимых разрешений.  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradePrepOptionsCreds.png)  
  
Дополнительные параметры командлета addsdeployment таков:  
  
```  
-adprepcredential <pscredential>  
```  
  
> [!IMPORTANT]  
> Как в предыдущих версиях Windows Server, автоматической подготовке домена для контроллеров домена под управлением Windows Server 2012 не запускается средство GPPREP. Запустите **adprep.exe/gpprep** вручную для всех доменов, которые не были ранее подготовлены для Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2. Необходимо запустить средство GPPrep только один раз за историю домена, а не при каждом обновлении. Adprep.exe не выполняет команду/gpprep автоматически, так как его работы может привести к все файлы и папки в папке SYSVOL будет повторно реплицировано во всех контроллерах домена.  
>   
> RODCPrep запускается автоматически при повышении роли первого контроллера RODC без предварительной подготовки в домене. Этого не происходит при повышении роли первого доступного для записи контроллера домена Windows Server 2012. Также можно по-прежнему вручную **adprep.exe/rodcprep** Если планируется развертывать контроллеры домена только для чтения.  
  
### <a name="review-options-and-view-script"></a>Просмотрите параметры и просмотреть сценарий  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeReviewOptions.png)  
  
**Просмотреть параметры** странице можно проверить параметры и убедитесь, что они отвечают требованиям, прежде чем начать установку. Это последняя возможность прервать установку, с помощью диспетчера сервера. На этой странице просто позволяет просмотреть и подтвердить параметры перед продолжением настройки.  
  
**Просмотреть параметры** страницу в диспетчере сервера расположена дополнительная **просмотреть сценарий** кнопку, чтобы создать текстовый файл в кодировке Юникод, содержащего текущую конфигурацию развертывания ADDSDeployment в виде единого скрипта Windows PowerShell. Это позволяет использовать графический интерфейс диспетчера сервера в качестве студии развертывания Windows PowerShell. Используйте мастер настройки доменных служб Active Directory, чтобы настроить параметры, экспортировать конфигурацию и затем отменить мастер.  Этого процесса создается допустимый и синтаксически верный образец для дальнейшего изменения или прямого использования.  
  
Например:  
  
```  
#  
# Windows PowerShell Script for AD DS Deployment  
#  
Import-Module ADDSDeployment  
Install-ADDSDomainController `  
-CreateDNSDelegation `  
-Credential (Get-Credential) `  
-CriticalReplicationOnly:$false `  
-DatabasePath "C:\Windows\NTDS" `  
-DomainName "root.fabrikam.com" `  
-InstallDNS:$true `  
-LogPath "C:\Windows\NTDS" `  
-SiteName "Default-First-Site-Name" `  
-SYSVOLPath "C:\Windows\SYSVOL"  
-Force:$true  
  
```  
  
> [!NOTE]  
> Диспетчер сервера обычно задает все значения аргументов при повышении роли, не зависит от значения по умолчанию (как они могут изменяться в будущих версиях Windows или пакетах обновления). Единственным исключением является **- safemodeadministratorpassword** аргумент. Для принудительного вывода запроса на подтверждение, не указывайте значение, при интерактивном выполнении командлета.  
>   
> Используйте дополнительный **Whatif** аргумент с **Install-ADDSDomainController** для просмотра сведений о конфигурации. Это позволяет просмотреть явные и неявные значения аргументов командлета.  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_PSWhatIf.png)  
  
### <a name="prerequisites-check"></a>Проверка готовности к установке  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradePrereqCheck.png)  
  
**Проверка предварительных требований** — это новая функция в конфигурации домена AD DS. На этом новом этапе проверяется возможность поддержки нового контроллера домена Windows Server 2012 доменом и лесом.  
  
При установке нового контроллера домена, Server Manager Active Directory домена мастер настройки служб вызывает ряд сериализованных модульных тестов. Эти предлагаются рекомендуемые способы восстановления. Тесты можно выполнять необходимое число раз. Домен контроллера не может продолжаться, пока все проверки предварительных требований передачи.  
  
**Проверка предварительных требований** также поверхности важные сведения, такие как изменения безопасности, затрагивающих предыдущие операционные системы.  
  
Дополнительные сведения о проверках предварительных требований см. в разделе [проверка предварительных требований](../../ad-ds/manage/AD-DS-Simplified-Administration.md#BKMK_PrereuisiteChecking).  
  
Нельзя **проверка готовности к установке** при с помощью диспетчера сервера, но вы можете пропустить при использовании командлета развертывания AD DS, с помощью следующего аргумента:  
  
```  
-skipprechecks  
  
```  
  
> [!WARNING]  
> Корпорация Майкрософт не рекомендует пропускать проверку предварительных требований, так как это может привести к повышению роли контроллера домена частичная или повреждению леса AD DS.  
  
Нажмите кнопку **установить** начинается процесс повышения роли контроллера домена. Это последняя возможность отменить установку. Процесс повышения роли нельзя отменить после ее начала. По завершении повышения роли, вне зависимости от результата повышения роли компьютер перезагрузится автоматически. **Проверка предварительных требований** странице отображаются все проблемы, обнаруженной во время и рекомендации по их устранению.  
  
### <a name="installation"></a>Установка  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_UpgradeInstallProgress.png)  
  
Когда **установки** отображает страницу, конфигурации контроллера домена начинается и невозможно остановить или отменить. Подробная информация об операциях выводится на этой странице и записывается в журналы:  
  
-   %systemroot%\debug\dcpromo.log  
  
-   %systemroot%\debug\dcpromoui.log  
  
-   %systemroot%\debug\adprep\logs  
  
-   %systemroot%\debug\netsetup.log (если сервер входит в рабочую группу)  
  
Чтобы установить новый лес Active Directory, с помощью модуля ADDSDeployment, используйте следующий командлет:  
  
```  
Install-addsdomaincontroller  
```  
  
В разделе [обновление и Добавление реплики Windows PowerShell](../../ad-ds/deploy/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-.md#BKMK_PS) для обязательных и необязательных аргументов.  
  
**Install-AddsDomainController** командлет включает только два этапа (проверка предварительных требований и установка). На двух иллюстрациях ниже показан этап установки с минимальным необходимым набором аргументов **- domainname** и **-credential**. Обратите внимание, как операция Adprep выполняется автоматически в рамках добавления первого контроллера домена Windows Server 2012 в существующий лес Windows Server 2003:  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_PSGetCred.png)  
  
Обратите внимание, что так же, как диспетчер сервера **Install-ADDSDomainController** напоминает о том, что повышения уровня сервер автоматически перезагрузится. Чтобы напоминание о перезагрузке автоматически, используйте **-принудительно** или **-подтверждение: $false** аргументы с любым командлетом ADDSDeployment Windows PowerShell. Чтобы предотвратить автоматическую перезагрузку по завершении повышения роли сервера, используйте **- norebootoncompletion** аргумент.  
  
> [!WARNING]  
> Отключать перезагрузку не рекомендуется. Для правильной работы контроллер домена должен перезагрузиться.  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_PSUpgradeConfirm.gif)  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_PSUpgradeProgress.png)  
  
Чтобы настроить контроллер домена удаленно с помощью Windows PowerShell, заключите **install-adddomaincontroller** командлета *внутри* из **invoke-command** командлета. Для этого необходимо использовать фигурные скобки.  
  
```  
invoke-command {install-addsdomaincontroller "domainname <domain> -credential (get-credential)} -computername <dc name>  
```  
  
Например:  
  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_PSUpgradeExample.gif)  
  
> [!NOTE]  
> Дополнительные сведения о том, как установка и процесс Adprep, см. [Устранение неполадок развертывания контроллера домена](../../ad-ds/deploy/Troubleshooting-Domain-Controller-Deployment.md).  
  
### <a name="results"></a>Результаты  
![Установка реплики](media/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-/ADDS_SMI_TR_ForestSignOff.png)  
  
**Результатов** странице отображается успешном или неудачном повышение роли, а также все важные данные администратора. В случае успешного выполнения контроллер домена автоматически перезагрузится через 10 секунд.  
  
Как и в предыдущих версиях Windows Server, в автоматической подготовке домена для контроллеров домена под управлением Windows server 2012 средство GPPREP не запускается. Запустите **adprep.exe/gpprep** вручную для всех доменов, которые не были ранее подготовлены для Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2. Необходимо запустить средство GPPrep только один раз за историю домена, а не при каждом обновлении. Adprep.exe не выполняет команду/gpprep автоматически, так как его работы может привести к все файлы и папки в папке SYSVOL будет повторно реплицировано во всех контроллерах домена.  
  

