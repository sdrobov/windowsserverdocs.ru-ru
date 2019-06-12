---
title: Развертывание Windows Server гибридной облачной печати
description: Как настроить Microsoft гибридной облачной печати
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: Windows Server 2016
ms.tgt_pltfrm: na
ms.topic: ''
ms.assetid: fc239aec-e719-47ea-92fc-d82a7247c5e9
author: msjimwu
ms.author: coreyp
manager: dongill
ms.date: 3/15/2018
ms.openlocfilehash: 6e7bb2138afa159f945125d3fc20e4fa365340d5
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66435733"
---
# <a name="deploy-windows-server-hybrid-cloud-print-with-pre-authentication"></a>Развертывание функции Hybrid Cloud Print в Windows Server с помощью предварительной проверки подлинности

>Область применения. Windows Server 2016

В этом разделе для ИТ-администраторов, описывает end-to-end развертывание решения Microsoft гибридной облачной печати. Слои этого решения на основе существующих серверов Windows, выполняющихся в качестве сервера печати и позволяет присоединенных к Azure Active Directory и управляется MDM, управлять устройствами для обнаружения и печать организации принтеров.

## <a name="pre-requisites"></a>Предварительные требования

Есть несколько подписок, служб и компьютеров, которые необходимо получить перед началом этой установки. Они приведены ниже:

-   Подписка Azure AD premium
    
    См. в разделе [приступить к работе с подпиской Azure](https://azure.microsoft.com/trial/get-started-active-directory/), для получения пробной подписки в Azure. 

-   Службы управления мобильными Устройствами, например Intune
    
    См. в разделе [Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune), для получения пробной подписки на Intune.

-   Windows Server под управлением как Active Directory

    См. в разделе [пошаговые: Настройка Active Directory в Windows Server 2016](https://blogs.technet.microsoft.com/canitpro/2017/02/22/step-by-step-setting-up-active-directory-in-windows-server-2016/), для помощи в настройке Active Directory.

-   Работа в качестве сервера печати в Windows Server 2016, присоединенных к домену
    
    См. в разделе [Установка ролей, служб ролей и компонентов с помощью Добавить роли и функции мастера](https://docs.microsoft.com/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#BKMK_installarfw), сведения об установке ролей и служб ролей на Windows Server.

-   Azure AD Connect
    
    См. в разделе [Выборочная установка Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-get-started-custom), для помощи в настройке Azure AD Connect.

-   Соединитель прокси приложения Azure в отдельном домене присоединен компьютер Windows Server
    
    См. в разделе [приступить к работе с прокси приложения и установка соединителя](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-enable), для помощи в настройке соединителя прокси приложения Azure.

-   Общедоступное внешнее имя домена
    
    Можно использовать имя домена, автоматически создаваемые в Azure или приобрести собственное доменное имя.

## <a name="deployment-steps"></a>Шаги развертывания

Это руководство содержит описание действия по установке на пять (5):

- Шаг 1. Установка Azure AD Connect для синхронизации данных между Azure AD и локальной AD
- Шаг 2. Установите пакет гибридной облачной печати на сервере печати
- Шаг 3. Установка Azure прокси приложения (AAP) с использованием Kerberos Constrained Delegation (KCD)
- Шаг 4. Настройка необходимых политик управления мобильными Устройствами
- Шаг 5. Публикация общих принтеров

### <a name="step-1---install-azure-ad-connect-to-sync-between-azure-ad-and-on-premises-ad"></a>Шаг 1 - Установка Azure AD Connect для синхронизации данных между Azure AD и локальной AD
1. На компьютере Windows Server Active Directory Загрузите программное обеспечение Azure AD Connect
2. Запустите пакет установки Azure AD Connect и выберите **использовать стандартные параметры**
3. Введите необходимые сведения в процессе установки и нажмите кнопку **установки**

### <a name="step-2---install-hybrid-cloud-print-package-on-the-print-server"></a>Шаг 2 - пакет установки гибридной облачной печати на сервере печати

1. Установка модулей PowerShell печати гибридного облака
   - Выполните следующие команды из командной строки PowerShell с повышенными правами
      - `find-module -Name "PublishCloudPrinter"` Чтобы убедиться, что компьютер может связаться с коллекции PowerShell (PSGallery)
      - `install-module -Name "PublishCloudPrinter"`

     > ПРИМЕЧАНИЕ. Обмен сообщениями может появиться сообщение о том, что «PSGallery» ненадежного репозитория.  Введите «y», чтобы продолжить установку.

2. Установка решения гибридной облачной печати
    - В одном с повышенными правами командной строке PowerShell перейдите в каталог `C:\Program Files\WindowsPowerShell\Modules\PublishCloudPrinter\1.0.0.0`
    - Выполните следующую команду: <br>
        `CloudPrintDeploy.ps1 -AzureTenant <Domain name used by Azure AD Connect> -AzureTenantGuid <Azure AD Directory ID>`
3. Настройка 2 конечных точек служб IIS для поддержки протокола SSL
   -   SSL-сертификат может быть самозаверяющего сертификата, или, выданного из некоторых доверенных сертификации (ЦС)
   -  Если используется самозаверяющий сертификат, убедитесь, что сертификат импортируется для клиентских компьютеров
4. Установите пакет SQLite
   - Откройте командную строку PowerShell с повышенными правами
   - Выполните следующую команду, чтобы скачать пакеты nuget System.Data.SQLite <br>
       `Register-PackageSource -Name nuget.org -ProviderName NuGet -Location https://www.nuget.org/api/v2/ -Trusted -Force`
   - Выполните следующую команду для установки пакетов<br>
   `Install-Package system.data.sqlite [-requiredversion x.x.x.x] -providername nuget`

   > ПРИМЕЧАНИЕ. Рекомендуется загрузить и установить последнюю версию при исключении «-requiredversion» параметр.

5. Скопируйте DLL-библиотеки SQLite в веб-приложение MopriaCloudService \<bin\> папку (**C:\\inetpub\\wwwroot\\MopriaCloudService\\bin**): <br>
   - SQLite двоичные файлы должны находиться в "\\Program Files\\PackageManagement\\NuGet\\пакетов»

           \\System.Data.SQLite.**Core**.x.x.x.x\\lib\\net46\\System.Data.SQLite.dll
           --\> \<bin\>\\System.Data.SQLite.dll  
           \\System.Data.SQLite.**Core**.x.x.x.x\\build\\net46\\x86\\SQLite.Interop.dll
           --\> \<bin\>\\**x86**\\SQLite.Interop.dll  
           \\System.Data.SQLite.**Core**.x.x.x.x\\build\\net46\\x64\\SQLite.Interop.dll
           --\> \<bin\>\\**x64**\\SQLite.Interop.dll
           \\System.Data.SQLite.**Linq**.x.x.x.x\\lib\\net46\\System.Data.SQLite.Linq.dll
           --\> \<bin\>\\System.Data.SQLite.Linq.dll  
           \\System.Data.SQLite.**EF6**.x.x.x.x\\lib\\net46\\System.Data.SQLite.EF6.dll
           --\> \<bin\>\\System.Data.SQLite.EF6.dll

   > Примечание: x.x.x.x представляет версию SQLite, установленную выше.

6. Обновление `c:\inetpub\wwwroot\MopriaCloudService\web.config` файл и включит версия x.x.x.x SQLite в следующих \<среды выполнения\>/\<assemblyBinding\> разделах:

       <dependentAssembly>
       assemblyIdentity name="System.Data.SQLite" culture="neutral" publicKeyToken="db937bc2d44ff139" /
       <bindingRedirect oldVersion="0.0.0.0-x.x.x.x" newVersion="x.x.x.x" />
       </dependentAssembly>
       <dependentAssembly>
       <assemblyIdentity name="System.Data.SQLite.Core" culture="neutral" publicKeyToken="db937bc2d44ff139" />
       <bindingRedirect oldVersion="0.0.0.0-x.x.x.x" newVersion="x.x.x.x" />
       </dependentAssembly>
       <dependentAssembly>
       <assemblyIdentity name="System.Data.SQLite.EF6" culture="neutral" publicKeyToken="db937bc2d44ff139" />
       <bindingRedirect oldVersion="0.0.0.0-x.x.x.x" newVersion="x.x.x.x" />
       </dependentAssembly>
       <dependentAssembly>
       <assemblyIdentity name="System.Data.SQLite.Linq" culture="neutral" publicKeyToken="db937bc2d44ff139" />
       <bindingRedirect oldVersion="0.0.0.0-x.x.x.x" newVersion="x.x.x.x" />
       </dependentAssembly>

7. Создайте базу данных SQLite:
    -  Скачайте и установите средства SQLite двоичных файлов <https://www.sqlite.org/>
    -  Перейдите к **c:\\inetpub\\wwwroot\\MopriaCloudService\\базы данных** каталога
    -  Выполните следующую команду, чтобы создать базу данных в этом каталоге:  `sqlite3.exe MopriaDeviceDb.db ".read MopriaSQLiteDb.sql"`
    -  В проводнике откройте свойства файла MopriaDeviceDb.db, чтобы добавить пользователей или групп, которым разрешено публиковать mopria запрашивает базу данных на вкладке "Безопасность"
        - Рекомендуется, только добавив необходимые группы администратора пользователей.
8. Регистрация 2 веб-приложения в Azure AD для поддержки проверки подлинности OAuth2
   - Войдите от имени глобального администратора к порталу управления клиента Azure AD
     1. Перейдите на вкладку «Регистрация приложений», чтобы добавить печати конечной точки
        - Добавить приложение, выберите «Регистрация нового приложения»
        - Укажите соответствующее имя и выберите «веб-приложение или API»
        - URL-адрес входа = "<http://MicrosoftEnterpriseCloudPrint/CloudPrint>"
     2. Повторите для конечной точки обнаружения
        - URL-адрес входа = "<http://MopriaDiscoveryService/CloudPrint>"
     3. Повторите для собственного клиентского приложения
        -   При указании имени приложения, убедитесь, что вы выберите «Собственное клиентское приложение» как «тип приложения»
        -   URI перенаправления = « https://\<конечной точки службы машины\>/RedirectUrl»
     4. Перейдите в собственное клиентское приложение «Параметры»
        -   Скопируйте значение «Application ID», используемое для дальнейших этапов установки
        -   Выберите «Необходимые разрешения»
            1.  Нажмите кнопку «Добавить»
            2.  Нажмите кнопку «Выбрать API»
            3.  Поиск печати конечную точку и конечную точку обнаружения по имени, которую вы указали при создании конечной точки приложения
            4.  Добавьте две конечные точки
            5.  Убедитесь, что включен параметр «Делегированные разрешения» для каждой конечной точки приложения
            6.  Убедитесь, что нажать кнопку «Готово» внизу
            7.  Нажмите кнопку «Предоставление разрешения», после добавления обе конечные точки.  Нажмите кнопку «Да» при появлении запроса на утверждение запроса.
        -   Перейдите к «URI ПЕРЕНАПРАВЛЕНИЯ» и добавьте следующие URI перенаправления в список: `ms-appx-web://Microsoft.AAD.BrokerPlugin/\<NativeClientAppID\>`
            `ms-appx-web://Microsoft.AAD.BrokerPlugin/S-1-15-2-3784861210-599250757-1266852909-3189164077-45880155-1246692841-283550366`

### <a name="step-3---install-azure-application-proxy-aap-with-kerberos-constrained-delegation-kcd"></a>Шаг 3: Установка прокси приложения Azure (AAP) с использованием Kerberos Constrained Delegation (KCD)
1. Имя входа на портал управления клиента Azure AD (AAD)
    - В списке меню AAD выберите «Прокси приложения»
    - Нажмите кнопку «Включить прокси приложения» в верхней части экрана
    - Скачайте «Соединитель прокси приложения» на компьютере Windows Server присоединен к домену, который будет выступать в качестве прокси-сервера приложений Web (WAP).
2. WAP-компьютера, имя входа с правами администратора и установка «Соединитель прокси приложения»
    - Во время установки присвойте соединитель прокси приложения учетные данные в Azure принципу, который требуется включить AAP на
    - Убедитесь, что WAP-компьютера подключен к домену в локальной Active Directory
3. На компьютере, Active Directory, перейдите в каталог **Сервис -> пользователи и компьютеры**
    - Выберите компьютер, на котором работает соединитель прокси приложения
    - Щелкните правой кнопкой мыши и выберите **свойства "->" делегирование** вкладку
    - Выберите **доверять компьютеру делегирование только указанных служб.**
    - Выберите **использовать любой протокол проверки подлинности.**
    - В разделе **служб, которым эта учетная запись может предоставлять делегированные учетные данные**
        - Добавьте значение для идентификатора SPN компьютера, где запущены службы (service MopriaDiscoveryService и MicrosoftEnterpriseCloudPrint)
            - Для имени участника-службы введите имя участника-службы из самой виртуальной машине, т. е. «УЗЛА /\<MachineName\>.\< Домен\>"<br>
                `HOST/appServer.Contoso.com`
4. Вернитесь на портал управления клиента AAD и добавьте прокси приложений
   - Перейдите к **корпоративные приложения** вкладку
   - Нажмите кнопку **нового приложения**
   - Выберите **локальное приложение** и заполните поля
       - Имя: Любое имя, которое вы хотите
       - Внутренний URL-адрес: Это внутренний URL-адрес к облачной службе обнаружения mopria запрашивает доступ к которой можно получить компьютере WAP
       - Внешний URL-адрес: Настройте нужные для вашей организации
       - Метод предварительной проверки подлинности: Azure Active Directory

     >   Примечание. Если вы не нашли все параметры, приведенные выше, добавить прокси-сервера с параметрами по и затем выберите только что созданный прокси приложения и перейдите к **прокси приложения** вкладка и добавить все указанные выше сведения.

   - После создания вернитесь к **корпоративные приложения** -> **все приложения**, выберите новое приложение, вы только что создали
   - Перейдите к **единого входа**, убедитесь, что «единый вход» режим «Встроенная проверка подлинности Windows»
   - Присвоено имя участника-службы, указанные в шаг 3.3 выше «SPN внутреннего приложения»
   - Убедитесь, что «делегированное удостоверение для входа» имеет значение «Имя участника-пользователя»

5. Повторить 4 выше, для облачной службы печати Enterprise и ввести внутренний URL-адрес к облачной службе печати Enterprise
6. Вернитесь на портал управления Azure AD клиента и перейти к **регистрация приложений** и выберите собственное клиентское приложение -> «Параметры»
    - Выберите **необходимые разрешения**
        - Добавьте 2 новый прокси приложения, которые вы только что создали
        - Предоставьте делегированные разрешения эти 2 приложения
        - После добавления обоих приложений прокси-сервера, нажмите кнопку «Предоставление разрешений».  Нажмите кнопку «Да» при появлении запроса на утверждение запроса.

7. Включить проверку подлинности Windows в службах IIS для компьютеров Mopria облачной службы и Корпоративная облачная служба печати
    - Убедитесь, что установлен компонент проверки подлинности Windows:
        1. Открытие диспетчера сервера
        2. Нажмите кнопку **управление**
        3. Нажмите кнопку **Добавить роли и компоненты**
        4. Выберите **Установка ролей или компонентов**
        5. Выберите сервер
        6. В разделе веб-сервер (IIS) -> веб-сервер "->" безопасности, выберите **проверки подлинности Windows**
        7. Нажмите кнопку Далее, до завершения установки
    - Включение проверки подлинности Windows в службах IIS.
        1. Откройте диспетчер служб IIS (IIS)
        2. Для каждой службы или сайта:
            1.  Выберите службы или сайта
            2.  Дважды щелкните **проверки подлинности**
            3.  Нажмите кнопку **проверки подлинности Windows** и нажмите кнопку **включить** под **действия**

### <a name="step-4---configure-the-required-mdm-policies"></a>Шаг 4 — Настройка необходимых политик управления мобильными Устройствами
- Имя входа для своего поставщика услуг MDM.
- Найдите группу политики корпоративной облачной печати и настроить политики следуя приведенным ниже рекомендациям:
  - CloudPrintOAuthAuthority = https://login.microsoftonline.com/\<Azure AD Directory ID\>
  - CloudPrintOAuthClientId = значение «Application ID» собственного веб-приложения, зарегистрированный на портале управления Azure AD
  - CloudPrinterDiscoveryEndPoint = внешний URL-адрес mopria запрашивает обнаружение службы прокси приложения Azure в шаг 3.3 (должно быть ровно прежним, но без завершающие /)
  - MopriaDiscoveryResourceId = внешний URL-адрес mopria запрашивает обнаружение службы прокси приложения Azure в шаг 3.4 (должен быть точно так же, включая завершающий символ /)
  - CloudPrintResourceId = внешний URL-адрес Enterprise Cloud Print службы прокси приложения Azure в шаг 3.5 (должен быть точно так же, включая завершающий символ /)
  - DiscoveryMaxPrinterLimit = \<положительное целое число\>

>   Примечание. Если вы используете службу Microsoft Intune, можно найти эти параметры в категории «Облако принтер».

|Intune отображаемое имя                     |Политика                         |
|----------------------------------------|-------------------------------|
|URL-адрес обнаружения принтера                   |CloudPrinterDiscoveryEndpoint  |
|URL-адрес центра доступа к принтеру            |CloudPrintOAuthAuthority       |
|GUID приложения собственного клиента Azure            |CloudPrintOAuthClientId        |
|URI ресурса службы печати              |CloudPrintResourceId           |
|Максимальное число принтеров для запроса (только для мобильных устройств)  |DiscoveryMaxPrinterLimit       |
|URI ресурса службы обнаружения принтера  |MopriaDiscoveryResourceId      |

>   Примечание. Если группа политики облачной печати недоступна, но поставщик MDM поддерживает параметры OMA-URI, можно задать те же политики.  См. в <a href="https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint#enterprisecloudprint-cloudprintoauthauthority">статье</a> для дополнительной информации.

- OMA-URI
    - `CloudPrintOAuthAuthority = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority`
        - Значение = `https://login.microsoftonline.com/` \<идентификатор каталога Azure AD\>
    - `CloudPrintOAuthClientId = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrintOAuthClientId`
        - Значение = \<идентификатор приложения Azure AD собственного приложения\>
    - `CloudPrinterDiscoveryEndPoint = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrinterDiscoveryEndPoint`
        - Значение = внешний URL-адрес mopria запрашивает обнаружение службы прокси приложения Azure в шаг 3.3 (должно быть ровно прежним, но без завершающие /)
    - `MopriaDiscoveryResourceId = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/MopriaDiscoveryResourceId`
        - Значение = внешний URL-адрес mopria запрашивает обнаружение службы прокси приложения Azure в шаг 3.4 (должен быть точно так же, включая завершающий символ /)
    - `CloudPrintResourceId = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrintResourceId`
        - Значение = внешний URL-адрес Enterprise Cloud Print службы прокси приложения Azure в шаг 3.5 (должен быть точно так же, включая завершающий символ /)
    - `DiscoveryMaxPrinterLimit = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/DiscoveryMaxPrinterLimit`
        - Значение = \<положительное целое число\>

### <a name="step-5---publish-desired-shared-printers"></a>Шаг 5 — нужный общих принтеров "Опубликовать"
1. Установить нужный принтер на сервере печати
2. Общий доступ к принтеру через пользовательский Интерфейс свойств принтера
3. Выберите нужный набор пользователей для предоставления доступа
4. Сохраните изменения и закройте окно свойств принтера
5. С компьютера Windows 10 Fall Creator Update откройте командную строку с повышенными привилегиями Windows PowerShell
   1. Выполните следующие команды
      - `find-module -Name "PublishCloudPrinter"` Чтобы убедиться, что компьютер может связаться с коллекции PowerShell (PSGallery)
      - `install-module -Name "PublishCloudPrinter"`

        >   ПРИМЕЧАНИЕ. Обмен сообщениями может появиться сообщение о том, что «PSGallery» ненадежного репозитория.  Введите «y», чтобы продолжить установку.

      - Публикация CloudPrinter
        - Принтер = имя общего принтера, которая была определена
        - Производитель = производителя принтера
        - Модель = модель принтера
        - OrgLocation = JSON строка, задающая расположение принтера, например:   `{"attrs": [{"category":"country", "vs":"USA", "depth":0}, {"category":"organization", "vs":"Microsoft", "depth":1}, {"category":"site", "vs":"Redmond, WA", "depth":2}, {"category":"building", "vs":"Building 1", "depth":3}, {"category":"floor\_number", "vn":1, "depth":4}, {"category":"room\_name", "vs":"1111", "depth":5}]}`
        - SDDL = Строка SDDL, представляющая разрешений для принтера. Это можно сделать путем изменения на вкладке Безопасность свойства принтера соответствующим образом и затем выполните следующую команду в командной строке: `(Get-Printer PrinterName -full).PermissionSDDL`
            Например "G:DUD:(A;OICI;FA;;;WD)"

          > ПРИМЕЧАНИЕ. Необходимо будет добавить **`O:BA`** префикс к результату в командной строке указанную выше команду перед установкой значения как параметры SDDL.  Пример. SDDL = `O:BAG:DUD:(A;OICI;FA;;;WD)`

        - DiscoveryEndpoint = внешний URL-адрес mopria запрашивает обнаружение службы прокси приложения Azure в шаг 3.4
        - PrintServerEndpoint = внешний URL-адрес Enterprise Cloud Print службы прокси приложения Azure в шаг 3.5
        - AzureClientId = идентификатор приложения для зарегистрированных собственного веб-приложения значение выше
        - AzureTenantGuid = идентификатор каталога клиента Azure AD
        - DiscoveryResourceId = [необязательно] идентификатор приложения через прокси облачной службы обнаружения Mopria

        > ПРИМЕЧАНИЕ. В командной строке также можно ввести все значения обязательных параметров.<br>
        **Публикация CloudPrinter** синтаксис команды PowerShell: <br>
        Публикация CloudPrinter-принтера \<строка\> -производителя \<строка\> -модели \<строка\> - OrgLocation \<строка\> - Sddl \<строка\> - DiscoveryEndpoint \<строка\> - PrintServerEndpoint \<строка\> - AzureClientId \<строка\> - AzureTenantGuid \<строка\> [-DiscoveryResourceId \<строка\>] <br>
        Пример команды: `publish-cloudprinter -Printer EcpPrintTest -Manufacturer Microsoft -Model FilePrinterEcp -OrgLocation '{"attrs": [{"category":"country", "vs":"USA", "depth":0}, {"category":"organization", "vs":"MyCompany", "depth":1}, {"category":"site", "vs":"MyCity, State", "depth":2}, {"category":"building", "vs":"Building 1", "depth":3}, {"category":"floor\_number", "vn":1, "depth":4}, {"category":"room\_name", "vs":"1111", "depth":5}]}' -Sddl "O:BAG:DUD:(A;OICI;FA;;;WD)" -DiscoveryEndpoint https://<services-machine-endpoint>/mcs -PrintServerEndpoint https://<services-machine-endpoint>/ecp -AzureClientId <Native Web App ID> -AzureTenantGuid <Azure AD Directory ID> -DiscoveryResourceId <Proxied Mopria Discovery Cloud Service App ID>`


## <a name="verifying-the-deployment"></a>Проверка развертывания
На устройства присоединены к Azure AD с настройки политик управления мобильными Устройствами:
- Откройте браузер и перейти к https://&lt;конечной точки службы машины &gt; /mcs/services (внешний URL-адрес для конечной точки обнаружения)
- Вы должны увидеть текст JSON, описывающий набор функций этой конечной точки
- Последовательно выберите пункты «параметры операционной системы —\> устройств —\> принтеров и сканеров»
    - Вы увидите ссылку «Search for облачных принтеров»
    - Щелкните ссылку
    - Щелкните ссылку «Выберите область поиска»
        - Вы должны увидеть иерархии расположение устройства
    - Выберите расположение и нажмите кнопку **ОК** и нажмите кнопку **поиска** кнопку, чтобы найти принтеров
    - Выберите принтер и нажмите кнопку **добавить устройства** кнопки
    - После установки успешно принтер печататйте на принтер из избранные приложения

>   Примечание. При использовании принтера «EcpPrintTest», можно найти выходной файл на компьютере сервера печати в разделе «C:\\ECPTestOutput\\EcpTestPrint.xps» расположение.
