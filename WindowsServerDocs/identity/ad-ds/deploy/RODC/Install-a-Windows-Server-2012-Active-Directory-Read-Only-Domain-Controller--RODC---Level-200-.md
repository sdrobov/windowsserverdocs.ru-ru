---
ms.assetid: 66fa945e-598d-4f18-b603-97a39ce0d836
title: "Установка Windows контроллера домена только для Active Directory Server 2012 чтения (RODC) (уровень 200)"
description: "В этом разделе объясняется, как создать промежуточную учетную запись RODC и затем связать сервер с этой учетной записи во время установки RODC. В этом разделе также объясняется, как установить RODC, не выполняя поэтапную установку."
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 78281ca845f79955aaa25aa45394284c59e639cb
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="install-a-windows-server-2012-active-directory-read-only-domain-controller-rodc-level-200"></a>Установка Windows контроллера домена только для Active Directory Server 2012 чтения (RODC) (уровень 200)

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе объясняется, как создать промежуточную учетную запись RODC и затем связать сервер с этой учетной записи во время установки RODC. В этом разделе также объясняется, как установить RODC, не выполняя поэтапную установку.  
  
## <a name="stage-rodc-workflow"></a>Рабочий процесс поэтапной RODC  
Поэтапная только контроллера домена чтения (RODC) установки состоит из двух отдельных этапов:  
  
1.  Промежуточное хранение незанятой учетной записи компьютера  
  
2.  При повышении роли эту учетную запись для подключения контроллера RODC  
  
Схеме ниже показан процесс поэтапного контроллера домена Active Directory домена службы только для чтения, где создать пустой учетной записи компьютера RODC в домене, используя Центр администрирования Active Directory (Dsac.exe).  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/adds_stagedcreation.png)  
  
## <a name="BKMK_StagePS"></a>Поэтапная Установка RODC Windows PowerShell  
  
|||  
|-|-|  
|**Командлет ADDSDeployment**|Аргументы (**Полужирный** требуются аргументы. *Курсивом* аргументов можно указать с помощью Windows PowerShell или мастера настройки AD DS.)|  
|-Addsreadonlydomaincontrolleraccount|-SkipPreChecks<br /><br />***-DomainControllerAccountName***<br /><br />***-DomainName***<br /><br />***-SiteName***<br /><br />*-AllowPasswordReplicationAccountName*<br /><br />***-Credential***<br /><br />*-DelegatedAdministratorAccountName*<br /><br />*-DenyPasswordReplicationAccountName*<br /><br />*-NoGlobalCatalog*<br /><br />*-InstallDNS*<br /><br />-ReplicationSourceDC|  
  
> [!NOTE]  
> **-Credential** только требуется, если вы уже вошли на является членом группы администраторов домена.  
  
## <a name="attach-rodc-workflow"></a>Рабочий процесс подключения RODC  
На схеме ниже показан процесс настройки доменных служб Active Directory, что вы уже установили роль Доменных службах Active Directory, вы подготовили учетную запись RODC и запустили **повысить роль этого сервера до уровня контроллера домена** создания контроллера RODC в существующем домене и его подключения к промежуточной учетной записи компьютера с помощью диспетчера сервера.  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/adds_stageddeploy_beta1.png)  
  
## <a name="BKMK_AttachPS"></a>Подключение RODC с Windows PowerShell  
  
|||  
|-|-|  
|**Командлет ADDSDeployment**|Аргументы (**Полужирный** требуются аргументы. *Курсивом* аргументов можно указать с помощью Windows PowerShell или мастера настройки AD DS.)|  
|Install-AddsDomaincontroller|-SkipPreChecks<br /><br />***-DomainName***<br /><br />*-SafeModeAdministratorPassword*<br /><br />*-ApplicationPartitionsToReplicate*<br /><br />*-CreateDNSDelegation*<br /><br />***-Credential***<br /><br />-CriticalReplicationOnly<br /><br />*-DatabasePath*<br /><br />*-DNSDelegationCredential*<br /><br />*-InstallationMediaPath*<br /><br />*-LogPath*<br /><br />-Norebootoncompletion<br /><br />*-ReplicationSourceDC*<br /><br />*-SystemKey*<br /><br />*-SYSVOLPath*<br /><br />***-UseExistingAccount***|  
  
> [!NOTE]  
> **-Credential** только требуется, если вы уже вошли на является членом группы администраторов домена.  
  
## <a name="staging"></a>Промежуточного хранения  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_PreCreateRODC.png)  
  
Чтобы выполнить Поэтапное создание учетной записи компьютера контроллера домена только для чтения, откройте Центр администрирования Active Directory (**Dsac.exe**). Щелкните имя домена, в области навигации. Дважды щелкните **контроллеры домена** в списке управления. Нажмите кнопку **предварительное создание учетной записи контроллера домена только для чтения** на панели задач.  
  
