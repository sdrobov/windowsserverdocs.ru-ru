---
ms.assetid: 35de490f-c506-4b73-840c-b239b72decc2
title: Настройка локального условного доступа на основе устройств
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 08/11/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 0df290248f049b3f8a823e902cefa860fa074091
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189851"
---
# <a name="configure-on-premises-conditional-access-using-registered-devices"></a>Настройка локального условного доступа с помощью зарегистрированных устройств


Следующий документ поможет вам Установка и Настройка локального условного доступа с зарегистрированных устройств.

![Условный доступ](media/Using-Device-based-Conditional-Access-on-Premises/ADFS_ITPRO4.png)  

## <a name="infrastructure-pre-requisites"></a>Предварительные требования инфраструктуры
Ниже предварительным являются обязательными, прежде чем начать с локального условного доступа. 

|Требование|Описание
|-----|-----
|Подписка Azure AD с Azure AD Premium | Чтобы включить устройство записи за в локальной среде условный доступ — [подходит бесплатную пробную версию](https://azure.microsoft.com/trial/get-started-active-directory/)  
|Подписка Intune|требуется только для интеграции управления мобильными Устройствами для сценариев соответствия устройства -[подходит бесплатную пробную версию](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0)
|Azure AD Connect|Ноябрь 2015 г. исправление QFE или более поздней версии.  Получить последнюю версию [здесь](https://www.microsoft.com/en-us/download/details.aspx?id=47594).  
|Windows Server 2016|Сборка 10586 или более поздней версии, для AD FS  
|Схема Windows Server 2016 Active Directory|Необходим уровень схемы 85 или более поздней версии.
|Контроллер домена Windows Server 2016|Это только необходимые для развертываний доверием ключ Hello для бизнеса.  Дополнительные сведения можно найти в [здесь](https://aka.ms/whfbdocs).  
|Клиент Windows 10|Build 10586 или более новую, присоединенных к домену выше необходим для присоединения к домену Windows 10 и Microsoft Passport для рабочих сценариев только  
|Учетная запись пользователя Azure AD с назначенной лицензией Azure AD Premium|Для регистрации устройства  


 
## <a name="upgrade-your-active-directory-schema"></a>Обновление схемы Active Directory
Чтобы использовать локального условного доступа с зарегистрированных устройств, необходимо сначала обновить схему AD.  Должны быть выполнены следующие условия:
    - Схема должна быть 85 или более поздней версии
    - Это только необходимые для леса, который соединяется с AD FS

> [!NOTE]
> Если вы установили Azure AD Connect перед обновлением до версии схемы (уровень 85 или более поздней версии) в Windows Server 2016, необходимо будет повторно запустите установку Azure AD Connect и обновить в локальной схеме AD для обеспечения правила синхронизации для Атрибут msDS-KeyCredentialLink настраивается.

### <a name="verify-your-schema-level"></a>Проверьте уровень схемы
Чтобы проверить уровень схемы, сделайте следующее:

1.  Можно использовать ADSIEdit или LDP и подключитесь к контекст именования схемы.  
2.  С помощью ADSIEdit, щелкните правой кнопкой мыши «CN = Schema, CN = Configuration, DC =<domain>, DC =<com> и выберите пункт Свойства.  Relpace домена и части com со сведениями о леса.
3.  В разделе Редактор атрибутов найдите атрибута objectVersion по адресу, и он сообщит вам, вашей версии.  

![Редактирование ADSI](media/Configure-Device-Based-Conditional-Access-on-Premises/adsiedit.png)  

Также можно использовать следующий командлет PowerShell (замените объект с именования сведения о контексте схемы):

``` powershell
Get-ADObject "cn=schema,cn=configuration,dc=domain,dc=local" -Property objectVersion
    
```

![PowerShell](media/Configure-Device-Based-Conditional-Access-on-Premises/pshell1.png) 

Дополнительные сведения об обновлении см. в разделе [обновление контроллеров домена до Windows Server 2016](../../ad-ds/deploy/Upgrade-Domain-Controllers-to-Windows-Server-2016.md). 

## <a name="enable-azure-ad-device-registration"></a>Включение регистрации устройств Azure AD  
Чтобы настроить этот сценарий, необходимо настроить возможность регистрации устройства в Azure AD.  

Чтобы сделать это, следуйте инструкциям в разделе [настройке присоединения к Azure AD в вашей организации](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-setup/)  

## <a name="setup-ad-fs"></a>Настройка AD FS  
1. Создание [новой фермы AD FS 2016](https://technet.microsoft.com/library/dn486775.aspx).   
2.  Или [перенести](../../ad-fs/deployment/Upgrading-to-AD-FS-in-Windows-Server-2016.md) ферме AD FS 2016 из AD FS 2012 R2  
4. Развертывание [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnectfed-whatis/) использование пользовательский путь для подключения AD FS в Azure AD.  

## <a name="configure-device-write-back-and-device-authentication"></a>Настроить устройство записи обратно и проверку подлинности устройства  
> [!NOTE]
> Если вы запустили Azure AD Connect, используя стандартные параметры, к объектам правильного AD будут созданы для вас.  Однако в большинстве случаев AD FS, Azure AD Connect была запущена с настраиваемые параметры для настройки AD FS, поэтому следующие действия необходимы.  

### <a name="create-ad-objects-for-ad-fs-device-authentication"></a>Создание объектов AD для проверки подлинности устройств в AD FS  
Если в вашей ферме AD FS еще не настроена проверка подлинности устройств (это можно проверить в консоли управления AD FS в разделе "Служба" -> "Регистрация устройств"), выполните следующие действия, чтобы создать верные объекты и конфигурацию AD DS.  

![Регистрация устройств](media/Configure-Device-Based-Conditional-Access-on-Premises/device1.png)

>Примечание. Для выполнения следующих команд требуются средства администрирования Active Directory, поэтому если ваш сервер федерации не является контроллером домена, сначала установите эти средства с помощью шага 1, описанного ниже.  В противном случае можно пропустить этот шаг.  

1.  Запустите мастер **добавления ролей и компонентов** и выберите компонент **Средства удаленного администрирования сервер** -> **Средства администрирования ролей** -> **Средства AD DS и AD LDS**, а затем выберите **Модуль Active Directory для Windows PowerShell** и **Средства AD DS**.

![Регистрация устройств](media/Configure-Device-Based-Conditional-Access-on-Premises/device2.png)
  
2.  На сервере-источнике AD FS убедитесь, использованная в Доменных службах Active Directory пользователя с правами администратора Enterprise (EA) и откройте командную строку powershell с повышенными правами.  Затем выполните следующие команды PowerShell:  
    
    `Import-module activedirectory`  
    `PS C:\> Initialize-ADDeviceRegistration -ServiceAccountName "<your service account>" ` 
3.  На всплывающем окне нажмите кнопку "Да".

>Примечание. Если ваша служба AD FS настроена на использование групповой управляемой учетной записи службы, введите имя учетной записи в формате "domain\accountname$"

![Регистрация устройств](media/Configure-Device-Based-Conditional-Access-on-Premises/device3.png)  

Указанная выше команда PSH создает следующие объекты:  


- Контейнер RegisteredDevices в разделе домена AD  
- Контейнер и объект службы регистрации устройств в разделе "Настройка" --> "Службы" --> "Конфигурация регистрации устройств"  
- Контейнер и объект DKM службы регистрации устройств в разделе "Настройка" --> "Службы" --> "Конфигурация регистрации устройств"  

![Регистрация устройств](media/Configure-Device-Based-Conditional-Access-on-Premises/device4.png)  

4.  После выполнения этой команды отобразится сообщение об успешном завершении.

![Регистрация устройств](media/Configure-Device-Based-Conditional-Access-on-Premises/device5.png) 

###        <a name="create-service-connection-point-scp-in-ad"></a>Создание точки подключения службы (SCP) в AD  
Если вы планируете использовать присоединение к домену Windows 10 (с автоматической регистрацией в Azure AD), как описано здесь, выполните следующие команды, чтобы создать точку подключения службы в AD DS  
1.  Откройте Windows PowerShell и выполните следующую команду:
    
    `PS C:>Import-Module -Name "C:\Program Files\Microsoft Azure Active Directory Connect\AdPrep\AdSyncPrep.psm1" ` 

>Примечание: при необходимости, скопируйте файл AdSyncPrep.psm1 с вашего сервера Azure AD Connect.  Этот файл находится в каталоге Program Files\Microsoft Azure Active Directory Connect\AdPrep

![Регистрация устройств](media/Configure-Device-Based-Conditional-Access-on-Premises/device6.png)   

2. Укажите учетные данные глобального администратора Azure AD  

    `PS C:>$aadAdminCred = Get-Credential`

![Регистрация устройств](media/Configure-Device-Based-Conditional-Access-on-Premises/device7.png) 

3.  Выполните следующую команду PowerShell 

    `PS C:>Initialize-ADSyncDomainJoinedComputerSync -AdConnectorAccount [AD connector account name] -AzureADCredentials $aadAdminCred ` 

Где [AD connector account name] — имя учетной записи, которую вы настроили в Azure AD Connect при добавлении локального каталога AD DS.
  
После выполнения приведенных выше команд клиенты Windows 10 могут найти верный домен Azure AD для присоединения путем создания объекта serviceConnectionpoint в AD DS.  

### <a name="prepare-ad-for-device-write-back"></a>Подготовка AD к обратной записи устройств   
Чтобы обеспечить верное состояние объектов и контейнеров AD DS для обратной записи устройств из Azure AD, выполните следующие действия.

1.  Откройте Windows PowerShell и выполните следующую команду:  

    `PS C:>Initialize-ADSyncDeviceWriteBack -DomainName <AD DS domain name> -AdConnectorAccount [AD connector account name] ` 

Где [AD connector account name] — имя учетной записи, которую вы настроили в Azure AD Connect при добавлении локального каталога AD DS в формате domain\accountname  

Приведенная выше команда создает следующие объекты для обратной записи устройств в AD DS, если они еще не были созданы, и обеспечивает доступ к указанному имени учетной записи соединителя AD  

- Контейнер RegisteredDevices в разделе домена AD  
- Контейнер и объект службы регистрации устройств в разделе "Настройка" --> "Службы" --> "Конфигурация регистрации устройств"  

### <a name="enable-device-write-back-in-azure-ad-connect"></a>Включение обратной записи устройств в Azure AD Connect  
Включите обратную запись устройств в Azure AD Connect, если она еще не включена. Для этого запустите мастер еще раз и выберите **"Настройка параметров синхронизации"** , затем установите флажок обратной записи устройств и выберите лес, в котором выполнялись приведенные выше командлеты  

### <a name="configure-device-authentication-in-ad-fs"></a>Настройка проверки подлинности устройств в AD FS  
Используйте окно командной строки PowerShell с повышенными привилегиями для настройки политики AD FS путем выполнения следующей команды  

`PS C:>Set-AdfsGlobalAuthenticationPolicy -DeviceAuthenticationEnabled $true -DeviceAuthenticationMethod All` 

### <a name="check-your-configuration"></a>Проверка конфигурации  
Для справки ниже приведен полный список устройств, контейнеров и разрешений AD DS, необходимых для обратной записи и проверки подлинности устройств
 


- объект типа ms-DS-DeviceContainer в CN=RegisteredDevices,DC=&lt;домен&gt;        
    - доступ для чтения к учетной записи службы AD FS   
    - доступ для чтения и записи к учетной записи соединителя AD с синхронизацией Azure AD Connect</br></br>

- Контейнер CN=Device Registration Configuration,CN=Services,CN=Configuration,DC=&lt;домен&gt;  
- Контейнер DKM службы регистрации устройств под указанным выше контейнером

![Регистрация устройств](media/Configure-Device-Based-Conditional-Access-on-Premises/device8.png) 
 


- объект типа serviceConnectionpoint в CN=&lt;guid&gt;, CN=Device Registration

- Configuration,CN=Services,CN=Configuration,DC=&lt;домен&gt;  
 - доступ для чтения и записи к указанному имени учетной записи соединителя AD в новом объекте</br></br> 


- объект типа msDS-DeviceRegistrationServiceContainer в CN = Device Registration Services, CN = Device Registration Configuration, CN = Services, CN = Configuration, DC = & ltdomain >  


- объект типа msDS-DeviceRegistrationService в указанном выше контейнере  

### <a name="see-it-work"></a>Увидеть это в действии  
Для оценки новых утверждений и политики, необходимо сначала зарегистрируйте устройство.  Например, можно с помощью параметров приложения в системе компьютера Windows 10, "->" о присоединения к Azure AD, или присоединения к домену Windows 10 можно настроить автоматическую регистрацию устройств следующие дополнительные действия [здесь](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-devices-group-policy/).  Сведения о соединении Windows 10 для мобильных устройств, см. в документе [здесь](https://technet.microsoft.com/itpro/windows/manage/join-windows-10-mobile-to-azure-active-directory).  

Для целей оценки самый простой вход AD FS с помощью тестового приложения, в которой отображается список утверждений. Можно видеть новых утверждений, включая isManaged isCompliant и trusttype.  Если включить Microsoft Passport для работы, вы увидите также prt утверждения.  
 

## <a name="configure-additional-scenarios"></a>Настроить дополнительные сценарии  
### <a name="automatic-registration-for-windows-10-domain-joined-computers"></a>Автоматическая регистрация для Windows 10 к домену компьютеров  
Чтобы включить автоматическую регистрацию устройств для Windows 10 домена компьютеров, присоединенных к, выполните шаги 1 и 2 [здесь](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-devices-group-policy/).   
Это поможет вам в достижении следующее:  

1. Убедитесь, точка подключения службы в Доменных службах Active Directory существует и имеет соответствующие разрешения (мы создали этот объект выше, но она не помешает проверить).  
2. Убедитесь, что AD FS настроена правильно  
3. Убедитесь, что система AD FS имеет правильные конечные точки включены и настроены правила утверждений   
4. Настройка параметров групповой политики, необходимые для автоматической регистрации присоединенных к домену компьютеров   

### <a name="microsoft-passport-for-work"></a>Microsoft Passport for Work   
Сведения о включении Windows 10 с помощью Microsoft Passport for Work см. в разделе [включить Microsoft Passport for Work в вашей организации.](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-passport-deployment/)  

### <a name="automatic-mdm-enrollment"></a>Автоматическая регистрация MDM   
Чтобы включить автоматическую регистрацию MDM для зарегистрированных устройств, можно использовать isCompliant утверждения в политике управления доступом, сделайте [здесь.](https://blogs.technet.microsoft.com/ad/2015/08/14/windows-10-azure-ad-and-microsoft-intune-automatic-mdm-enrollment-powered-by-the-cloud/)  

## <a name="troubleshooting"></a>Устранение неполадок  
1.  Если отобразится сообщение об ошибке `Initialize-ADDeviceRegistration` , сообщает об объекте уже существуют в неверном состоянии, такие как «объект службы drs обнаружена без всех необходимых атрибутов», вы может выполнить команды powershell Azure AD Connect ранее и есть частичную конфигурацию в AD DS.  Попробуйте вручную удалить объекты, находящиеся под **CN = Device Registration Configuration, CN = Services, CN = Configuration, DC =&lt;домена&gt;**  и повторить попытку.  
2.  Присоединенные к домену Windows 10 клиентов  
    1. Убедитесь, что работает, проверку подлинности устройства, для входа в домен, присоединенных к клиента как тестовая учетная запись пользователя. Чтобы запустить подготовку быстро, блокировать и разблокировать рабочий стол по крайней мере один раз.   
    2. Инструкции для проверки учетных данных ключа stk ссылку на объект AD DS (синхронизации по-прежнему необходимо дважды запустить?)  
3.  Если вы получите ошибку при попытке регистрации компьютера Windows, устройство уже было зарегистрировано, но вы не можете или уже отменить регистрацию устройства, возможно, фрагмент конфигурации регистрации устройства в реестре.  Чтобы исследовать и удалить ее, выполните следующие действия:  
    1. На компьютере Windows, откройте средство Regedit и перейдите к **HKLM\Software\Microsoft\Enrollments**   
    2. В этом разделе будет много подразделов в виде идентификатора GUID.  Перейдите в папку подраздела, который содержит значения ~ 17 в нем и имеет «EnrollmentType», «6» [MDM объединить] или «13» (присоединение к Azure AD)  
    3. Изменить **EnrollmentType** для **0** 
    4. Повторите попытку регистрации устройства или регистрации  

### <a name="related-articles"></a>Связанные статьи  
* [Защита доступа к Office 365 и другим приложениям, подключенным к Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access/)  
* [Политики условного доступа устройств к службам Office 365](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-device-policies/)  
* [Настройка локального условного доступа, с помощью регистрации устройств Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-on-premises-setup)  
* [Подключение присоединенных к домену устройств к Azure AD для работы в Windows 10](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-devices-group-policy/)  
