---
ms.assetid: ae241ed8-ef19-40a9-b2d5-80b8391551ff
title: "Установка доменных служб Active Directory (уровень 100)"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: f76aa1e5200a9fc2f47a559c4a318aa619d31557
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="install-active-directory-domain-services-level-100"></a>Установка доменных служб Active Directory (уровень 100)

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе описан процесс установки AD DS в Windows Server 2012 с помощью любого из следующих методов:  
  
-   [Требования к учетным данным для запуска Adprep.exe и установки доменных служб Active Directory](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_Creds)  
  
-   [Установка AD DS с помощью Windows PowerShell](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_PS)  
  
-   [Установка AD DS с помощью диспетчера сервера](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_GUI)  
  
-   [Выполнение поэтапной установки RODC с помощью графического пользовательского интерфейса](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_UIStaged)  
  
## <a name="BKMK_Creds"></a>Требования к учетным данным для запуска Adprep.exe и установки доменных служб Active Directory  
Для запуска Adprep.exe и установки в Доменных службах Active Directory необходимы следующие учетные данные.  
  
-   Чтобы установить новый лес, необходимо войти как локального администратора на компьютере.  
  
-   Чтобы установить новый дочерний домен или новое доменное дерево, необходимо войти как член группы администраторов предприятия.  
  
-   Для установки дополнительного контроллера домена в существующий домен, необходимо быть членом группы администраторов домена.  
  
    > [!NOTE]  
    > Если вы команда adprep.exe запущена не отдельно и установке первого контроллера домена под управлением Windows Server 2012 в существующем домене или лесу, будет предложено ввести учетные данные для выполнения команд Adprep. Требуются учетные данные следующим образом:  
    >   
    > -   Для установки первого контроллера домена Windows Server 2012 в лесу, необходимо ввести учетные данные члена группы администраторов предприятия, группу администраторов схемы и группы администраторов домена, в домене, на котором размещается хозяин схемы.  
    > -   Для установки первого контроллера домена Windows Server 2012 в домене, необходимо ввести учетные данные члена группы "Администраторы домена".  
    > -   Для установки первого контроллера домена только для чтения (RODC) в лесу, необходимо ввести учетные данные члена группы администраторов предприятия.  
    >   
    >     > [!NOTE]  
    >     > Если команда adprep/rodcprep уже выполнялась в Windows Server 2008 или Windows Server 2008 R2, запустите его снова для Windows Server 2012 не нужно.  
  