Дополнительные сведения о центре администрирования Active Directory см. в разделе [Дополнительно AD DS управления при помощи Active Directory центра администрирования & #40; Уровень 200 & #41; ](../../../ad-ds/get-started/adac/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-.md) и просмотрите [Центр администрирования Active Directory: Приступая к работе](https://technet.microsoft.com/library/dd560651(WS.10).aspx).  
  
Если у вас есть опыт создания контроллеров домена только для чтения, вы заметите, что мастер установки имеет такой же графический интерфейс, что при использовании оснастки компьютеров с Windows Server 2008 и более старых Active Directory-пользователи и использует тот же код, включая экспорт конфигурации в формате файла автоматической установки, используемом устаревшим средством dcpromo.  
  
Windows Server 2012 появился новый командлет ADDSDeployment для поэтапного создания учетных записей компьютеров RODC, но мастер используется для ее работы. Следующих разделах приводится эквивалентный командлет и аргументы позволит лучше сведения, связанные с ними для понимания.  
  
**Предварительное создание учетной записи контроллера домена только для чтения** ссылку в области задач Центр администрирования Active Directory является эквивалентом командлетом ADDSDeployment Windows PowerShell:  
  
```  
Add-addsreadonlydomaincontrolleraccount  
  
```  
  
### <a name="welcome"></a>Добро пожаловать  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_WelcomeStage1.png)  
  
**Добро пожаловать в мастер установки доменных служб Active Directory** диалоговое окно содержит один параметр под названием **использовать расширенный режим установки**. Выберите этот параметр, нажмите кнопку **Далее** Чтобы просмотреть параметры политики репликации паролей. Снимите этот флажок, чтобы использовать значения по умолчанию для параметров по политики репликации паролей (рассматриваются подробнее далее в этом разделе).  
  
### <a name="network-credentials"></a>Сетевые учетные данные  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage1Creds.png)  
  
В поле доменного имени указан **сетевые учетные данные** Центр администрирования Active Directory целевой домен по умолчанию, отображается диалоговое окно. По умолчанию используются ваши текущие учетные данные. Если они не входят в группу "Администраторы домена", нажмите кнопку **альтернативные учетные данные**и нажмите кнопку **задать** чтобы предоставить мастеру имя пользователя и пароль, который является членом группы "Администраторы домена".  
  
— Эквивалентный аргумент ADDSDeployment Windows PowerShell:  
  
```  
-credential <pscredential>  
```  
  
Имейте в виду, что система поэтапного создания была напрямую перенесена из Windows Server 2008 R2 и не предоставляет новых функциональных возможностей Adprep. Если вы планируете развертывать поэтапно создаваемые учетные записи RODC, необходимо сначала развернуть RODC без предварительной подготовки в том же домене, что автоматически выполнять операцию rodcprep или вручную выполнить команду adprep.exe/rodcprep сначала.  
  
В противном случае появится ошибка «Не можно установить контроллер домена только для чтения в этом домене, поскольку «adprep/rodcprep еще не была выполнена».  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCPrepNotRunError.png)  
  
### <a name="specify-the-computer-name"></a>Укажите имя компьютера  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage1CompName.png)  
  
**Указать имя компьютера** диалоговое окно необходимо ввести однокомпонентное **имя компьютера** контроллера домена, который не существует. Контроллер домена, вы настроите и подключите к этой учетной записи позднее, должен иметь то же имя, или операции повышения роли не удастся обнаружить промежуточную учетную запись.  
  
— Эквивалентный аргумент ADDSDeployment Windows PowerShell:  
  
```  
-domaincontrolleraccountname <string>  
```  
  
### <a name="select-a-site"></a>Выберите сайт  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage1Site.png)  
  
**Выберите сайт** диалогового окна отображается список сайтов Active Directory для текущего леса. Операция контроллера домена предварительной подготовки только для чтения требует выбора одного сайта из списка. Контроллер RODC использует эту информацию для создания собственного объекта параметров NTDS в разделе конфигурации и подключения к соответствующему сайту при первом запуске после развертывания.  
  
— Эквивалентный аргумент ADDSDeployment Windows PowerShell:  
  
```  
-sitename <string>  
```  
  
### <a name="additional-domain-controller-options"></a>Дополнительные параметры контроллера домена  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage1DCOptions.png)  
  
**Дополнительные параметры контроллера домена** диалогового окна можно указать, что контроллер домена также выступать в роли **DNS-сервер** и **глобального каталога**. Майкрософт рекомендует, чтобы контроллеры домена только для чтения предоставляли службы DNS и глобального Каталога, поэтому оба устанавливаются по умолчанию; одно из предназначений роли RODC — сценарии использования в филиалах которых глобальная сеть может быть недоступна, а без этих служб DNS и глобального каталога, компьютеры филиала не смогут использовать ресурсы в Доменных службах Active Directory и функциональные возможности.  
  
**Контроллер домена только для чтения (RODC)** параметр предварительно выбран и не может быть отключено. Эквивалентные аргументы ADDSDeployment Windows PowerShell являются:  
  
```  
-installdns <string>  
-NoGlobalCatalog <{$true | $false}>  
  
```  
  
> [!NOTE]  
> По умолчанию **- NoGlobalCatalog** имеет значение $false, то есть контроллер домена будет являться сервером глобального каталога, если аргумент не задан.  
  
### <a name="specify-the-password-replication-policy"></a>Укажите политику репликации паролей  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage1PRP.png)  
  
**Укажите политику репликации паролей** диалоговое окно позволяет изменить список учетных записей, которые разрешено кэшировать пароли в данном контроллере домена только для чтения по умолчанию. Учетные записи в списке задано **запретить** или которые отсутствуют в списке (неявный запрет), не кэшируют свои пароли. Учетные записи, которые не разрешено кэшировать пароли в контроллере RODC и не могут подключаться и проверки подлинности для записи контроллеру домена не имеют доступа к ресурсам и функциональным возможностям Active Directory.  
  
> [!IMPORTANT]  
> Это диалоговое окно мастера выводится только при выборе **использовать расширенный режим установки** флажок на экране приветствия. Если вы снимете этот флажок установлен, мастер использует следующие группы по умолчанию и значения:  
>   
> -   Администраторы — запретить  
> -   Операторы сервера — запретить  
> -   Операторы архива — запретить  
> -   Операторы учета — запретить  
> -   Отказано в группу репликации паролей RODC — запретить  
> -   Группа репликации паролей RODC — разрешить  
  
