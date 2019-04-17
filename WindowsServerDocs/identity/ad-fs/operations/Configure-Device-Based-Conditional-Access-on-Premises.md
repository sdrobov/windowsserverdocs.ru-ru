---
ms.assetid: 35de490f-c506-4b73-840c-b239b72decc2
title: "Настройка условного доступа на основе устройства локально"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 08/11/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 47afd0c6963bd8b8b4dde82650cf807c1954b40b
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="configure-on-premises-conditional-access-using-registered-devices"></a>Настройка локального условного доступа с помощью зарегистрированных устройств

>Область применения: Windows Server 2016, Windows Server 2012 R2  

Следующий документ поможет выполнить процесс установки и настройки на локальный условный доступ с зарегистрированных устройств.

![условный доступ](media/Using-Device-based-Conditional-Access-on-Premises/ADFS_ITPRO4.png)  

## <a name="infrastructure-pre-requisites"></a>Необходимые компоненты инфраструктуры
Следующие каждого условия являются обязательными, прежде чем начать с локального условного доступа. 

|Требования|Описание
|-----|-----
|Подписку Azure AD с Azure AD Premium | Чтобы включить устройство записи обратно на локальный условный доступ — [установлено бесплатной пробной версии](https://azure.microsoft.com/en-us/trial/get-started-active-directory/)  
|Подписки Intune|требуется только для интеграции MDM для сценариев соответствия устройства -[установлено бесплатной пробной версии](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0)
|Azure AD Connect|Ноябрь 2015 QFE или более поздней версии.  Получите последнюю версию [здесь](https://www.microsoft.com/en-us/download/details.aspx?id=47594).  
|В Windows Server 2016|Сборки 10586 или более поздней версии для служб AD FS  
|Схема Windows Server 2016 Active Directory|Требуется схема уровне 85 или выше.
|Контроллер домена Windows Server 2016|Это только необходимые для развертываний доверия ключ Hello для бизнеса.  Дополнительные сведения можно найти в [здесь](https://aka.ms/whfbdocs).  
|Клиент Windows 10|Сборка 10586 или более новые, присоединенного к домену выше необходим для присоединения к домену Windows 10 и Microsoft Passport рабочих только для сценариев  
|Учетная запись пользователя Azure AD с назначена лицензия Azure AD Premium|Для регистрации устройства  


 
## <a name="upgrade-your-active-directory-schema"></a>Обновить схему Active Directory
Чтобы воспользоваться локального условного доступа для зарегистрированных устройств, необходимо сначала обновить свою схему AD.  Должны быть выполнены следующие условия:
    - Схема должна быть 85 или более поздней версии
    - Это только необходимые для леса, который присоединен к AD FS

> [!NOTE]
> Если вы установили Azure AD Connect перед обновлением до версии схемы (уровень 85 или более поздней версии) в Windows Server 2016, необходимо будет повторно запустите установку с Azure AD Connect и обновить локальную схему AD, чтобы правило синхронизации для msDS-KeyCredentialLink настроен.

### <a name="verify-your-schema-level"></a>Проверьте уровень схемы
Чтобы проверить уровень схемы, сделайте следующее:

1.  Можно использовать средства ADSIEdit или LDP и подключитесь к контекст именования схемы.  
2.  С помощью ADSIEdit, щелкните правой кнопкой мыши «CN = Schema, CN = Configuration, DC =<domain>, DC =<com> и выберите пункт Свойства.  Домен Relpace и фрагменты com со сведениями о леса.
3.  В разделе Редактор атрибутов найдите атрибута objectVersion и оно сообщит вам, ваша версия.  

![Редактирование ADSI](media/Configure-Device-Based-Conditional-Access-on-Premises/adsiedit.png)  

Также можно использовать следующий командлет PowerShell (вместо объекта с данные контекста именования схемы):

``` powershell
Get-ADObject "cn=schema,cn=configuration,dc=domain,dc=local" -Property objectVersion
    
```

![PowerShell](media/Configure-Device-Based-Conditional-Access-on-Premises/pshell1.png) 

Дополнительные сведения об обновлении см. в разделе [обновление контроллеров домена до Windows Server 2016](../../ad-ds/deploy/Upgrade-Domain-Controllers-to-Windows-Server-2016.md). 

## <a name="enable-azure-ad-device-registration"></a>Включение регистрации устройств Azure AD  
Чтобы настроить этот сценарий, необходимо настроить возможность регистрации устройства в Azure AD.  

Для этого следуйте инструкциям в разделе [настройке присоединения к Azure AD в вашей организации](https://azure.microsoft.com/en-us/documentation/articles/active-directory-azureadjoin-setup/)  

## <a name="setup-ad-fs"></a>Настройка AD FS  
1. Создание [новой ферме AD FS 2016](https://technet.microsoft.com/library/dn486775.aspx).   
2.  Или [перенести](../../ad-fs/deployment/Upgrading-to-AD-FS-in-Windows-Server-2016.md) фермы AD FS 2016 из AD FS 2012 R2  
4. Развертывание [Azure AD Connect](https://azure.microsoft.com/documentation/articles/active-directory-aadconnectfed-whatis/) использование пользовательский путь для подключения службы федерации Active Directory к Azure AD.  

## <a name="configure-device-write-back-and-device-authentication"></a>Настройка проверки подлинности устройства и обратно в записи устройства  
> [!NOTE]
> При запуске Azure AD Connect, используя стандартные параметры объектов AD были созданы для вас.  Однако в большинстве сценариев Служб федерации Active Directory, Azure AD Connect была запущена с особые параметры, чтобы настроить AD FS, поэтому ниже действия необходимы.  

### <a name="create-ad-objects-for-ad-fs-device-authentication"></a>Создание объектов AD для проверки подлинности устройств AD FS  
Если фермы AD FS не настроен для проверки подлинности устройств (это можно увидеть в консоли управления AD FS в рамках службы регистрации устройства ->), выполните следующие действия для создания объектов AD DS и конфигурации.  

![Регистрация устройства](media/Configure-Device-Based-Conditional-Access-on-Premises/device1.png)

>Примечание: Ниже команды требуется средствами администрирования Active Directory, поэтому если ваш сервер федерации также не является контроллером домена, установить средства, с помощью шаг 1 ниже.  В противном случае можно пропустить первый шаг.  

1.  Запустите **Добавить роли и компоненты** мастер и выберите компонент **средства удаленного администрирования сервера** -> **средства администрирования ролей** -> **AD DS и AD LDS средства** -> выберите оба **модуля Active Directory для Windows PowerShell** и **средства AD DS**.

![Регистрация устройства](media/Configure-Device-Based-Conditional-Access-on-Premises/device2.png)
  
2.  На основного сервера AD FS убедитесь, использованная в Доменных службах Active Directory пользователя с правами администратора предприятия (EA) и откройте командной строки powershell с повышенными правами.  Затем выполните следующие команды PowerShell:  
    
    `Import-module activedirectory`  
    `PS C:\> Initialize-ADDeviceRegistration -ServiceAccountName "<your service account>" ` 
3.  На всплывающем окне нажмите кнопку "Да".

>Примечание: Если службы AD FS настроен для использования групповой Управляемой учетной записи, введите имя учетной записи в формате «domain\accountname$»

![Регистрация устройства](media/Configure-Device-Based-Conditional-Access-on-Premises/device3.png)  

Выше PSH создает следующие объекты:  


- Контейнер RegisteredDevices под разделом домена AD  
- Контейнер служб регистрации устройства и объектов в разделе конфигурации--> служб--> Конфигурация регистрации устройств  
- Контейнер DKM службы регистрации устройств и объектов в разделе конфигурации--> служб--> Конфигурация регистрации устройств  

![Регистрация устройства](media/Configure-Device-Based-Conditional-Access-on-Premises/device4.png)  

4.  После этого, вы увидите сообщение успешное завершение.

![Регистрация устройства](media/Configure-Device-Based-Conditional-Access-on-Premises/device5.png) 

###        <a name="create-service-connection-point-scp-in-ad"></a>Создание точки подключения службы (SCP) в AD  
Если вы планируете использовать присоединение к домену Windows 10 (с автоматической регистрации в Azure AD), как описано ниже, выполните следующие команды, чтобы создать точки подключения службы в Доменных службах Active Directory  
1.  Откройте Windows PowerShell и выполните следующую команду:
    
    `PS C:>Import-Module -Name "C:\Program Files\Microsoft Azure Active Directory Connect\AdPrep\AdSyncPrep.psm1" ` 

>Примечание: Если необходимо, скопируйте файл AdSyncPrep.psm1 с Azure AD Connect сервера.  Этот файл находится в программе Files\Microsoft Azure Active Directory Connect\AdPrep

![Регистрация устройства](media/Configure-Device-Based-Conditional-Access-on-Premises/device6.png)   

2. Предоставить свои учетные данные глобального администратора Azure AD  

    `PS C:>$aadAdminCred = Get-Credential`

![Регистрация устройства](media/Configure-Device-Based-Conditional-Access-on-Premises/device7.png) 

3.  Выполните следующую команду PowerShell 

    `PS C:>Initialize-ADSyncDomainJoinedComputerSync -AdConnectorAccount [AD connector account name] -AzureADCredentials $aadAdminCred ` 

Где [AD соединителя учетной записи имя] — Имя учетной записи, настроенной в Azure AD Connect при добавлении локальной среды Доменных служб Active directory.
  
Вышеуказанные команды включения клиентов Windows 10 найти правильный домен Azure AD для присоединения к путем создания объекта serviceConnectionpoint в Доменных службах Active Directory.  

### <a name="prepare-ad-for-device-write-back"></a>Подготовка AD обратно записи устройства   
Чтобы обеспечить Доменных объектов и контейнеров в правильном состоянии для записи заднюю устройствами с Azure AD, выполните следующие действия.

1.  Откройте Windows PowerShell и выполните следующую команду:  

    `PS C:>Initialize-ADSyncDeviceWriteBack -DomainName <AD DS domain name> -AdConnectorAccount [AD connector account name] ` 

Где [AD соединителя учетной записи имя] — Имя учетной записи, настроенной в Azure AD Connect при добавлении локальной среды Доменных служб Active directory в формате domain\accountname  

Приведенная выше команда создает следующие объекты для записи устройства к AD DS, если они еще не существует и позволяет получить доступ к указанным именем учетной записи AD соединителя  

- Контейнер RegisteredDevices в разделе домена AD  
- Контейнер служб регистрации устройства и объектов в разделе конфигурации--> служб--> Конфигурация регистрации устройств  

### <a name="enable-device-write-back-in-azure-ad-connect"></a>Включить запись устройства в Azure AD подключения  
Если вы еще не перед таким образом, включение запись устройства в Azure AD Connect, запустив мастер еще раз и выбрав **«Настройка параметров синхронизации»**, установив флажок обратно устройства записи и выбрав леса, в котором вы запустили выше командлеты  

### <a name="configure-device-authentication-in-ad-fs"></a>Настройка проверки подлинности устройства в AD FS  
С помощью командное окно PowerShell с повышенными привилегиями, настройте политики службы федерации Active Directory, выполнив следующую команду  

`PS C:>Set-AdfsGlobalAuthenticationPolicy -DeviceAuthenticationEnabled $true -DeviceAuthenticationMethod All` 

### <a name="check-your-configuration"></a>Проверьте конфигурацию  
Для справки ниже приведен полный список устройств, контейнеры и разрешения, необходимые для обратной записи устройства и проверки подлинности для работы AD DS
 


- объект типа ms-доменных служб Active Directory-DeviceContainer в CN = RegisteredDevices, DC =&lt;домена&gt;        
    - доступ на чтение для учетной записи службы AD FS   
    - чтение и запись доступа к Azure AD Connect синхронизации учетной записи AD соединителя</br></br>

- В контейнере CN = Device Registration Configuration, CN = Services, CN = Configuration, DC =&lt;домена&gt;  
- DKM службы регистрации устройств контейнера в контейнере выше

![Регистрация устройства](media/Configure-Device-Based-Conditional-Access-on-Premises/device8.png) 
 


- объект типа serviceConnectionpoint в CN =&lt;guid&gt;, CN = регистрации устройств

- Конфигурации, CN = Services, CN = Configuration, DC =&lt;домена&gt;  
 - чтение и запись доступа к указанному имени учетной записи AD соединителя для нового объекта</br></br> 


- объект типа msDS-DeviceRegistrationServiceContainer в CN = службы регистрации устройств, CN = Device Registration Configuration, CN = Services, CN = Configuration, DC = & ltdomain >  


- объект типа msDS-DeviceRegistrationService в контейнере выше  

### <a name="see-it-work"></a>В разделе его работы  
Чтобы оценить новых утверждений, а также политики, необходимо сначала зарегистрируйте устройство.  Например, вы можете компьютере с Windows 10, с помощью приложения «параметры» в разделе Система -> о присоединении к Azure AD или присоединения к домену Windows 10 можно настроить с помощью регистрации автоматического устройств следующие дополнительные действия [здесь](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-devices-group-policy/).  Сведения о соединении Windows 10 мобильных устройств см. в документе [здесь](https://technet.microsoft.com/itpro/windows/manage/join-windows-10-mobile-to-azure-active-directory).  

Для простейший оценки вход с помощью тестового приложения, которое показывает список утверждений Служб федерации Active Directory. Можно в разделе новых утверждений, включая isManaged, isCompliant и trusttype.  Если включить Microsoft Passport для работы, вы увидите также prt утверждений.  
 

## <a name="configure-additional-scenarios"></a>Настройка дополнительных сценариев  
### <a name="automatic-registration-for-windows-10-domain-joined-computers"></a>Автоматическая регистрация для Windows 10 к домену компьютеров  
Для обеспечения регистрации автоматического устройства для Windows 10 домена компьютеров, присоединенных к, выполните шаги 1 и 2 [здесь](https://azure.microsoft.com/documentation/articles/active-directory-azureadjoin-devices-group-policy/).   
Это поможет вам в следующих целях:  

1. Обеспечить вашей точки подключения службы в Доменных службах Active Directory существует и имеет правильные разрешения (мы создали этот объект выше, но он не помешает двойной проверки).  
2. Убедитесь, что службы федерации Active Directory настроена правильно  
3. Убедитесь, что система AD FS имеет правильный конечные точки включена и правила, настроенные для утверждений   
4. Настройка параметров групповой политики, необходимые для регистрации устройств автоматического присоединен к домену компьютеров   

### <a name="microsoft-passport-for-work"></a>Microsoft Passport for Work   
Сведения о включении Windows 10 с помощью Microsoft Passport for Work см. в разделе [включить Microsoft Passport для работы в организации.](https://azure.microsoft.com/en-us/documentation/articles/active-directory-azureadjoin-passport-deployment/)  

### <a name="automatic-mdm-enrollment"></a>Автоматическая регистрация в MDM   
Чтобы включить автоматическую регистрацию в MDM зарегистрированных устройств, вы можете использовать утверждений isCompliant в политике управления доступом, выполните действия [здесь.](https://blogs.technet.microsoft.com/ad/2015/08/14/windows-10-azure-ad-and-microsoft-intune-automatic-mdm-enrollment-powered-by-the-cloud/)  

## <a name="troubleshooting"></a>Устранение неполадок  
1.  Если сообщение об ошибке `Initialize-ADDeviceRegistration` , жалуется об объекте, уже существующие в неправильном состоянии, такие как «объект службы drs обнаружена без все обязательные атрибуты», выполняемых Azure AD Connect powershell команды ранее и есть частичные конфигурации в AD DS.  Попробуйте вручную удалить объекты в **CN = Device Registration Configuration, CN = Services, CN = Configuration, DC =&lt;домена&gt; ** и повторите попытку.  
2.  Для Windows 10 объединенных в домен клиентов  
    1. Убедитесь, что проверка подлинности устройств работает, выполните вход в домен клиент присоединен к тестовой учетной записи пользователя. Для запуска быстрой подготовки, блокировать и разблокировать рабочий стол по крайней мере один раз.   
    2. Инструкции для проверки учетных данных ключа stk ссылку на объект AD DS (Синхронизация по-прежнему нужно выполнить дважды?)  
3.  Если сообщение об ошибке при попытке зарегистрировать компьютер Windows, который уже регистрации устройства, но не удается или уже отмене регистрации устройства, возможно, фрагменту конфигурация регистрации устройств в реестре.  Проверка и удалить это, выполните следующие действия:  
    1. На компьютере Windows, откройте средство Regedit и перейдите к **HKLM\Software\Microsoft\Enrollments**   
    2. В этом разделе будет много подразделов в форме GUID.  Перейдите в раздел, который имеет ~ 17 значения в нем, а «EnrollmentType» на «6» [присоединено к MDM] или «13» (присоединенные к Azure AD)  
    3. Изменение **EnrollmentType** для **0** 
    4. Повторите попытку регистрации или регистрации устройств  

### <a name="related-articles"></a>Связанные статьи  
* [Защита доступа к Office 365 и другие приложения, подключенные к Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access/)  
* [Устройство политики условного доступа для службы Office 365](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-device-policies/)  
* [Настройка локального условного доступа с помощью регистрации устройств Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-device-registration-on-premises-setup)  
* [Подключение присоединенных к домену устройств к Azure AD для работы в Windows 10](https://azure.microsoft.com/en-us/documentation/articles/active-directory-azureadjoin-devices-group-policy/)  