## <a name="BKMK_PS"></a>Установка AD DS с помощью Windows PowerShell  
Начиная с Windows Server 2012, можно установить AD DS с помощью Windows PowerShell. Dcpromo.exe устарел начиная с Windows Server 2012, но по-прежнему можно запустить dcpromo.exe с использованием файла ответов (dcpromo / unattend:<answerfile> или dcpromo/Answer:<answerfile>). Возможность продолжить выполнение dcpromo.exe с файлом ответов предоставляет организациям, в которых есть ресурсы, которые вложили средства в существующих автоматизации время на преобразование автоматизации с dcpromo.exe в Windows PowerShell. Дополнительные сведения о выполнении dcpromo.exe с файлом ответов см. в разделе [https://support.microsoft.com/kb/947034](https://support.microsoft.com/kb/947034).  
  
Дополнительные сведения об удалении AD DS с помощью Windows PowerShell см. в разделе [удалить AD DS с помощью Windows PowerShell](assetId:///99b97af0-aa7e-41ed-8c81-4eee6c03eb4c#BKMK_RemovePS).  
  
Начните с добавления роли с помощью Windows PowerShell. Эта команда устанавливает роль сервера AD DS и AD DS и AD LDS средств администрирования серверов, включая такие Active Directory-пользователи и компьютеры средства на базе графического интерфейса и программы командной строки, например, dcdia.exe. Средства администрирования сервера не устанавливаются по умолчанию при использовании Windows PowerShell. Необходимо указать **» IncludeManagementTools** для управления локальным сервером или установить [средства удаленного администрирования сервера](https://www.microsoft.com/download/details.aspx?id=28972) для управления удаленным сервером.  
  
```  
Install-windowsfeature -name AD-Domain-Services -IncludeManagementTools  
<<Windows PowerShell cmdlet and arguments>>  
```  
  
Нет перезагрузка потребуется только после завершения установки AD DS.  
  
Затем можно выполнить следующую команду, чтобы просмотреть доступные командлеты в модуле ADDSDeployment.  
  
```  
Get-Command -Module ADDSDeployment
```  
  
Чтобы просмотреть список аргументов, которые можно указывать для командлетов и синтаксиса:  
  
```  
Get-Help <cmdlet name>  
```  
  
Например чтобы просмотреть аргументы для создания незанятой только для чтения (RODC) контроллера учетной записи домена, введите  
  
```  
Get-Help Add-ADDSReadOnlyDomainControllerAccount
```  
  
Дополнительные аргументы приведены в квадратных скобках.  
  
Можно также загрузить новые примеры справки и концепции, реализованные в командлеты Windows PowerShell. Дополнительные сведения см. в разделе [about_Updatable_Help](https://technet.microsoft.com/library/hh847735.aspx).  
  
Командлеты Windows PowerShell можно выполнять на удаленных серверах:  
  
-   В Windows PowerShell используйте Invoke-Command с командлетом ADDSDeployment. Например для установки AD DS на удаленном сервере с именем ConDC3 в домене contoso.com, введите следующую команду:  
  
    ```  
    Invoke-Command { Install-ADDSDomainController -DomainName contoso.com -Credential (Get-Credential) } -ComputerName ConDC3  
    ```  
  
- или -  
  
-   В диспетчере серверов создайте группу серверов, включающую удаленный сервер. Щелкните правой кнопкой мыши имя удаленного сервера и нажмите кнопку **Windows PowerShell**.  
  
В следующем разделе описан способ выполнения командлетов модуля ADDSDeployment для установки служб AD DS.  
  
-   [Аргументы командлета ADDSDeployment](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_Params)  
  
-   [Указание учетных данных Windows PowerShell](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_PSCreds)  
  
-   [Использование тестовых командлетов](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_TestCmdlets)  
  
-   [Установка нового корневого домена леса с помощью Windows PowerShell](../../ad-ds/deploy/../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_PSForest)  
  
-   [Установка нового дочернего домена или домена дерева с помощью Windows PowerShell](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_PSDomain)  
  
-   [Установка контроллера домена дополнительных (реплики) с помощью Windows PowerShell](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_PSReplica)  
  
### <a name="BKMK_Params"></a>Аргументы командлета ADDSDeployment  
В следующей таблице перечислены аргументы командлетов ADDSDeployment в Windows PowerShell. Аргументы, выделенные жирным шрифтом являются обязательными. Эквивалентные аргументы для dcpromo.exe указаны в скобках, если они называются в Windows PowerShell.  
  
Допускается использование в параметрах Windows PowerShell аргументов $TRUE и $FALSE. Аргументы, которые являются $TRUE по умолчанию, указывать не требуется.  
  
Для переопределения значений по умолчанию, можно указать аргумент со значением $False. Например так как **- installdns** автоматически выполнять для установки нового леса, если он не указан, единственным способом *предотвратить* установку DNS при установке нового леса — это использовать:  
  
```  
-InstallDNS:$false  
```  
  
Аналогично поскольку **» installdns** имеет значение $False по умолчанию при установке контроллера домена в среде, где сервер Windows DNS сервера, необходимо указать следующий аргумент для установки DNS-сервера:  
  
```  
-InstallDNS:$true  
```  
  
|Аргумент|Описание|  
|------------|---------------|  
|**ADPrepCredential <PS Credential> ** **Примечание:** обязательным при установке первого контроллера домена Windows Server 2012 в домене или лесу и учетные данные текущего пользователя недостаточны для выполнения операции.|Указывает учетную запись члена группы "Администраторы предприятия" и "Администраторы схемы", которая может подготовить лес, в соответствии с правилами [Get-Credential](https://technet.microsoft.com/library/dd315327.aspx) и объектом PSCredential.<br /><br />Если значение не указано, значение **«credential** используется аргумент.|  
|AllowDomainControllerReinstall|Указывает, следует ли продолжать ли установку контроллера домена с возможностью записи, несмотря на то, что обнаружено другую учетную запись контроллера домена с возможностью записи, с тем же именем.<br /><br />Используйте **$True** только в том случае, если вы уверены, что учетная запись не используется в настоящее время другой контроллер домена с возможностью записи.<br /><br />Значение по умолчанию — **$False**.<br /><br />Этот аргумент неприменим для RODC.|  
|AllowDomainReinstall|Указывает, воссоздается ли существующий домен.<br /><br />Значение по умолчанию — **$False**.|  
|AllowPasswordReplicationAccountName < string [] >|Указывает имена учетных записей пользователей, учетные записи групп и учетных записей компьютеров, чьи пароли могут быть реплицированы на данном RODC. Используйте пустую строку «» Если вы хотите сохранить пустое значение. По умолчанию разрешен только допустимое группа репликации паролей RODC и изначально создается пустой.<br /><br />Введите значения в виде строкового массива. Например:<br /><br />Код - AllowPasswordReplicationAccountName «JSmith», «JSmithPC», «Филиала пользователи»|  
|ApplicationPartitionsToReplicate < string [] > **Примечание:** существует в пользовательском Интерфейсе эквивалентного параметра нет. Если устанавливается с помощью пользовательского интерфейса, с помощью IFM, то все разделы приложений будут реплицированы.|Указывает разделы каталога приложений для репликации. Этот аргумент применяется только в том случае, если указать **- InstallationMediaPath** аргумент для установки с носителя (IFM). По умолчанию все приложения будут реплицироваться разделов на основании собственных областей.<br /><br />Введите значения в виде строкового массива. Например:<br /><br />Кода.<br /><br />-ApplicationPartitionsToReplicate «partition1», «partition2», «partition3»|  
|Подтверждение|Запрашивает подтверждение перед выполнением командлета.|  
|CreateDnsDelegation **Примечание:** этот аргумент нельзя указывать при выполнении командлета Add-ADDSReadOnlyDomainController.|Указывает, следует ли создавать делегирование DNS со ссылкой на новый сервер DNS, который устанавливается вместе с контроллером домена. Допустимые для Active Directory» интегрированного только. Записи делегирования могут создаваться только на DNS-серверах Майкрософт, сети и доступен. Записи делегирования невозможно создавать для доменов, подчиненных непосредственно доменов верхнего уровня, например .com, .gov, .biz, .edu или доменов двухбуквенных кода, например, .nz и .au.<br /><br />Значение по умолчанию определяется автоматически на основании среды.|  
|**Учетные данные <PS Credential> ** **Примечание:** является обязательным, только если учетные данные текущего пользователя недостаточны для выполнения операции.|Указывает учетную запись домена, которая может подключаться к домену, в соответствии с правилами [Get-Credential](https://technet.microsoft.com/library/dd315327.aspx) и объектом PSCredential.<br /><br />Если значение не указано, используются учетные данные текущего пользователя.|  
|CriticalReplicationOnly|Указывает ли операции установки Доменных службах Active Directory выполнить только критичную репликацию перед перезагрузкой компьютера, а затем продолжит работу. Некритическая репликация выполняется после завершения установки и перезагрузки компьютера.<br /><br />Использовать этот аргумент не рекомендуется.<br /><br />Не существует эквивалента для этого параметра в интерфейсе пользователя (UI).|  
|Путь к базе данных <string>|Указывает полное не «путь имен (UNC) к каталогу на фиксированном диске локального компьютера, на котором хранится база данных домена, например, **C:\Windows\NTDS.**<br /><br />Значение по умолчанию — **%SYSTEMROOT%\NTDS**. **Важно:** можно хранить файлы базы данных и журнала AD DS на томе, отформатированном Resilient File System (ReFS), существует особых преимуществ от размещения AD DS на ReFS нет, только обычные преимущества от устойчивости получить размещения любой данных на ReFS.|  
|DelegatedAdministratorAccountName <string>|Указывает имя пользователя или группы, которые могут устанавливать и администрирования RODC.<br /><br />По умолчанию только члены группы "Администраторы домена" могут администрирование RODC.|  
|DenyPasswordReplicationAccountName < string [] >|Указывает имена учетных записей пользователей, учетные записи групп и учетных записей компьютеров, чьи пароли, не реплицируются на данном RODC. Используйте пустую строку «» Если не нужно запрещать репликацию учетных данных всех пользователей или компьютеров. По умолчанию запрещен Администраторы, операторы сервера, операторы архива, операторов учета и отказано в группу репликации паролей RODC. По умолчанию отказано в группу репликации паролей RODC включает издателей сертификатов, "Администраторы домена", "Администраторы предприятия", контроллеры домена предприятия, контроллеры домена только для чтения предприятия, владельцы-создатели групповой политики, учетной записи krbtgt и администраторов схемы.<br /><br />Введите значения в виде строкового массива. Например:<br /><br />Кода.<br /><br />-DenyPasswordReplicationAccountName «RegionalAdmins», «AdminPCs»|  
|DnsDelegationCredential <PS Credential> **Примечание:** этот аргумент нельзя указывать при выполнении командлета Add-ADDSReadOnlyDomainController.|Указывает имя пользователя и пароль для создания делегирования DNS в соответствии с правилами [Get-Credential](https://technet.microsoft.com/library/dd315327.aspx) и объектом PSCredential.|  
|DomainMode <DomainMode> {Win2003 & #124; Win2008 & #124; Win2008R2 & #124; Win2012 & #124; Win2012R2}<br /><br />Или<br /><br />DomainMode <DomainMode> {2 & #124; 3 & #124; 4 & #124; 5 & #124; 6}|Указывает режим работы домена во время создания нового домена.<br /><br />Режим работы домена не может быть ниже режима работы леса, но может быть выше.<br /><br />Значение по умолчанию определяется автоматически и на уровне существующего режима работы леса или значение, заданное для **- ForestMode**.|  
|**Имя_домена**<br /><br />Обязательно для командлетов Install-ADDSForest и Install-ADDSDomainController.|Указывает полное имя домена, в котором требуется установить дополнительный контроллер домена.|  
|**DomainNetbiosName <string>**<br /><br />Обязательно для Install-ADDSForest, если имя префикса полного Доменного имени превышает 15 символов.|Используется с Install-ADDSForest. Присваивает NetBIOS-имя нового корневого домена леса.|  
|DomainType <DomainType> {ChildDomain & #124; TreeDomain} или {дочерних & #124; дерева}|Указывает тип создаваемого домена, который вы хотите создать: новое дерево домена в существующем лесе, дочерний существующем домене или новый лес.<br /><br />По умолчанию для domaintype принимается значение ChildDomain.|  
|Принудительное|Если этот параметр указан, любые предупреждения, которые могут обычно отображаться во время установки и добавления контроллера домена, будут блокироваться, чтобы разрешить командлету завершить выполнение. Этот параметр можно использовать при создании сценария установки.|  
|ForestMode <ForestMode> {Win2003 & #124; Win2008 & #124; Win2008R2 & #124; Win2012 & #124; Win2012R2}<br /><br />Или<br /><br />ForestMode <ForestMode> {2 & #124; 3 & #124; 4 & #124; 5 & #124; 6}|Указывает режим работы леса, при создании нового леса.<br /><br />Значение по умолчанию — Win2012.|  
|InstallationMediaPath|Указывает расположение установочного носителя, который будет использоваться для установки нового контроллера домена.|  
|InstallDns|Включение установлена и настроена на контроллере домена службу DNS-сервера.<br /><br />Для нового леса значение по умолчанию — **$True** и DNS-сервер устанавливается.<br /><br />Для нового дочернего домена или доменного дерева Если родительский домен (или корневого домена леса доменного дерева) уже содержит и хранит DNS-имена домена, то по умолчанию для этого параметра принимается $True.<br /><br />Для установки контроллера домена в существующий домен, если этот параметр не указан, и текущий домен уже содержит и хранит DNS-имена домена, то по умолчанию для этого параметра — **$True**. В противном случае, если доменные имена DNS размещаются вне Active Directory, по умолчанию используется **$False** и DNS-сервер устанавливается.|  
|LogPath <string>|Указывает полный путь не в формате UNC к каталогу на фиксированном диске локального компьютера, содержащий файлы журнала домена, например, **C:\Windows\Logs**.<br /><br />Значение по умолчанию — **%SYSTEMROOT%\NTDS**. **Важно:** не храните файлы журнала Active Directory на томе данных, отформатированном Resilient File System (ReFS).|  
|MoveInfrastructureOperationMasterRoleIfNecessary|Указывает, следует ли переносить инфраструктуры главную роль хозяина операций (известные также как гибкие операции с единым хозяином или FSMO) контроллера домена, который вы создаете «в случае, он в настоящий момент размещен на сервере глобального каталога», и вы не планируете превращение создаваемого контроллера домена создаются с сервером глобального каталога. Укажите этот параметр для переноса роли хозяина инфраструктуры на контроллер домена, который вы создаете на случай, если такой перенос необходим; в этом случае укажите **NoGlobalCatalog** вариант, если вы хотите, чтобы оставаться, где в настоящее время является роль хозяина инфраструктуры.|  
|**NewDomainName <string> ** **Примечание:** требуется только для Install-ADDSDomain.|Указывает имя одного домена для нового домена.<br /><br />Например, если вы хотите создать новый дочерний домен с именем **emea.corp.fabrikam.com**, следует указать **emea** в качестве значения этого аргумента.|  
|**NewDomainNetbiosName <string>**<br /><br />Обязательно для Install-ADDSDomain, если имя префикса полного Доменного имени превышает 15 символов.|Используется с Install-ADDSDomain. Присваивает NetBIOS-имя нового домена. Значение по умолчанию является производным от значение **» NewDomainName**.|  
|NoDnsOnNetwork|Указывает, что служба DNS не доступен в сети. Этот параметр используется только в том случае, если параметра IP сетевого адаптера этого компьютера не настроено имя DNS-сервера для разрешения имен. Оно означает, что DNS-сервер будет установлен на этом компьютере, для разрешения имен. В противном случае параметры IP сетевого адаптера, необходимо сначала настроить адрес DNS-сервера.<br /><br />Пропуск этого параметра (по умолчанию) указывает, что параметры клиента TCP/IP сетевого адаптера на этом сервере будет использоваться для связи с DNS-сервера. Таким образом Если этот параметр не задан, убедитесь, сначала настроить параметры клиента TCP/IP с адрес предпочитаемого DNS-сервера.|  
|NoGlobalCatalog|Указывает, что контроллер домена является сервером глобального каталога не должен.<br /><br />Контроллеры домена под управлением Windows Server 2012 устанавливаются с глобальным каталогом по умолчанию. Другими словами Эта процедура выполняется автоматически без вспомогательных вычислений, если не указано:<br /><br />Кода.<br /><br />-NoGlobalCatalog|  
|NoRebootOnCompletion|Указывает, следует ли перезапустить компьютер после завершения выполнения команды независимо от результата. По умолчанию компьютер будет перезагружен. Чтобы блокировать перезагрузку сервера, укажите следующее:<br /><br />Кода.<br /><br />-NoRebootOnCompletion: $True<br /><br />Не существует эквивалента для этого параметра в интерфейсе пользователя (UI).|  
|**ParentDomainName <string> ** **Примечание:** является обязательным для командлета Install-ADDSDomain|Указывает полное доменное имя существующего родительского домена. Этот аргумент используется при установке дочернего домена или нового доменного дерева.<br /><br />Например, если вы хотите создать новый дочерний домен с именем **emea.corp.fabrikam.com**, следует указать **corp.fabrikam.com** в качестве значения этого аргумента.|  
|ReadOnlyReplica|Указывает, следует ли устанавливать контроллер домена только для чтения (RODC).|  
|ReplicationSourceDC <string>|Указывает полное доменное имя партнерского контроллера домена, с которого реплицируется информация домена. По умолчанию вычисляется автоматически.|  
|**SafeModeAdministratorPassword <securestring>**|Предоставляет пароль для учетной записи администратора при запуске компьютера в безопасном режиме или разновидности безопасного режима, например в режиме восстановления служб каталогов.<br /><br />По умолчанию используется пустой пароль. Необходимо ввести пароль. Пароль следует вводить в формате System.Security.SecureString, например, предоставленных read-host - assecurestring или ConvertTo-SecureString.<br /><br />Аргумент SafeModeAdministratorPassword действует особым: Если аргумент не указан, командлет предлагает ввести и подтвердить Скрытый пароль. Это предпочтительный вариант использования при интерактивном выполнении командлета. Если указан без значения и нет других аргументы не указан в командлет, командлет предложит ввести Скрытый пароль без подтверждения. Это не является предпочтительным при интерактивном выполнении командлета. Если указано значение, значение должно быть защищенной строкой. Это не является предпочтительным при интерактивном выполнении командлета. Например, можно вручную ввести запрос пароля с помощью командлета Read-Host, чтобы предложить пользователю ввести защищенную строку:-safemodeadministratorpassword (чтение host - строки «пароль:» - assecurestring) можно также ввести защищенную строку в переменной с преобразованным открытым текстом, хотя это не рекомендуется. -safemodeadministratorpassword (convertto-securestring «Пароль1» - asplaintext-force)|  
|**SiteName <string>**<br /><br />Является обязательным для командлета Add-addsreadonlydomaincontrolleraccount|Указывает сайт, где устанавливается контроллер домена. Существует не **«sitename** аргумент при запуске **Install-ADDSForest** так как первым создается сайт по умолчанию-First-Site-Name.<br /><br />Имя сайта уже должно существовать на момент ввода в качестве аргумента для **- sitename**. Командлет этот сайт не создает.|  
|SkipAutoConfigureDNS|Пропуск автоматической настройки параметров клиента DNS, серверов пересылки и корневых ссылок. Этот аргумент действует только, если служба DNS-сервера уже установлена или автоматически устанавливаются вместе с **- InstallDNS**.|  
|SystemKey <string>|Указывает системный ключ для носителя, с которого реплицируются данные.<br /><br />Значение по умолчанию — **нет**.<br /><br />Данные должны быть в формате, предоставленном командой read-host - assecurestring или ConvertTo-SecureString.|  
|SysvolPath <string>|Указывает полный путь не в формате UNC к каталогу на фиксированном диске локального компьютера, например, **C:\Windows\SYSVOL**.<br /><br />Значение по умолчанию — **%SYSTEMROOT%\SYSVOL**. **Важно:** SYSVOL не может храниться на томе данных, отформатированном Resilient File System (ReFS).|  
|SkipPreChecks|Не выполняется проверка необходимых компонентов до начала установки. Не рекомендуется использовать этот параметр.|  
|WhatIf|Показывает, что произойдет при запуске командлета. Командлет не запущен.|  
  
### <a name="BKMK_PSCreds"></a>Указание учетных данных Windows PowerShell  
Можно указать учетные данные, не отображая их в виде простого текста на экране с помощью [Get-credential](https://technet.microsoft.com/library/dd315327.aspx).  
  
Операция - SafeModeAdministratorPassword и LocalAdministratorPassword аргументы специальные:  
  
-   Если аргумент не указан, командлет предлагает ввести и подтвердить Скрытый пароль. Это предпочтительный вариант использования при интерактивном выполнении командлета.  
  
-   Если указано значение, значение должно быть защищенной строкой. Это не является предпочтительным при интерактивном выполнении командлета.  
  
Например, можно вручную ввести запрос пароля с помощью **Read-Host** командлету предложить пользователю ввести защищенную строку  
  
```  
-SafeModeAdministratorPassword (Read-Host -Prompt "DSRM Password:" -AsSecureString)
```  
  
> [!WARNING]  
> Поскольку в предыдущем варианте пароль не подтверждается, соблюдайте повышенную осторожность: пароль невидим.  
  
Можно также ввести защищенную строку в переменной с преобразованным открытым текстом, хотя использовать такой вариант настоятельно не рекомендуется:  
  
```  
-SafeModeAdministratorPassword (ConvertTo-SecureString "Password1" -AsPlainText -Force)
```  
  
> [!WARNING]  
> Ввод или хранение пароля в виде открытого текста не рекомендуется. Любой пользователь, выполняющий эту команду в сценарии или заглядывающий через ваше плечо, сможет узнать пароль DSRM этого доменного контроллера. Зная пароль они персонифицировать сам контроллер домена и повысить уровень собственных привилегий самый высокий уровень в лесу Active Directory.  
  
### <a name="BKMK_TestCmdlets"></a>Использование тестовых командлетов  
Для каждого командлета ADDSDeployment предусмотрен соответствующий тестовый командлет. Тестовые командлеты выполняют только проверку необходимых компонентов для проведения установки; параметры установки, не настроены. Аргументы для каждого тестового командлета являются так же, как и для соответствующего командлета установки, но **» SkipPreChecks** недоступно для тестирования командлетов.  
  
|Тестовый командлет|Описание|  
|---------------|---------------|  
|Test-ADDSForestInstallation|Выполняет необходимые условия для установки нового леса Active Directory.|  
|Test-ADDSDomainInstallation|Выполняет необходимые условия для установки нового домена в Active Directory.|  
|Test-ADDSDomainControllerInstallation|Выполняет необходимые условия для установки контроллера домена в Active Directory.|  
|Test-ADDSReadOnlyDomainControllerAccountCreation|Выполняет необходимые условия для добавления контроллера домена только для чтения (RODC) учетной записи.|  
  
### <a name="BKMK_PSForest"></a>Установка нового корневого домена леса с помощью Windows PowerShell  
Синтаксис команд для установки нового леса выглядит следующим образом. Дополнительные аргументы приведены в квадратных скобках.  
  
```  
Install-ADDSForest [-SkipPreChecks] -DomainName <string> -SafeModeAdministratorPassword <SecureString> [-CreateDNSDelegation] [-DatabasePath <string>] [-DNSDelegationCredential <PS Credential>] [-NoDNSOnNetwork] [-DomainMode <DomainMode> {Win2003 | Win2008 | Win2008R2 | Win2012}] [-DomainNetBIOSName <string>] [-ForestMode <ForestMode> {Win2003 | Win2008 | Win2008R2 | Win2012}] [-InstallDNS] [-LogPath <string>] [-NoRebootOnCompletion] [-SkipAutoConfigureDNS] [-SYSVOLPath] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]  
```  
  
> [!NOTE]  
> Аргумент - DomainNetBIOSName является обязательным, если требуется изменить 15-значное имя, созданное автоматически на основе префикса имени домена DNS или если длина имени превышает 15 символов.  
  
Например чтобы установить новый лес с именем corp.contoso.com и запрашивать пароль DSRM для доступа, введите следующую команду:  
  
```  
Install-ADDSForest -DomainName "corp.contoso.com"   
```  
  
> [!NOTE]  
> DNS-сервер устанавливается по умолчанию при выполнении командлета Install-ADDSForest.  
  
Чтобы установить новый лес с именем corp.contoso.com, создайте делегирование DNS в домене contoso.com, задайте режим работы домена до Windows Server 2008 R2 и режим работы леса до Windows Server 2008, установите базу данных Active Directory и SYSVOL на диск D:\, установите файлы журнала на диск E:\ и быть запроса на ввод пароля для режима восстановления служб каталогов и введите :  
  
```  
Install-ADDSForest -DomainName corp.contoso.com -CreateDNSDelegation -DomainMode Win2008 -ForestMode Win2008R2 -DatabasePath "d:\NTDS" -SYSVOLPath "d:\SYSVOL" -LogPath "e:\Logs"   
```  
  
### <a name="BKMK_PSDomain"></a>Установка нового дочернего домена или домена дерева с помощью Windows PowerShell  
Синтаксис команд для установки нового домена выглядит следующим образом. Дополнительные аргументы приведены в квадратных скобках.  
  
```  
Install-ADDSDomain [-SkipPreChecks] -NewDomainName <string> -ParentDomainName <string> -SafeModeAdministratorPassword <SecureString> [-ADPrepCredential <PS Credential>] [-AllowDomainReinstall] [-CreateDNSDelegation] [-Credential <PS Credential>] [-DatabasePath <string>] [-DNSDelegationCredential <PS Credential>] [-NoDNSOnNetwork] [-DomainMode <DomainMode> {Win2003 | Win2008 | Win2008R2 | Win2012}] [DomainType <DomainType> {Child Domain | TreeDomain} [-InstallDNS] [-LogPath <string>] [-NoGlobalCatalog] [-NewDomainNetBIOSName <string>] [-NoRebootOnCompletion] [-ReplicationSourceDC <string>] [-SiteName <string>] [-SkipAutoConfigureDNS] [-Systemkey <SecureString>] [-SYSVOLPath] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]  
```  
  
> [!NOTE]  
> **-Credential** только требуется, если вы не в настоящее время вход в качестве члена группы администраторов предприятия.  
>   
> **- NewDomainNetBIOSName** аргумент является обязательным, если требуется изменить 15-значное имя, созданное автоматически на основе префикса имени домена DNS или если длина имени превышает 15 символов.  
  
Например использовать учетные данные corp\EnterpriseAdmin1 для создания нового дочернего домена с именем child.corp.contoso.com, установки DNS-сервера, создания делегирования DNS в домене corp.contoso.com, задайте режим работы домена до Windows Server 2003, превращение создаваемого контроллера домена с сервером глобального каталога на сайте с именем Хьюстоне, использовать DC1.corp.contoso.com в качестве контроллера домена источника репликации, установите базу данных Active Directory и SYSVOL на диск D:\ , установите файлы журнала на диск E:\ и будет предложено ввести пароль режима восстановления служб каталогов, но не получать приглашение на подтверждение команды, введите:  
  
```  
Install-ADDSDomain -SafeModeAdministratorPassword -Credential (get-credential corp\EnterpriseAdmin1) -NewDomainName child -ParentDomainName corp.contoso.com -InstallDNS -CreateDNSDelegation -DomainMode Win2003 -ReplicationSourceDC DC1.corp.contoso.com -SiteName Houston -DatabasePath "d:\NTDS" "SYSVOLPath "d:\SYSVOL" -LogPath "e:\Logs" -Confirm:$False  
```  
  
### <a name="BKMK_PSReplica"></a>Установка контроллера домена дополнительных (реплики) с помощью Windows PowerShell  
Далее представлен синтаксис команд для установки дополнительного контроллера домена. Дополнительные аргументы приведены в квадратных скобках.  
  
```  
Install-ADDSDomainController -DomainName <string> [-SkipPreChecks] -SafeModeAdministratorPassword <SecureString> [-ADPrepCredential <PS Credential>] [-AllowDomainControllerReinstall] [-ApplicationPartitionsToReplicate <string[]>] [-CreateDNSDelegation] [-Credential <PS Credential>] [-CriticalReplicationOnly] [-DatabasePath <string>] [-DNSDelegationCredential <PS Credential>] [-NoDNSOnNetwork] [-NoGlobalCatalog] [-InstallationMediaPath <string>] [-InstallDNS] [-LogPath <string>] [-MoveInfrastructureOperationMasterRoleIfNecessary] [-NoRebootOnCompletion] [-ReplicationSourceDC <string>] [-SiteName <string>] [-SkipAutoConfigureDNS] [-SystemKey <SecureString>] [-SYSVOLPath <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]  
```  
  
Чтобы установить контроллер домена и DNS-сервера в домене corp.contoso.com и получить запрос на ввод учетных данных администратора домена и пароля DSRM, введите следующую команду:  
  
```  
Install-ADDSDomainController -Credential (Get-Credential CORP\Administrator) -DomainName "corp.contoso.com"
```  
  
Если компьютер уже присоединен к домену и вы являетесь членом группы администраторов домена, можно использовать:  
  
```  
Install-ADDSDomainController -DomainName "corp.contoso.com"  
```  
  
Чтобы запрашивать имя домена, введите:  
  
```  
Install-ADDSDomainController -Credential (Get-Credential) -DomainName (Read-Host "Domain to promote into")
```  
  
Следующая команда будет использовать учетные данные Contoso\EnterpriseAdmin1 для установки записи контроллеру домена и сервер глобального каталога на сайте с именем Boston, установки DNS-сервера, создания делегирования DNS в домене contoso.com, установки с носителя, который хранится в папке c:\ADDS IFM, установки базы данных Active Directory и SYSVOL на диск D:\, установите файлы журнала на диск E:\ , у сервера автоматически перезагружаться после завершения установки AD DS и будет предложено ввести пароль режима восстановления служб каталогов:  
  
```  
Install-ADDSDomainController -Credential (Get-Credential CONTOSO\EnterpriseAdmin1) -CreateDNSDelegation -DomainName corp.contoso.com -SiteName Boston -InstallationMediaPath "c:\ADDS IFM" -DatabasePath "d:\NTDS" -SYSVOLPath "d:\SYSVOL" -LogPath "e:\Logs"   
```  
  
### <a name="performing-a-staged-rodc-installation-using-windows-powershell"></a>Выполнение поэтапной установки RODC с помощью Windows PowerShell  
Синтаксис команд для создания учетной записи RODC выглядит следующим образом. Дополнительные аргументы приведены в квадратных скобках.  
  
```  
Add-ADDSReadOnlyDomainControllerAccount [-SkipPreChecks] -DomainControllerAccuntName <string> -DomainName <string> -SiteName <string> [-AllowPasswordReplicationAccountName <string []>] [-NoGlobalCatalog] [-Credential <PS Credential>] [-DelegatedAdministratorAccountName <string>] [-DenyPasswordReplicationAccountName <string []>] [-InstallDNS] [-ReplicationSourceDC <string>] [-Force] [-WhatIf] [-Confirm] [<Common Parameters>]  
```  
  
Синтаксис команд для прикрепления сервера к учетной записи RODC выглядит следующим образом. Дополнительные аргументы приведены в квадратных скобках.  
  
```  
Install-ADDSDomainController -DomainName <string> [-SkipPreChecks] -SafeModeAdministratorPassword <SecureString> [-ADPrepCredential <PS Credential>] [-ApplicationPartitionsToReplicate <string[]>] [-Credential <PS Credential>] [-CriticalReplicationOnly] [-DatabasePath <string>] [-NoDNSOnNetwork] [-InstallationMediaPath <string>] [-InstallDNS] [-LogPath <string>] [-MoveInfrastructureOperationMasterRoleIfNecessary] [-NoRebootOnCompletion] [-ReplicationSourceDC <string>] [-SkipAutoConfigureDNS] [-SystemKey <SecureString>] [-SYSVOLPath <string>] [-UseExistingAccount] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]  
```  
  
Например чтобы создать учетную запись RODC с именем RODC1:  
  
```  
Add-ADDSReadOnlyDomainControllerAccount -DomainControllerAccountName RODC1 -DomainName corp.contoso.com -SiteName Boston DelegatedAdministratoraccountName PilarA  
```  
  
Затем выполните следующие команды на сервере, который следует прикрепить к учетной записи RODC1. Сервер не может быть присоединен к домену. Сначала установите средства ролями и сервера AD DS:  
  
```  
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
```  
  
Затем выполните следующую команду, чтобы создать RODC:  
  
```  
Install-ADDSDomainController -DomainName corp.contoso.com -SafeModeAdministratorPassword (Read-Host -Prompt "DSRM Password:" -AsSecureString) -Credential (Get-Credential Corp\PilarA) -UseExistingAccount
```  
  
Нажмите клавишу **Y** для подтверждения либо включите **«Подтверждение** аргумента, чтобы избежать запроса подтверждения.  
  
## <a name="BKMK_GUI"></a>Установка AD DS с помощью диспетчера сервера  
AD DS можно установить в Windows Server 2012 с помощью мастера добавления ролей в диспетчере сервера, за которым следует Active Directory мастер настройки доменных служб, который является новой начиная с Windows Server 2012. Active Directory домена мастер установки служб (dcpromo.exe) устарел начиная с Windows Server 2012.  
  
Ниже описаны способ создания пулов серверов для установки и управления AD DS на нескольких серверах, а также порядок использования мастеров для установки служб AD DS.  
  
### <a name="BKMK_ServerPools"></a>Создание пулов серверов  
Диспетчер серверов может объединять в пул другие серверы в сети, пока они доступны с компьютера, на котором запущен диспетчер сервера. После объединения в пул эти серверы для удаленной установки Доменных службах Active Directory или любых других вариантов конфигурации возможных в диспетчере сервера можно использовать. Компьютер с запущенным диспетчером сервера автоматически включает себя в пул. Дополнительные сведения о пулах серверов см. в разделе [Добавление серверов к диспетчеру серверов](https://technet.microsoft.com/library/hh831453.aspx).  
  
> [!NOTE]  
> Для управления компьютером присоединенных к домену, с помощью диспетчера сервера на сервер рабочей группы или наоборот необходимы дополнительные действия по настройке. Дополнительные сведения см. в разделе «Добавление и управление серверами в рабочих группах» в [Добавление серверов к диспетчеру серверов](https://technet.microsoft.com/library/hh831453.aspx).  
  
### <a name="BKMK_installADDSGUI"></a>Установка AD DS  
**Учетные данные администратора**  
  
Требования к учетным данным для установки Доменных служб Active Directory могут отличаться в зависимости от конфигурации развертывания выбранной. Дополнительные сведения см. в разделе [требования для запуска Adprep.exe и установки доменных служб Active Directory Credential](../../ad-ds/deploy/../../ad-ds/deploy/../../ad-ds/deploy/../../ad-ds/deploy/../../ad-ds/deploy/../../ad-ds/deploy/../../ad-ds/deploy/../../ad-ds/deploy/../../ad-ds/deploy/../../ad-ds/deploy/../../ad-ds/deploy/../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_Creds).  
  
Используйте следующие процедуры для установки AD DS с помощью Графического интерфейса пользователя. Шаги можно выполнять локально или удаленно. Более подробные объяснения этих шагов см. в следующих разделах:  
  
-   [Развертывание леса с помощью диспетчера серверов](../../ad-ds/deploy/Install-a-New-Windows-Server-2012-Active-Directory-Forest--Level-200-.md#BKMK_SMForest)  
  
-   [Установка контроллера домена реплики Windows Server 2012 в существующем домене & #40; Уровень 200 & #41;](../../ad-ds/deploy/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-.md)  
  
-   [Установка нового дочернего Active Directory Windows Server 2012 или домена дерева & #40; Уровень 200 & #41;](../../ad-ds/deploy/Install-a-New-Windows-Server-2012-Active-Directory-Child-or-Tree-Domain--Level-200-.md)  
  
-   [Установка контроллера домена только для Active Directory Server 2012 чтения Windows & #40; RODC & #41; & #40; Уровень 200 & #41;](../../ad-ds/deploy/RODC/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-.md)  
  
##### <a name="to-install-ad-ds-by-using-server-manager"></a>Для установки AD DS с помощью диспетчера сервера  
  
1.  В диспетчере серверов щелкните **управление** и нажмите кнопку **Добавить роли и компоненты** для запуска мастера добавления ролей.  
  
2.  На **перед началом** щелкните **Далее**.  
  
3.  На **Выбор типа установки** щелкните **Установка на основе ролей или компонентов** и нажмите кнопку **Далее**.  
  
4.  На **Выбор целевого сервера** щелкните **выберите сервер из пула серверов**, щелкните имя сервера, где вы хотите установку AD DS, а затем нажмите кнопку **Далее**.  
  
    Чтобы выбрать удаленные серверы, сначала создайте пул серверов и добавление удаленных серверов. Дополнительные сведения о создании пулов серверов см. в разделе [Добавление серверов к диспетчеру серверов](https://technet.microsoft.com/library/hh831453.aspx).  
  
5.  На **Выбор ролей сервера** щелкните **доменных служб Active Directory**, а затем на **мастера добавления ролей и компонентов** диалоговом нажмите кнопку **добавить компоненты**и нажмите кнопку **Далее**.  
  
6.  На **выберите компоненты** выберите дополнительные компоненты, вы хотите установить и нажмите кнопку **Далее**.  
  
7.  На **доменных служб Active Directory** , просмотрите сведения и нажмите кнопку **Далее**.  
  
8.  На **подтверждение выбранных элементов для установки** щелкните **установить**.  
  
9. На **результатов** убедитесь, что установка успешно завершена и нажмите кнопку **повысить роль этого сервера до уровня контроллера домена** Чтобы запустить мастер настройки доменных служб Active Directory.  
  
    ![Установите службы AD DS](media/Install-Active-Directory-Domain-Services--Level-100-/ADDS_SMI_SMPromotes.gif)  
  
    > [!IMPORTANT]  
    > Если вы закроете мастер добавления ролей на этом этапе без запуска мастер настройки доменных служб Active Directory, его можно перезапустить, щелкнув "задачи" в диспетчере сервера.  
  
    ![Установите службы AD DS](media/Install-Active-Directory-Domain-Services--Level-100-/ADDS_SMI_Tasks.gif)  
  
10. На **конфигурации развертывания** выберите один из следующих вариантов:  
  
    -   При установке дополнительного контроллера домена в существующем домене, нажмите кнопку **добавить контроллер домена в существующий домен**и введите имя домена (например, emea.corp.contoso.com) или нажмите **выберите... ** выбрать домен и учетные данные (например, указать учетную запись, которая является членом группы администраторов домена) и нажмите кнопку **Далее**.  
  
        > [!NOTE]  
        > Имя домена и учетные данные текущего пользователя предоставляются по умолчанию только в том случае, если компьютер присоединен к домену и выполняется локальная установка. Если вы устанавливаете AD DS на удаленном сервере, необходимо указать учетные данные, с помощью встроенных. Если учетные данные текущего пользователя недостаточны для выполнения установки, нажмите кнопку **изменение... ** чтобы указать другие учетные данные.  
  
        Дополнительные сведения см. в разделе [установки контроллера домена реплики Windows Server 2012 в существующем домене & #40; Уровень 200 & #41; ](../../ad-ds/deploy/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-.md).  
  
    -   Если вы устанавливаете новый дочерний домен, щелкните **добавить новый домен в существующий лес**, для **Выбор типа домена**выберите **дочернего домена**введите или выберите имя DNS-имя родительского домена (например, corp.contoso.com), введите относительное имя нового дочернего домена (например emea), введите учетные данные для создания нового домена, а затем нажмите кнопку **Далее**.  
  
        Дополнительные сведения см. в разделе [Установка Windows Server 2012 Active Directory дочерний или домена дерева & #40; Уровень 200 & #41; ](../../ad-ds/deploy/Install-a-New-Windows-Server-2012-Active-Directory-Child-or-Tree-Domain--Level-200-.md).  
  
    -   Если выполняется установка нового доменного дерева, щелкните **добавить новый домен в существующий лес**, для **Выбор типа домена**, выберите **домена дерева**, введите имя корневого домена (например, corp.contoso.com), введите DNS-имя нового домена (например, fabrikam.com), введите учетные данные для создания нового домена, а затем нажмите кнопку **Далее**.  
  
        Дополнительные сведения см. в разделе [Установка Windows Server 2012 Active Directory дочерний или домена дерева & #40; Уровень 200 & #41; ](../../ad-ds/deploy/Install-a-New-Windows-Server-2012-Active-Directory-Child-or-Tree-Domain--Level-200-.md).  
  
    -   При установке нового леса, щелкните **добавить новый лес** и затем введите имя корневого домена (например, corp.contoso.com).  
  
        Дополнительные сведения см. в разделе [Установка нового леса Windows Server 2012 Active Directory & #40; Уровень 200 & #41; ](../../ad-ds/deploy/Install-a-New-Windows-Server-2012-Active-Directory-Forest--Level-200-.md).  
  
11. На **параметры контроллера домена** выберите один из следующих вариантов:  
  
    -   При создании нового леса или домена выберите функциональные уровни домена и леса, щелкните **сервера доменных имен (DNS)**, укажите пароль DSRM и нажмите кнопку **Далее**.  
  
    -   Если выполняется добавление контроллера домена в существующий домен, щелкните **сервера доменных имен (DNS)**, **глобальный каталог (GC)**, или **чтение только контроллер домена (RODC)** при необходимости, выберите имя сайта, введите пароль DSRM и нажмите кнопку **Далее**.  
  
    Дополнительные сведения о том, какие параметров на этой странице при различных условиях см. в разделе [параметры контроллера домена](../../ad-ds/deploy/AD-DS-Installation-and-Removal-Wizard-Page-Descriptions.md#BKMK_DCOptionsPage).  
  
12. На **параметры DNS** (которая отображается только в случае установки DNS-сервера), нажмите кнопку **обновить DNS-делегирование** при необходимости. В противном случае укажите учетные данные, которые имеют разрешение на создание записей DNS-делегирования в родительской зоне DNS.  
  
    Если не удается связаться с DNS-сервер, который располагается родительская зона, **обновить DNS-делегирование** будет недоступен.  
  
    Дополнительные сведения о том, требуется ли обновить делегирование DNS см. в разделе [общее представление о делегировании зоны](https://technet.microsoft.com/library/cc771640.aspx). Если вы попытаетесь обновить делегирование DNS и выдано сообщение об ошибке см. в разделе [параметры DNS](../../ad-ds/deploy/AD-DS-Installation-and-Removal-Wizard-Page-Descriptions.md#BKMK_DNSOptionsPage).  
  
13. На **параметры RODC** (которая отображается только в случае установки контроллера RODC), укажите имя группы или пользователя, который будет управлять RODC, добавьте учетные записи или удалите учетные записи из группы репликации разрешена или запрещена пароль и нажмите кнопку **Далее**.  
  
    Дополнительные сведения см. в разделе [политики репликации паролей](https://technet.microsoft.com/library/cc730883(v=ws.10)).  
  
14. На **Дополнительные параметры** выберите один из следующих вариантов:  
  
    -   При создании нового домена введите новое NetBIOS-имя или проверьте NetBIOS-имя домена по умолчанию и нажмите кнопку **Далее**.  
  
    -   При добавлении контроллера домена в существующий домен, выберите контроллер домена, который требуется реплицировать данные установки Доменных службах Active Directory (или Разрешите мастеру выбрать любой контроллер домена). При установке с носителя щелкните **путь установки с носителя** введите и проверьте путь к исходным файлам установки и нажмите кнопку **Далее**.  
  
        Нельзя использовать с носителя (IFM) для установки первого контроллера домена в домене. IFM не работает в разных версиях операционных систем. Другими словами Чтобы установить дополнительный контроллер домена под управлением Windows Server 2012 с помощью IFM, необходимо создать носитель резервной копии на контроллере домена Windows Server 2012. Дополнительные сведения об IFM см. в разделе [установка дополнительного контроллера домена с использованием IFM](https://technet.microsoft.com/library/cc816722(WS.10).aspx).  
  
15. На **пути** страницы введите расположения для базы данных Active Directory, файлы журналов и папки SYSVOL (либо примите расположение по умолчанию) и нажмите кнопку **Далее**.  
  
    > [!IMPORTANT]  
    > Не храните базу данных Active Directory, файлы журнала и папку SYSVOL на томе данных, отформатированном Resilient File System (ReFS).  
  
16. На **параметры подготовки** введите учетные данные, достаточные для выполнения команды adprep. Дополнительные сведения см. в разделе [требования для запуска Adprep.exe и установки доменных служб Active Directory Credential](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md#BKMK_Creds).  
  
17. На **просмотреть параметры** подтвердите свой выбор, нажмите кнопку **просмотреть скрипт** Если вы хотите экспортировать параметры в сценарий Windows PowerShell и нажмите кнопку **Далее**.  
  
18. На **проверка предварительных требований** страницы, убедитесь, что проверка предварительных требований завершена, а затем нажмите кнопку **установить**.  
  
19. На **результатов** убедитесь, что сервер успешно настроен в качестве контроллера домена. Сервер будет автоматически перезагружен для завершения установки AD DS.  
  
## <a name="BKMK_UIStaged"></a>Выполнение поэтапной установки RODC с помощью графического пользовательского интерфейса  
Поэтапная Установка RODC позволяет создать RODC в два этапа. На первом этапе член группы администраторов домена создает учетную запись RODC. На втором этапе сервер прикрепляется к учетной записи RODC. Второй этап может выполнить член группы администраторов домена либо делегированный пользователь домена или группы.  
  
#### <a name="to-create-an-rodc-account-by-using-the-active-directory-management-tools"></a>Чтобы создать учетную запись RODC с помощью средства управления Active Directory  
  
1.  Можно создать учетную запись RODC, используя Центр администрирования Active Directory или Active Directory-пользователи и компьютеры.  
  
    1.  Нажмите кнопку **запустить**, нажмите кнопку **Администрирование**, а затем нажмите кнопку **Центр администрирования Active Directory**.  
  
    2.  В области навигации (левая панель) щелкните имя домена.  
  
    3.  В списке управления (центральная панель) щелкните **контроллеры домена** Подразделения.  
  
    4.  На панели задач (правая панель) щелкните **предварительное создание учетной записи контроллера домена только для чтения**.  
  
    - Или -  
  
    1.  Нажмите кнопку **запустить**, нажмите кнопку **Администрирование**, а затем нажмите кнопку **Active Directory-пользователи и компьютеры**.  
  
    2.  Либо щелкните правой кнопкой мыши **контроллеры домена** подразделение (OU) или щелкните **контроллеры домена** Подразделения и нажмите кнопку **действие**.  
  
    3.  Нажмите кнопку **учетную запись создать заранее контроллера домена только для чтения**.  
  
2.  На **Добро пожаловать в мастер установки доменных служб Active Directory** страницы, если вы хотите изменить заданное по умолчанию репликации политики Паролей, выберите **использовать расширенный режим установки**, а затем нажмите кнопку **Далее**.  
  
3.  На **сетевые учетные данные** в разделе **укажите учетные данные учетной записи, используемые для выполнения установки**, нажмите кнопку **мои текущие учетные данные входа** или нажмите кнопку **альтернативные учетные данные**, а затем нажмите кнопку **задать**. В **безопасности Windows** диалогового окна введите имя пользователя и пароль для учетной записи, которая обладает возможностью установки дополнительного контроллера домена. Чтобы установить дополнительный контроллер домена, необходимо быть членом группы администраторов предприятия или группы администраторов домена. По завершении ввода учетных данных, нажмите кнопку **Далее**.  
  
4.  На **указать имя компьютера** введите имя компьютера сервера, который будет входить в RODC.  
  
5.  На **выберите сайт** выберите сайт из списка или выберите параметр, чтобы установить контроллер домена в сайте, который соответствует IP-адрес компьютера, на котором запущен мастер и нажмите кнопку **Далее**.  
  
6.  На **Дополнительные параметры контроллера домена** страницы, выберите следующие параметры и нажмите кнопку **Далее**:  
  
    -   **DNS-сервер**: этот параметр выбран по умолчанию, чтобы контроллер домена может выступать в роли сервера доменных имен (DNS). Если вы не хотите, чтобы контроллер домена в качестве DNS-сервера, снимите флажок. Тем не менее если не установить роль DNS-сервера на RODC чтения является единственным контроллером домена в филиале, пользователи филиала не смогут выполнять разрешение имен при глобальной сети (WAN) на сайте концентратора находится в автономном режиме.  
  
    -   **Глобальный каталог**: этот параметр выбран по умолчанию. Он добавляет глобальный каталог, доступный только для чтения разделы на контроллер домена и позволяет функции поиска глобального каталога. Если вы не хотите, чтобы контроллер домена является сервером глобального каталога, снимите флажок. Тем не менее если не установить сервер глобального каталога в филиале или не включить возможность кэширования членства универсальных группах для сайта, содержащего RODC, пользователи в филиале, не смогут войти в домен при отсутствии соединения по глобальной сети с узловым сайтом.  
  
    -   **Контроллер домена только для чтения**. При создании учетной записи RODC, этот параметр выбран по умолчанию и снять его нельзя.  
  
7.  Если вы выбрали **использовать расширенный режим установки** флажок на **приветствия** страницы, **Укажите политику репликации паролей** откроется страница. По умолчанию паролей учетных записей, реплицируются только для чтения и учетных записей, чувствительных к безопасности (например, члены группы администраторов домена) явным образом запрещается свои пароли, реплицируется в RODC.  
  
    Чтобы добавить другие учетные записи в политику, нажмите кнопку **добавить**, нажмите кнопку **разрешить использование паролей для учетной записи для репликации на этот RODC** или щелкните **запретить пароли для учетной записи репликации на этот RODC** , а затем выберите учетные записи.  
  
    После завершения (или оставив настройку по умолчанию), нажмите кнопку **Далее**.  
  
8.  На **делегирования для установки и администрирования RODC** введите имя пользователя или группы, которые будут связывать сервер с учетной записью RODC, которая создается. Можно ввести имя только одного субъекта безопасности.  
  
    Чтобы найти в каталоге определенного пользователя или группу, нажмите кнопку **задать**. В **выбрать пользователя или группу**, введите имя пользователя или группы. Рекомендуется делегировать права установки и администрирования в группу RODC.  
  
    Этот пользователь или группа также получат локальные права администратора на RODC после установки. Если вы не укажете пользователю или группе, будет возможность подключения сервера к учетной записи только члены группы администраторов домена или группы администраторов предприятия.  
  
    Когда вы закончите, нажмите кнопку **Далее**.  
  
9. На **Сводка** просмотрите выбранные параметры. Нажмите кнопку **обратно** при необходимости изменить какие-либо параметры.  
  
    Чтобы сохранить выбранные параметры в файл ответов, который можно использовать для автоматизации последующей работы Доменных службах Active Directory, нажмите кнопку **экспорт параметров**. Введите имя файла ответов, а затем нажмите кнопку **Сохранить**.  
  
    Когда правильности свой выбор, нажмите кнопку **Далее** для создания учетной записи RODC.  
  
10. На **Завершение мастера установки доменных служб Active Directory** щелкните **Готово**.  
  
После создания учетной записи RODC можно подключить сервер к учетной записи для завершения установки RODC. Данный второй этап можно выполнить в филиале, где будет находиться контроллер RODC. Сервер, где выполняется эта процедура не должен быть присоединен к домену. Начиная с Windows Server 2012, можно использовать мастер добавления ролей в диспетчере сервера для прикрепления сервера к учетной записи RODC.  
  
#### <a name="to-attach-a-server-to-an-rodc-account-using-server-manager"></a>Чтобы подключить сервер к учетной записи RODC с помощью диспетчера сервера  
  
1.  Вход в качестве локального администратора.  
  
2.  В диспетчере серверов щелкните **Добавить роли и компоненты**.  
  
3.  На **перед началом** щелкните **Далее**.  
  
4.  На **Выбор типа установки** щелкните **Установка на основе ролей или компонентов** и нажмите кнопку **Далее**.  
  
5.  На **Выбор целевого сервера** щелкните **выберите сервер из пула серверов**, щелкните имя сервера, где вы хотите установку AD DS, а затем нажмите кнопку **Далее**.  
  
6.  На **Выбор ролей сервера** щелкните **доменных служб Active Directory**, нажмите кнопку **добавить компоненты** и нажмите кнопку **Далее**.  
  
7.  На **выберите компоненты** выберите дополнительные компоненты, которые вы хотите установить и нажмите кнопку **Далее**.  
  
8.  На **доменных служб Active Directory** , просмотрите сведения и нажмите кнопку **Далее**.  
  
9. На **подтверждение выбранных элементов для установки** щелкните **установить**.  
  
10. На **результатов** проверьте **Установка успешно завершена**и нажмите кнопку **повысить роль этого сервера до уровня контроллера домена** Чтобы запустить мастер настройки доменных служб Active Directory.  
  
    > [!IMPORTANT]  
    > Если вы закроете мастер добавления ролей на этом этапе без запуска мастер настройки доменных служб Active Directory, его можно перезапустить, щелкнув "задачи" в диспетчере сервера.  
  
    (media/Install-Active-Directory-Domain-Services--Level-100-/ADDS_SMI_Tasks.gif)  
  
11. На **конфигурации развертывания** щелкните **добавить контроллер домена в существующий домен**, введите имя домена (например, emea.contoso.com) и учетные данные (например, укажите учетную запись, делегированную для управления и установки RODC), а затем нажмите кнопку **Далее**.  
  
12. На **параметры контроллера домена** щелкните **использовать существующую учетную запись RODC**, введите и подтвердите пароль режима восстановления служб каталогов и затем нажмите кнопку **Далее**.  
  
13. На **Дополнительные параметры** страниц, при установке с носителя, нажмите кнопку **путь установки с носителя** введите и проверьте путь к исходным файлам установки, выберите контроллер домена, который требуется реплицировать данные установки Доменных службах Active Directory (или Разрешите мастеру выбрать любой контроллер домена) и нажмите кнопку **Далее**.  
  
14. На **пути** введите расположения для базы данных Active Directory, файлы журналов и папки SYSVOL или примите расположение по умолчанию и нажмите кнопку **Далее**.  
  
15. На **просмотреть параметры** подтвердите свой выбор, нажмите кнопку **просмотреть сценарий** экспортировать параметры в сценарий Windows PowerShell, и нажмите кнопку **Далее**.  
  
16. На **проверка предварительных требований** страницы, убедитесь, что проверка предварительных требований завершена, а затем нажмите кнопку **установить**.  
  
    Чтобы завершить установку AD DS, сервер перезагрузится автоматически.  
  
## <a name="see-also"></a>См. также:  
[Устранение неполадок развертывания контроллера домена](Troubleshooting-Domain-Controller-Deployment.md)  
[Установка нового леса Active Directory Windows Server 2012 & #40; Уровень 200 & #41;](../../ad-ds/deploy/Install-a-New-Windows-Server-2012-Active-Directory-Forest--Level-200-.md)  
[Установка нового дочернего Active Directory Windows Server 2012 или домена дерева & #40; Уровень 200 & #41;](../../ad-ds/deploy/Install-a-New-Windows-Server-2012-Active-Directory-Child-or-Tree-Domain--Level-200-.md)  
[Установка контроллера домена реплики Windows Server 2012 в существующем домене & #40; Уровень 200 & #41;](../../ad-ds/deploy/Install-a-Replica-Windows-Server-2012-Domain-Controller-in-an-Existing-Domain--Level-200-.md)  
  