Эквивалентные аргументы ADDSDeployment Windows PowerShell являются:  
  
```  
-allowpasswordreplicationaccountname <string []>  
-denypasswordreplicationaccountname <string []>  
```  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage1PRPAllow.png)  
  
### <a name="delegation-of-rodc-installation-and-administration"></a>Делегирование установки и администрирования RODC  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage1DelegateAdmin.png)  
  
**Делегирования для установки и администрирования RODC** диалоговое окно позволяет настроить пользователя или группу, содержащую пользователей, которым разрешено подключать сервер к учетной записи компьютера RODC. Нажмите кнопку **задать** для просмотра домена для пользователя или группы. Пользователь или группа, указанные в этом диалоговом окне прибыли локальные права администратора для RODC. Указанный пользователь или члены указанной группы могут выполнять операции на RODC с правами, эквивалентными правам группы администраторов компьютера. Они являются *не* членами группы администраторов домена или встроенной группы администраторов домена.  
  
Используйте этот параметр, чтобы делегировать администрирование филиала, не предоставляя администраторам филиала членство в группе администраторов домена. Делегировать администрирование RODC необязательно.  
  
— Эквивалентный аргумент ADDSDeployment Windows PowerShell:  
  
```  
-delegatedadministratoraccountname <string>  
```  
  
### <a name="summary"></a>Сводка  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage1Summary.png)  
  
**Сводка** диалоговое окно позволяет подтвердить параметры. Это последняя возможность прервать установку, прежде чем мастер создаст промежуточную учетную запись. Нажмите кнопку **Далее** когда вы будете готовы создать промежуточную учетную запись компьютера RODC.  Нажмите кнопку **экспорт параметров** сохранить файл ответов в формате файла автоматической установки устаревшим средством dcpromo.  
  
### <a name="creation"></a>Создание  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage1InstallProgress.png)  
  
**Мастер установки доменных служб Active Directory** создает контроллер домена только для чтения предварительной подготовки в Active Directory. Невозможно отменить эту операцию после ее запуска.  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage1Complete.png)  
  
Чтобы поэтапно учетной записи компьютера контроллера домена только для чтения с помощью модуля ADDSDeployment Windows PowerShell, используйте следующий командлет:  
  
```  
Add-addsreadonlydomaincontrolleraccount  
  
```  
  
В разделе [поэтапная установка RODC Windows PowerShell](../../../ad-ds/deploy/RODC/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-.md#BKMK_StagePS) для обязательных и необязательных аргументов.  
  
Так как **Add-addsreadonlydomaincontrolleraccount** имеет только один раз в два этапа (готовности к установке проверка и установка), приведенных ниже снимках экрана показан этап установки с минимальным необходимым набором аргументов.  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_PSAddRODC.png)  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_PSAddRODCValidating.png)  
  
Этап операции RODC создает учетную запись компьютера RODC в Active Directory. Центр администрирования Active Directory показывает **тип контроллера домена** как **незанятая учетная запись контроллера домена**. Этот тип контроллера домена указывает, что промежуточная учетная запись RODC готова к подключению сервера в его как только контроллера домена для чтения.  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Unoccupied.png)  
  
> [!IMPORTANT]  
> Центр администрирования Active Directory больше не требуется для прикрепления сервера к учетной записи компьютера контроллера домена только для чтения. Используйте диспетчер сервера и мастер настройки доменных служб Active Directory или командлет ADDSDeployment Windows PowerShell модуля **Install-AddsDomainController** Чтобы подключить контроллер RODC к промежуточной учетной записи. Действия, аналогичны добавлении нового контроллера домена в существующий домен, за исключением, что промежуточную учетную запись компьютера RODC содержит параметры конфигурации, заданные при поэтапном создании учетной записи компьютера RODC.  
  
## <a name="attaching"></a>Присоединение  
  
### <a name="deployment-configuration"></a>Конфигурация развертывания  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCDeployConfig.png)  
  
Диспетчер серверов начинает повышение роли каждого контроллера домена с **конфигурации развертывания** страницы. Оставшиеся параметры и обязательные поля меняются на этой странице и последующих страницах в зависимости от того, какая операция развертывания выбрана.  
  
Чтобы добавить контроллер домена только для чтения в существующий домен, выберите **добавить контроллер домена в существующий домен** и нажмите кнопку **выберите** , чтобы **указать сведения о домене для данного домена**. Диспетчер серверов автоматически запросит действительные учетные данные, либо нажать кнопку **изменение**.  
  
Для подключения контроллера RODC необходимо членство в группе администраторов домена в Windows Server 2012. Мастер настройки доменных служб Active Directory предлагает позже, если у текущих учетных данных нет соответствующих разрешений или членства в группах.  
  
**Конфигурации развертывания** ADDSDeployment Windows PowerShell командлет и аргументы:  
  
```  
Install-AddsDomainController  
-domainname <string>   
-credential <pscredential>  
```  
  
### <a name="domain-controller-options"></a>Параметры контроллера домена  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage2DCOptions.png)  
  
**Параметры контроллера домена** страницы показаны параметры нового контроллера домена. При загрузке этой страницы мастер настройки доменных служб Active Directory отправляет запрос LDAP к контроллеру домена для проверки незанятых учетных записей. Если запрос находит найдена незанятая учетная запись компьютера, с тем же именем, что текущего компьютера, а затем Мастер отображает информационное сообщение в верхней части страницы «**предварительно созданная учетная запись RODC, соответствующая имени целевого сервера существует в каталоге. Выберите, следует ли использовать существующую учетную запись RODC или переустановить этот контроллер домена**.» В мастере используется **использовать существующую учетную запись RODC** по умолчанию.  
  
> [!IMPORTANT]  
> Можно использовать **переустановить этот контроллер домена** вариант, если контроллер домена произошла физическая неполадка и не может восстановить работоспособность. Это позволит сэкономить время при настройке контроллера домена для замены благодаря тому учетная запись компьютера контроллера домена и метаданные в Active Directory объекта. Установите новый компьютер с *таким же именем*, повысьте его роль до контроллера домена в домене. **Переустановить этот контроллер домена** параметр недоступен, если вы удалили метаданные объекта контроллера домена из Active Directory (выполнили очистку метаданных).  
  
Настроить параметры контроллера домена при подключении сервера к учетной записи компьютера RODC нельзя. При создании промежуточную учетную запись компьютера RODC, настроить параметры контроллера домена.  
  
Указанный **пароль режима восстановления служб каталогов** должен соответствовать политике паролей, действующей для сервера. Всегда выбирайте надежный, сложный пароль, предпочтительно парольную фразу.  
  
**Параметры контроллера домена** аргументы ADDSDeployment Windows PowerShell:  
  
```  
-UseExistingAccount <{$true | $false}>  
-SafeModeAdministratorPassword <secure string>  
```  
  
> [!IMPORTANT]  
> Имя сайта уже должно существовать на момент ввода в качестве аргумента для **- sitename**. **Install-AddsDomainController** командлет не создает имена сайтов. Можно использовать командлет **новый adreplicationsite** для создания сайтов.  
  
**Install-ADDSDomainController** аргументы выполните того же значения по умолчанию в диспетчере сервера, если не указано.  
  
**SafeModeAdministratorPassword** аргумента действует особым:  
  
-   Если *не указан* аргумента, командлет предлагает ввести и подтвердить Скрытый пароль. Это предпочтительный вариант использования при интерактивном выполнении командлета.  
  
    Например чтобы создания контроллера RODC в домене corp.contoso.com с выводом запроса на ввод и подтверждение скрытого пароля:  
  
    ```  
    Install-ADDSDomainController -DomainName corp.contoso.com -credential (get-credential)  
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
> Ввод или хранение пароля в виде открытого или скрытого текста не рекомендуется. Любой пользователь, выполняющий эту команду в сценарии или заглядывающий через ваше плечо, сможет узнать пароль DSRM этого доменного контроллера.  Все, кто имеет доступ к файлу, сможет восстановить Скрытый пароль. Зная пароль они могут войти в контроллер домена запущен в режиме DSRM и персонифицировать сам контроллер домена, повысив уровень собственных привилегий самый высокий уровень в составе леса AD. Дополнительный набор действия, используя **System.Security.Cryptography** для шифрования текстового файла данных рекомендуется, но вне области действия. Рекомендуется полностью отказаться от хранения паролей.  
  
### <a name="additional-options"></a>Дополнительные параметры  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage2AdditionalOptions.png)  
  
**Дополнительные параметры** страница содержит параметры конфигурации для имя контроллера домена в качестве источника репликации, или можно использовать любой контроллер домена в качестве источника репликации.  
  
Также можно установить контроллер домена с помощью архивированных носителей, использовав параметр установки с носителя (IFM). **Установки с носителя** флажок предоставляет возможность выбора, и вам необходимо щелкнуть **проверка** чтобы убедиться, что предоставленный путь является действительным носителем. Носители, используемые параметром IFM создается с помощью архивации данных Windows Server или Ntdsutil.exe только из другого существующего Windows Server 2012 компьютера; Windows Server 2008 R2 или предыдущей версии операционной системы нельзя использовать для создания носителей для контроллера домена Windows Server 2012. Дополнительные сведения об изменениях в IFM см. в разделе [Ntdsutil.exe установки с носителя изменения](../../../ad-ds/deploy/Simplified-Administration-Appendix.md#BKMK_IFM). Если носители защищены SYSKEY, диспетчер сервера запрашивает пароль образа во время проверки.  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_StagedIFM.png)  
  
**Дополнительные параметры** аргументы командлета ADDSDeployment:  
  
```  
-replicationsourcedc <string>  
-installationmediapath <string>  
-systemkey <secure string>  
```  
  
### <a name="paths"></a>Пути  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage2Paths.png)  
  
**Пути** страницы позволяет переопределить расположение папок по умолчанию для базы данных AD DS, журналов транзакций базы данных и общего доступа к SYSVOL. Расположение по умолчанию, всегда в подкаталогах % systemroot %. **Пути** аргументы командлета ADDSDeployment:  
  
```  
-databasepath <string>  
-logpath <string>  
-sysvolpath <string>  
```  
  
### <a name="review-options-and-view-script"></a>Просмотрите параметры и просмотреть сценарий  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage2ReviewOptions.png)  
  
**Просмотреть параметры** странице можно проверить параметры и убедитесь, что они отвечают требованиям, прежде чем начать установку. Это последняя возможность прервать установку, с помощью диспетчера сервера. На этой странице просто позволяет просмотреть и подтвердить параметры перед продолжением настройки. **Просмотреть параметры** страницу в диспетчере сервера расположена дополнительная **просмотреть сценарий** кнопку, чтобы создать текстовый файл в кодировке Юникод, содержащего текущую конфигурацию развертывания ADDSDeployment в виде единого скрипта Windows PowerShell. Это позволяет использовать графический интерфейс диспетчера сервера в качестве студии развертывания Windows PowerShell. Используйте мастер настройки доменных служб Active Directory, чтобы настроить параметры, экспортировать конфигурацию и затем отменить мастер. Этого процесса создается допустимый и синтаксически верный образец для дальнейшего изменения или прямого использования. Например:  
  
```  
#  
# Windows PowerShell Script for AD DS Deployment  
#  
  
Import-Module ADDSDeployment  
Install-ADDSDomainController `  
-Credential (Get-Credential) `  
-CriticalReplicationOnly:$false `  
-DatabasePath "C:\Windows\NTDS" `  
-DomainName "corp.contoso.com" `  
-LogPath "C:\Windows\NTDS" `  
-SYSVOLPath "C:\Windows\SYSVOL" `  
-UseExistingAccount:$true `  
-Norebootoncompletion:$false  
-Force:$true  
  
```  
  
> [!NOTE]  
> Диспетчер сервера обычно задает все значения аргументов при повышении роли, не зависит от значения по умолчанию (как они могут изменяться в будущих версиях Windows или пакетах обновления). Единственным исключением является **- safemodeadministratorpassword** аргумент. Для принудительного вывода запроса на подтверждение, не указывайте значение, при интерактивном выполнении командлета.  
  
Используйте дополнительный **Whatif** аргумент с **Install-ADDSDomainController** для просмотра сведений о конфигурации. Это позволяет просмотреть явные и неявные значения аргументов командлета.  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage2WhatIf.png)  
  
### <a name="prerequisites-check"></a>Проверка готовности к установке  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage2PrereqCheck.png)  
  
**Проверка предварительных требований** — это новая функция в конфигурации домена AD DS. На этом новом этапе проверяется конфигурации сервера возможность поддержки нового леса AD DS.  
  
При установке нового корневого домена леса, Server Manager Active Directory домена мастер настройки служб вызывает ряд сериализованных модульных тестов. Эти предлагаются рекомендуемые способы восстановления. Тесты можно выполнять необходимое число раз. Не удается продолжить процесс установки контроллера домена, пока все проверки предварительных требований передачи.  
  
**Проверка предварительных требований** также поверхности важные сведения, такие как изменения безопасности, затрагивающих предыдущие операционные системы. Дополнительные сведения о проверках предварительных требований см. в разделе [проверка предварительных требований](../../../ad-ds/manage/AD-DS-Simplified-Administration.md#BKMK_PrereuisiteChecking).  
  
Нельзя **проверка готовности к установке** при с помощью диспетчера сервера, но вы можете пропустить при использовании командлета развертывания AD DS, с помощью следующего аргумента:  
  
```  
-skipprechecks  
  
```  
  
> [!WARNING]  
> Корпорация Майкрософт не рекомендует пропускать проверку предварительных требований, так как это может привести к повышению роли контроллера домена частичная или повреждению леса AD DS.  
  
Нажмите кнопку **установить** начинается процесс повышения роли контроллера домена. Это последняя возможность отменить установку. Процесс повышения роли нельзя отменить после ее начала. По завершении повышения роли, вне зависимости от результата повышения роли компьютер перезагрузится автоматически.  
  
### <a name="installation"></a>Установка  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_Stage2Installation.png)  
  
При отображении страницы установки, настройки контроллера домена начинается невозможно приостановлена или и отменен. Подробная информация об операциях выводится на этой странице и записывается в журналы:  
  
-   %systemroot%\debug\dcpromo.log  
  
-   %systemroot%\debug\dcpromoui.log  
  
Чтобы установить новый лес Active Directory, с помощью модуля ADDSDeployment, используйте следующий командлет:  
  
```  
Install-addsdomaincontroller  
  
```  
  
В разделе [подключение RODC Windows PowerShell](../../../ad-ds/deploy/RODC/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-.md#BKMK_AttachPS) для обязательных и необязательных аргументов.  
  
**Install-addsdomaincontroller** командлет включает только два этапа (проверка предварительных требований и установка). На двух иллюстрациях ниже показан этап установки с минимальным необходимым набором аргументов **- domainname**, **- useexistingaccount**, и **-credential**. Обратите внимание, что так же, как диспетчер сервера **Install-ADDSDomainController** напоминает о том, что автоматической перезагрузке повышения роли сервера:  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_PSStage2.png)  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_PSStage2Complete.png)  
  
Чтобы напоминание о перезагрузке автоматически, используйте **-принудительно** или **-подтверждение: $false** аргументы с любым командлетом ADDSDeployment Windows PowerShell. Чтобы предотвратить автоматическую перезагрузку по завершении повышения роли сервера, используйте **- norebootoncompletion** аргумент.  
  
> [!WARNING]  
> Отключать перезагрузку не рекомендуется. Для правильной работы контроллер домена должен перезагрузиться.  
  
### <a name="results"></a>Результаты  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_ForestSignOff.png)  
  
**Результатов** странице отображается успешном или неудачном повышение роли, а также все важные данные администратора. Контроллер домена автоматически перезагрузится через 10 секунд.  
  
## <a name="rodc-without-staging-workflow"></a>Создание RODC без промежуточного хранения рабочего процесса  
Схеме ниже показан процесс настройки доменных служб Active Directory, если вы ранее установили роль Доменных служб Active Directory и запустили Active Directory мастер настройки доменных служб с помощью диспетчера сервера для создания нового контроллера домена только для чтения без предварительной подготовки в существующем домене Windows Server 2012.  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/adds_rodcdeploy.png)  
  
## <a name="rodc-without-staging-windows-powershell"></a>RODC без предварительной подготовки Windows PowerShell  
  
|||  
|-|-|  
|**Командлет ADDSDeployment**|Аргументы (**Полужирный** требуются аргументы. *Курсивом* аргументов можно указать с помощью Windows PowerShell или мастера настройки AD DS.)|  
|Install-AddsDomainController|-SkipPreChecks<br /><br />***-DomainName***<br /><br />*-SafeModeAdministratorPassword*<br /><br />***-SiteName***<br /><br />*-ApplicationPartitionsToReplicate*<br /><br />*-CreateDNSDelegation*<br /><br />***-Credential***<br /><br />*-CriticalReplicationOnly*<br /><br />*-DatabasePath*<br /><br />*-DNSDelegationCredential*<br /><br />-DNSOnNetwork<br /><br />*-InstallationMediaPath*<br /><br />*-InstallDNS*<br /><br />*-LogPath*<br /><br />-MoveInfrastructureOperationMasterRoleIfNecessary<br /><br />*-NoGlobalCatalog*<br /><br />-Norebootoncompletion<br /><br />*-ReplicationSourceDC*<br /><br />-SkipAutoConfigureDNS<br /><br />*-SystemKey*<br /><br />*-SYSVOLPath*<br /><br />*-AllowPasswordReplicationAccountName*<br /><br />*-DelegatedAdministratorAccountName*<br /><br />*-DenyPasswordReplicationAccountName*<br /><br />***-ReadOnlyReplica***|  
  
> [!NOTE]  
> **-Credential** только требуется, если вы уже вошли на является членом группы администраторов домена.  
  
## <a name="rodc-without-staging-deployment"></a>Создание RODC без развертывания промежуточного хранения  
  
### <a name="deployment-configuration"></a>Конфигурация развертывания  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCDeployConfig.png)  
  
Диспетчер серверов начинает повышение роли каждого контроллера домена с **конфигурации развертывания** страницы. Оставшиеся параметры и обязательные поля меняются на этой странице и последующих страницах в зависимости от того, какая операция развертывания выбрана.  
  
Чтобы добавить контроллер домена только для чтения без предварительной подготовки в существующий домен Windows Server 2012, установите **добавить контроллер домена в существующий домен** и нажмите кнопку **выберите** , чтобы **указать сведения о домене для данного домена**. Диспетчер серверов автоматически запросит действительные учетные данные, либо нажать кнопку **изменение**.  
  
Для подключения контроллера RODC необходимо членство в группе администраторов домена в Windows Server 2012. Мастер настройки доменных служб Active Directory предлагает позже, если у текущих учетных данных нет соответствующих разрешений или членства в группах.  
  
**Конфигурации развертывания** ADDSDeployment Windows PowerShell командлет и аргументы:  
  
```  
Install-AddsDomainController  
-domainname <string>   
-credential <pscredential>  
```  
  
### <a name="domain-controller-options"></a>Параметры контроллера домена  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCDCOptions.png)  
  
**Параметры контроллера домена** страницы указывает возможности контроллера домена для нового контроллера домена. Возможности контроллера домена настраивается являются **DNS-сервер**, **глобального каталога**, и **контроллера домена только для чтения**. Корпорация Майкрософт рекомендует, чтобы все контроллеры домена предоставляли службы DNS и глобального Каталога для обеспечения высокой доступности в распределенных средах. Глобальный Каталог всегда выбран по умолчанию и DNS-сервер выбран по умолчанию, если текущего домена размещены службы DNS на контроллерах домена на основе запроса начальной записи.  
  
**Параметры контроллера домена** страницы также можно выбрать соответствующий Active Directory логических **имя сайта** из конфигурации леса. По умолчанию выбирается сайт с наиболее подходящей подсетью. Если имеется только один сайт, он выбирается автоматически.  
  
> [!IMPORTANT]  
> Если сервер не входит в подсеть Active Directory и имеется несколько сайтов Active Directory, выбор не производится и **Далее** кнопка недоступна, пока не будет выбран сайт из списка.  
  
Указанный **пароль режима восстановления служб каталогов** должен соответствовать политике паролей, действующей для сервера. Всегда выбирайте надежный, сложный пароль, предпочтительно парольную фразу. **Параметры контроллера домена** аргументы ADDSDeployment Windows PowerShell:  
  
```  
-UseExistingAccount <{$true | $false}>  
-SafeModeAdministratorPassword <secure string>  
```  
  
> [!IMPORTANT]  
> Имя сайта уже должно существовать на момент ввода в качестве аргумента для **- sitename**. **Install-AddsDomainController** командлет не создает имена сайтов. Можно использовать командлет **новый adreplicationsite** для создания сайтов.  
  
**Install-ADDSDomainController** аргументы выполните того же значения по умолчанию в диспетчере сервера, если не указано.  
  
**SafeModeAdministratorPassword** аргумента действует особым:  
  
-   Если *не указан* аргумента, командлет предлагает ввести и подтвердить Скрытый пароль. Это предпочтительный вариант использования при интерактивном выполнении командлета.  
  
    Например чтобы создания контроллера RODC в домене corp.contoso.com с выводом запроса на ввод и подтверждение скрытого пароля:  
  
    ```  
    Install-ADDSDomainController -DomainName corp.contoso.com -credential (get-credential)  
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
> Ввод или хранение пароля в виде открытого или скрытого текста не рекомендуется. Любой пользователь, выполняющий эту команду в сценарии или заглядывающий через ваше плечо, сможет узнать пароль DSRM этого доменного контроллера.  Все, кто имеет доступ к файлу, сможет восстановить Скрытый пароль. Зная пароль они могут войти в контроллер домена запущен в режиме DSRM и персонифицировать сам контроллер домена, повысив уровень собственных привилегий самый высокий уровень в составе леса AD. Дополнительный набор действия, используя **System.Security.Cryptography** для шифрования текстового файла данных рекомендуется, но вне области действия. Рекомендуется полностью отказаться от хранения паролей.  
  
### <a name="rodc-options"></a>Параметры RODC  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCOptions.png)  
  
**Параметры RODC** странице можно изменить параметры:  
  
-   Делегированная учетная запись администратора  
  
-   Учетные записи, которым разрешено реплицировать пароли в RODC.  
  
-   Учетные записи, которым запрещено реплицировать пароли в RODC.  
  
Делегированные учетные записи администратора получают локальные права администратора для RODC. Эти пользователи имеют привилегии группы администраторов локального компьютера.  Они не являются членами группы администраторов домена или встроенной группы администраторов домена. Этот параметр полезен при делегировании администрирования филиалом без выдачи разрешения на администрирование домена. Настройка делегирования прав администратора не требуется.  
  
— Эквивалентный аргумент ADDSDeployment Windows PowerShell:  
  
```  
-delegatedadministratoraccountname <string>  
```  
  
Учетные записи, которые не разрешено кэшировать пароли в контроллере RODC и не могут подключаться и проверки подлинности для записи контроллеру домена не имеют доступа к ресурсам и функциональным возможностям Active Directory.  
  
> [!IMPORTANT]  
> Если не изменяется, используются группы по умолчанию и параметры:  
>   
> -   Администраторы — запретить  
> -   Операторы сервера — запретить  
> -   Операторы архива — запретить  
> -   Операторы учета — запретить  
> -   Отказано в группу репликации паролей RODC — запретить  
> -   Группа репликации паролей RODC — разрешить  
  
Эквивалентные аргументы ADDSDeployment Windows PowerShell являются:  
  
```  
-allowpasswordreplicationaccountname <string []>  
-denypasswordreplicationaccountname <string []>  
```  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_SelectDelAdmin.png)  
  
### <a name="additional-options"></a>Дополнительные параметры  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCAdditionalOptions.png)  
  
**Дополнительные параметры** страница содержит параметры конфигурации для имя контроллера домена в качестве источника репликации, или можно использовать любой контроллер домена в качестве источника репликации.  
  
Также можно установить контроллер домена с помощью архивированных носителей, использовав параметр установки с носителя (IFM). **Установки с носителя** флажок предоставляет возможность выбора, и вам необходимо щелкнуть **проверка** чтобы убедиться, что предоставленный путь является действительным носителем. Носители, используемые параметром IFM создается с помощью архивации данных Windows Server или Ntdsutil.exe только из другого существующего Windows Server 2012 компьютера; Windows Server 2008 R2 или предыдущей версии операционной системы нельзя использовать для создания носителей для контроллера домена Windows Server 2012.  Дополнительные сведения об изменениях в IFM приложения. Если носители защищены SYSKEY, диспетчер сервера запрашивает пароль образа во время проверки.  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_PSIFM.png)  
  
Ниже перечислены аргументы командлета ADDSDeployment Дополнительные параметры  
  
```  
-replicationsourcedc <string>  
-installationmediapath <string>  
-systemkey <secure string>  
```  
  
### <a name="paths"></a>Пути  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCPaths.png)  
  
**Пути** страницы позволяет переопределить расположение папок по умолчанию для базы данных AD DS, журналов транзакций базы данных и общего доступа к SYSVOL. Расположение по умолчанию, всегда в подкаталогах % systemroot %. **Пути** аргументы командлета ADDSDeployment:  
  
```  
-databasepath <string>  
-logpath <string>  
-sysvolpath <string>  
```  
  
### <a name="preparation-options"></a>Параметры подготовки  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCPrepOptions.png)  
  
**Параметры подготовки** страницы предупреждает, что конфигурация Доменных службах Active Directory включает в себя расширение схемы (forestprep) и обновление домена (domainprep). Только вы видите эту страницу, если лес или домен не были подготовлены с предыдущей установки контроллера домена Windows Server 2012 или путем запуска Adprep.exe вручную. Например мастер настройки доменных служб Active Directory подавляет эту страницу, при добавлении новой реплики контроллера домена в существующий корневой домен леса Windows Server 2012.  
  
Расширение схемы и обновление домена не производятся после нажатия **Далее**. Эти операции выполняются только во время этапа установки. На этой странице просто сообщается о событиях, которые будут происходить позднее в ходе установки.  
  
На этой странице также проверяется, учетные данные текущего пользователя, члены групп "Администраторы схемы" и "Администраторы предприятия", необходимо членство в этих группах для расширения схемы и подготовки домена. Нажмите кнопку **изменение** для предоставления учетных данных пользователя, если на странице указано, что текущие учетные данные не дают необходимых разрешений.  
  
Дополнительные параметры командлета addsdeployment таков:  
  
```  
-adprepcredential <pscredential>  
```  
  
> [!IMPORTANT]  
> Как в предыдущих версиях Windows Server, Windows Server 2012 автоматической подготовке домена не запускается средство GPPREP. Запустите **adprep.exe/gpprep** вручную для всех доменов, которые не были ранее подготовлены для Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2. Необходимо запустить средство GPPrep только один раз за историю домена, а не при каждом обновлении. Adprep.exe не выполняет команду/gpprep автоматически, так как его работы может привести к все файлы и папки в папке SYSVOL будет повторно реплицировано во всех контроллерах домена.  
>   
> RODCPrep запускается автоматически при повышении роли первого контроллера RODC без предварительной подготовки в домене. Этого не происходит при повышении роли первого доступного для записи контроллера домена Windows Server 2012. Можно также вручную запустить **adprep.exe/rodcprep** Если планируется развертывать контроллеры домена только для чтения.  
  
### <a name="review-options-and-view-script"></a>Просмотрите параметры и просмотреть сценарий  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCReviewOptions.png)  
  
**Просмотреть параметры** странице можно проверить параметры и убедитесь, что они отвечают требованиям, прежде чем начать установку. Это последняя возможность прервать установку, с помощью диспетчера сервера. На этой странице просто позволяет просмотреть и подтвердить параметры перед продолжением настройки.  
  
**Просмотреть параметры** страницу в диспетчере сервера расположена дополнительная **просмотреть сценарий** кнопку, чтобы создать текстовый файл в кодировке Юникод, содержащего текущую конфигурацию развертывания ADDSDeployment в виде единого скрипта Windows PowerShell. Это позволяет использовать графический интерфейс диспетчера сервера в качестве студии развертывания Windows PowerShell. Используйте мастер настройки доменных служб Active Directory, чтобы настроить параметры, экспортировать конфигурацию и затем отменить мастер. Этого процесса создается допустимый и синтаксически верный образец для дальнейшего изменения или прямого использования. Например:  
  
```  
#  
# Windows PowerShell Script for AD DS Deployment  
#  
  
Import-Module ADDSDeployment  
Install-ADDSDomainController `  
-AllowPasswordReplicationAccountName @("CORP\Allowed RODC Password Replication Group", "CORP\Chicago RODC Admins", "CORP\Chicago RODC Users and Computers") `  
-Credential (Get-Credential) `  
-CriticalReplicationOnly:$false `  
-DatabasePath "C:\Windows\NTDS" `  
-DelegatedAdministratorAccountName "CORP\Chicago RODC Admins" `  
-DenyPasswordReplicationAccountName @("BUILTIN\Administrators", "BUILTIN\Server Operators", "BUILTIN\Backup Operators", "BUILTIN\Account Operators", "CORP\Denied RODC Password Replication Group") `  
-DomainName "corp.contoso.com" `  
-InstallDNS:$true `  
-LogPath "C:\Windows\NTDS" `  
-ReadOnlyReplica:$true `  
-SiteName "Default-First-Site-Name" `  
-SYSVOLPath "C:\Windows\SYSVOL"  
-Force:$true  
  
```  
  
> [!NOTE]  
> Диспетчер сервера обычно задает все значения аргументов при повышении роли, не зависит от значения по умолчанию (как они могут изменяться в будущих версиях Windows или пакетах обновления). Единственным исключением является **- safemodeadministratorpassword** аргумент. Для принудительного вывода запроса на подтверждение, не указывайте значение при интерактивном выполнении командлета.  
  
Используйте необязательный аргумент Whatif с помощью командлета Install-ADDSDomainController для просмотра сведений о конфигурации. Это позволяет просмотреть явные и неявные значения аргументов командлета.  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCWhatIf.png)  
  
### <a name="prerequisites-check"></a>Проверка готовности к установке  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCPrereqCheck.png)  
  
**Проверка предварительных требований** — это новая функция в конфигурации домена AD DS. На этом новом этапе проверяется конфигурации сервера возможность поддержки нового леса AD DS.  
  
При установке нового корневого домена леса, Server Manager Active Directory домена мастер настройки служб вызывает ряд сериализованных модульных тестов. Эти предлагаются рекомендуемые способы восстановления. Тесты можно выполнять необходимое число раз. Домен контроллера не может продолжаться, пока все проверки предварительных требований передачи.  
  
**Проверка предварительных требований** также поверхности важные сведения, такие как изменения безопасности, затрагивающих предыдущие операционные системы.  
  
Нельзя **проверка готовности к установке** при с помощью диспетчера сервера, но вы можете пропустить при использовании командлета развертывания AD DS, с помощью следующего аргумента:  
  
```  
-skipprechecks  
  
```  
  
Нажмите кнопку **установить** начинается процесс повышения роли контроллера домена. Это последняя возможность отменить установку. Процесс повышения роли нельзя отменить после ее начала. По завершении повышения роли, вне зависимости от результата повышения роли компьютер перезагрузится автоматически.  
  
### <a name="installation"></a>Установка  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCInstallation.png)  
  
Когда **установки** отображает страницу, конфигурации контроллера домена начинается и невозможно остановить или отменить. Подробная информация об операциях выводится на этой странице и записывается в журналы:  
  
-   %systemroot%\debug\dcpromo.log  
  
-   %systemroot%\debug\dcpromoui.log  
  
Чтобы установить новый лес Active Directory, с помощью модуля ADDSDeployment, используйте следующий командлет:  
  
```  
Install-addsdomaincontroller  
  
```  
  
В разделе **командлет ADDSDeployment** таблицы в начале этого раздела для обязательных и необязательных аргументов.  
  
**Install-addsdomaincontroller** командлет включает только два этапа (проверка предварительных требований и установка). На двух иллюстрациях ниже показан этап установки с минимальным необходимым набором аргументов **- domainname**, **- readonlyreplica**, **- sitename**, и **-credential**. Обратите внимание, что так же, как диспетчер сервера **Install-ADDSDomainController** напоминает о том, что автоматической перезагрузке повышения роли сервера:  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_PSInstallRODC.png)  
  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_PSInstallRODCProgress.png)  
  
Чтобы напоминание о перезагрузке автоматически, используйте **-принудительно** или **-подтверждение: $false** аргументы с любым командлетом ADDSDeployment Windows PowerShell. Чтобы предотвратить автоматическую перезагрузку по завершении повышения роли сервера, используйте **- norebootoncompletion** аргумент.  
  
> [!WARNING]  
> Отключать перезагрузку не рекомендуется. Для правильной работы контроллер домена должен перезагрузиться. Если выйти из контроллера домена, вы не может снова войти в интерактивном режиме до ее перезапуска.  
  
### <a name="results"></a>Результаты  
![Установить RODC](media/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-/ADDS_SMI_TR_RODCSignoff.png)  
  
**Результатов** странице отображается успешном или неудачном повышение роли, а также все важные данные администратора. Контроллер домена автоматически перезагрузится через 10 секунд.  
  

