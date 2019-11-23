---
title: Развертывание гибридной облачной системы Windows Server — транзитная проверка подлинности
description: Как настроить Гибридное облако Microsoft для печати с сквозной проверкой подлинности
ms.prod: windows-server
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
ms.openlocfilehash: e9d461e2e9442e9473a6d2c9b13d9ede17361348
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370399"
---
# <a name="deploy-windows-server-hybrid-cloud-print-with-passthrough-authentication"></a>Развертывание гибридного облака Windows Server с сквозной проверкой подлинности

>Область применения: Windows Server 2016

В этой статье для ИТ-администраторов описывается комплексное развертывание гибридного облачного решения Microsoft для печати. Эти уровни решения поверх существующих серверов Windows Server, работающих в качестве сервера печати, и позволяют присоединять Azure Active Directory и управляемые MDM, устройства для обнаружения и печати на управляемых принтерах Организации.

## <a name="pre-requisites"></a>Предварительные требования

Перед началом установки необходимо получить несколько подписок, служб и компьютеров. Они приведены ниже:

-   Подписка Azure AD Premium
    
    Пробная подписка на Azure приведена в статье Начало [работы с подпиской Azure](https://azure.microsoft.com/trial/get-started-active-directory/). 

-   Служба MDM, например Intune
    
    Для пробной подписки на Intune см. [Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune).

-   Windows Server, работающий как Active Directory

    Дополнительные сведения о настройке Active Directory см. [в статье Пошаговое руководство. настройка Active Directory в Windows Server 2016](https://blogs.technet.microsoft.com/canitpro/2017/02/22/step-by-step-setting-up-active-directory-in-windows-server-2016/).

-   Присоединенный к домену Windows Server 2016, работающий как сервер печати
    
    Сведения об установке ролей и служб ролей в Windows Server см. в [статье Установка ролей, служб ролей и компонентов с помощью мастера добавления ролей и](https://docs.microsoft.com/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#BKMK_installarfw)компонентов.

-   Azure AD Connect
    
    Дополнительные сведения о настройке Azure AD Connect см. в разделе [Выборочная установка Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).

-   Соединитель прокси приложения Azure на отдельном компьютере, присоединенном к домену Windows Server
    
    Дополнительные сведения о настройке соединителя прокси приложения Azure см. [в статье Начало работы с прокси приложения и установка соединителя](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-enable).

-   Общедоступное доменное имя
    
    Вы можете использовать имя домена, созданное Azure, или приобрести собственное доменное имя.

## <a name="deployment-steps"></a>Шаги развертывания

В этом руководстве описаны пять (5) шагов установки:

- Шаг 1. Установка Azure AD Connect для синхронизации между Azure AD и локальной службой AD
- Шаг 2. Установка гибридного облачного пакета печати на сервере печати
- Шаг 3. Установка прокси приложения Azure (схема AAP) с сквозной проверкой подлинности
- Шаг 4. Настройка необходимых политик MDM
- Шаг 5. Публикация общих принтеров

### <a name="step-1---install-azure-ad-connect-to-sync-between-azure-ad-and-on-premises-ad"></a>Шаг 1. Установка Azure AD Connect для синхронизации между Azure AD и локальной службой AD
1. Загрузите Azure AD Connect программное обеспечение на компьютере Active Directory Windows Server
2. Запустите пакет установки Azure AD Connect и выберите **параметр использовать Экспресс параметры** .
3. Введите сведения, запрошенные в процессе установки, и нажмите кнопку **установить** .

### <a name="step-2---install-hybrid-cloud-print-package-on-the-print-server"></a>Шаг 2. Установка гибридного облачного пакета печати на сервере печати

1. Установка модулей PowerShell для гибридной облачной печати
   - Выполните следующие команды из командной строки PowerShell с повышенными привилегиями.
      - `find-module -Name "PublishCloudPrinter"`, чтобы убедиться, что компьютер может достичь коллекция PowerShell (PSGallery).
      - `install-module -Name "PublishCloudPrinter"`

     > Примечание. Вы можете увидеть обмен сообщениями о том, что "PSGallery" является недоверенным репозиторием.  Введите "y", чтобы продолжить установку.

2. Установка гибридного облачного решения для печати
    - В той же командной строке PowerShell с повышенными привилегиями измените каталог на `C:\Program Files\WindowsPowerShell\Modules\PublishCloudPrinter\1.0.0.0`
    - Выполните следующую команду: <br>
        `CloudPrintDeploy.ps1 -AzureTenant <Domain name used by Azure AD Connect> -AzureTenantGuid <Azure AD Directory ID>`
3. Настройка двух конечных точек IIS для поддержки SSL
   -   SSL-сертификат может представлять собой самозаверяющий сертификат или один, выданный доверенным центром сертификации (ЦС).
   -  Если используется самозаверяющий сертификат, убедитесь, что сертификат импортирован на клиентские компьютеры.
4. Установка пакета SQLite
   - Открытие командной строки PowerShell с повышенными привилегиями
   - Выполните следующую команду, чтобы скачать пакеты NuGet System. Data. SQLite <br>
       `Register-PackageSource -Name nuget.org -ProviderName NuGet -Location https://www.nuget.org/api/v2/ -Trusted -Force`
   - Выполните следующую команду, чтобы установить пакеты<br>
   `Install-Package system.data.sqlite [-requiredversion x.x.x.x] -providername nuget`

   > Примечание. рекомендуется загрузить и установить последнюю версию, опустив параметр "-requiredversion".

5. Скопируйте библиотеки DLL SQLite в папку Моприаклаудсервице webapp \<bin\> (**C:\\inetpub\\wwwroot\\моприаклаудсервице\\bin**): <br>
   - Двоичные файлы SQLite должны иметь\\Program Files\\PackageManagement\\пакетов NuGet\\

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

   > Примечание. x. x. x. x — это версия SQLite, установленная выше.

6. Обновите файл `c:\inetpub\wwwroot\MopriaCloudService\web.config`, чтобы включить SQLite версии x. x. x. x в следующей \<среды выполнения\>/\<assemblyBinding\> разделов:

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
    -  Скачайте и установите двоичные файлы средств SQLite из <https://www.sqlite.org/>
    -  Перейдите в раздел **c:\\inetpub\\wwwroot\\моприаклаудсервице\\каталог базы данных**
    -  Выполните следующую команду, чтобы создать базу данных в этом каталоге: `sqlite3.exe MopriaDeviceDb.db ".read MopriaSQLiteDb.sql"`
    -  В проводнике откройте свойства файла Моприадевицедб. DB, чтобы добавить пользователей и группы, которым разрешено публиковать в базе данных Mopria на вкладке Безопасность.
        - Рекомендуется добавлять только необходимую группу пользователей admin.
8. Регистрация 2 веб-приложения в Azure AD для поддержки проверки подлинности OAuth2
   - Войдите как глобальный администратор на портал управления клиентами Azure AD.
     1. Перейдите на вкладку "Регистрация приложений", чтобы добавить конечную точку печати
        - Добавление приложения выберите "Регистрация нового приложения"
        - Укажите соответствующее имя и выберите "веб-приложение или API".
        - URL-адрес входа = "<http://MicrosoftEnterpriseCloudPrint/CloudPrint>"
     2. Повторить для конечной точки обнаружения
        - URL-адрес входа = "<http://MopriaDiscoveryService/CloudPrint>"
     3. Повторение для собственного клиентского приложения
        -   При предоставлении имени приложения убедитесь, что в качестве типа приложения выбрано "собственное клиентское приложение".
        -   URI перенаправления = "https://\<Services-Machine-Endpoint\>/Редиректурл"
     4. Переход в собственное клиентское приложение "Параметры"
        -   Скопируйте значение Application ID, которое будет использоваться для последующих шагов установки.
        -   Выберите "необходимые разрешения".
            1.  Нажмите кнопку "Добавить".
            2.  Щелкните "выбрать API".
            3.  Найдите конечную точку печати и конечную точку обнаружения по имени, которое вы определили при создании конечной точки приложения.
            4.  Добавление двух конечных точек
            5.  Убедитесь, что параметр "делегированные разрешения" для каждой конечной точки приложения включен.
            6.  Убедитесь, что вы нащелкнули кнопку "Готово" в нижней части страницы
            7.  Щелкните "предоставить разрешения", когда будут добавлены обе конечные точки.  При появлении запроса на утверждение запроса выберите "Да".
        -   Перейдите в раздел "перенаправление URI" и добавьте следующие URI перенаправления в список: `ms-appx-web://Microsoft.AAD.BrokerPlugin/\<NativeClientAppID\>`
            `ms-appx-web://Microsoft.AAD.BrokerPlugin/S-1-15-2-3784861210-599250757-1266852909-3189164077-45880155-1246692841-283550366`

### <a name="step-3---install-azure-application-proxy-aap-with-passthrough-authentication"></a>Шаг 3. Установка прокси приложения Azure (схема AAP) с сквозной проверкой подлинности
1. Войдите на портал управления клиентами Azure AD (AAD).
    - В списке меню AAD выберите "прокси приложения".
    - Щелкните "включить прокси приложения" в верхней части экрана.
    - Скачайте "соединитель прокси приложения" на компьютер Windows Server, присоединенный к домену, который будет использоваться в качестве прокси веб-приложения (WAP).
2. На компьютере WAP Войдите как администратор и установите "соединитель прокси приложения".
    - Во время установки назначьте соединителю прокси приложения учетные данные для своего принципа Azure, на котором вы хотите включить схема AAP.
    - Убедитесь, что компьютер WAP присоединен к домену в локальной среде Active Directory
3. Вернитесь на портал управления клиентами AAD и добавьте прокси приложения.
   - Перейдите на вкладку " **корпоративные приложения** ".
   - Щелкните **создать приложение** .
   - Выберите **Локальное приложение** и заполните поля.
       - Имя: любое имя, которое вы хотите
       - Внутренний URL-адрес. это внутренний URL-адрес облачной службы обнаружения Mopria, к которой может получить доступ компьютер WAP.
       - Внешний URL-адрес: настройте соответствующим образом для вашей организации.
       - Метод предварительной проверки подлинности: passthrough

     >   Примечание. Если вы не нашли все приведенные выше параметры, добавьте прокси-сервер с доступными параметрами, а затем выберите только что созданный прокси **-сервер приложения** и добавьте все указанные выше сведения.

4. Повторите 3, выше, для облачной службы печати Enterprise и предоставьте внутренний URL-адрес облачной службе печати.

    >   Примечание. URL-адрес https://&lt;Services-Machine-Endpoint&gt;/МКС, упомянутый ниже, должен быть внешним URL-адресом, настроенным для облачной службы Mopria и (или) корпоративной облачной службы печати.


### <a name="step-4---configure-the-required-mdm-policies"></a>Шаг 4. Настройка необходимых политик MDM
- Вход в поставщик MDM
- Найдите группу политика печати корпоративного облака и настройте политики, следуя приведенным ниже рекомендациям.
  - Клаудпринтоаусаусорити = идентификатор каталога AD https://login.microsoftonline.com/\<Azure\>
  - Клаудпринтоаусклиентид = "идентификатор приложения" собственного веб-приложения, зарегистрированного на портале управления Azure AD.
  - Клаудпринтердисковерендпоинт = External URL-адрес прокси приложения Azure Discovery Service, созданного на шаге 3,3 (должен быть точно таким же, но без завершающего/)
  - Моприадисковериресаурцеид = идентификатор URI идентификатора приложения веб-приложения или API для конечной точки обнаружения, зарегистрированной на шаге 2,8.  Его можно найти в разделе Параметры — > свойства приложения.
  - Клаудпринтресаурцеид = идентификатор URI идентификатора приложения веб-приложения или API для конечной точки печати, зарегистрированной на шаге 2,8. Его можно найти в разделе Параметры — > свойства приложения.
  - Дисковеримакспринтерлимит = \<положительное целое число\>

>   Примечание. Если вы используете службу Microsoft Intune, эти параметры можно найти в категории "Облачный принтер".

|Отображаемое имя Intune                     |Политика                         |
|----------------------------------------|-------------------------------|
|URL-адрес обнаружения принтера                   |клаудпринтердисковерендпоинт  |
|URL-адрес центра доступа к принтерам            |клаудпринтоаусаусорити       |
|GUID собственного клиентского приложения Azure            |клаудпринтоаусклиентид        |
|URI ресурса службы печати              |клаудпринтресаурцеид           |
|Максимальное число принтеров для запроса (только для мобильных устройств)  |дисковеримакспринтерлимит       |
|URI ресурса службы обнаружения принтеров  |моприадисковериресаурцеид      |


>   Примечание. Если группа политик печати в облаке недоступна, но поставщик MDM поддерживает параметры OMA-URI, можно задать те же политики.  Дополнительные сведения см. в этой <a href="https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint#enterprisecloudprint-cloudprintoauthauthority">статье</a> .

- OMA-URI
    - `CloudPrintOAuthAuthority = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority`
        - Значение = `https://login.microsoftonline.com/`\<идентификатор каталога Azure AD\>
    - `CloudPrintOAuthClientId = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrintOAuthClientId`
        - Значение = \<идентификатор приложения собственного приложения Azure AD\>
    - `CloudPrinterDiscoveryEndPoint = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrinterDiscoveryEndPoint`
        - Значение = внешний URL-адрес прокси приложения службы обнаружения Mopria Azure, созданного на шаге 3,3 (должен быть точно таким же, но без замыкающего/)
    - `MopriaDiscoveryResourceId = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/MopriaDiscoveryResourceId`
        - Значение = идентификатор URI идентификатора приложения веб-приложения или API для конечной точки обнаружения, зарегистрированной на шаге 2,8.  Его можно найти в разделе Параметры — > свойства приложения.
    - `CloudPrintResourceId = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/CloudPrintResourceId`
        - Значение = идентификатор URI идентификатора приложения веб-приложения или API для конечной точки печати, зарегистрированной на шаге 2,8. Его можно найти в разделе Параметры — > свойства приложения.
    - `DiscoveryMaxPrinterLimit = ./Vendor/MSFT/Policy/Config/EnterpriseCloudPrint/DiscoveryMaxPrinterLimit`
        - Value = \<положительное целое число\>
  
### <a name="step-5---publish-desired-shared-printers"></a>Шаг 5. Публикация требуемых общих принтеров
1. Установка требуемого принтера на сервере печати
2. Предоставление общего доступа к принтеру через пользовательский интерфейс свойств принтера
3. Выберите требуемый набор пользователей для предоставления доступа
4. Сохраните изменения и закройте окно свойств принтера.
5. На компьютере с обновлением Windows 10 с правами создателя откройте командную строку Windows PowerShell с повышенными привилегиями.
   1. Выполните следующие команды.
      - `find-module -Name "PublishCloudPrinter"`, чтобы убедиться, что компьютер может достичь коллекция PowerShell (PSGallery).
      - `install-module -Name "PublishCloudPrinter"`

        >   Примечание. Вы можете увидеть обмен сообщениями о том, что "PSGallery" является недоверенным репозиторием.  Введите "y", чтобы продолжить установку.

      - Publish-Клаудпринтер
        - Printer = имя общего принтера, которое было определено
        - Manufacturer = изготовитель принтера
        - Model = модель принтера
        - Орглокатион = строка JSON, указывающая расположение принтера, например: `{"attrs": [{"category":"country", "vs":"USA", "depth":0}, {"category":"organization", "vs":"Microsoft", "depth":1}, {"category":"site", "vs":"Redmond, WA", "depth":2}, {"category":"building", "vs":"Building 1", "depth":3}, {"category":"floor\_number", "vn":1, "depth":4}, {"category":"room\_name", "vs":"1111", "depth":5}]}`
        - SDDL = строка SDDL, представляющая разрешения для принтера. Это можно получить, изменив соответствующим образом вкладку Безопасность свойства принтера, а затем выполнив в командной строке следующую команду: `(Get-Printer PrinterName -full).PermissionSDDL`
            Например, "Г:ДУД: (A; ОИЦИ; FA;;; WD) "

          > Примечание. необходимо добавить **`O:BA`** в качестве префикса в результат из команды командной строки выше, прежде чем задавать значение в качестве параметра SDDL.  Пример: SDDL = `O:BAG:DUD:(A;OICI;FA;;;WD)`

        - Дисковерендпоинт = https://&lt;Services-Machine-Endpoint&gt;/МКС
        - Принтсерверендпоинт = https://&lt;Services-Machine-Endpoint&gt;/ЕКП
        - Азуреклиентид = идентификатор приложения зарегистрированного собственного значения веб-приложения выше
        - Азуретенантгуид = идентификатор каталога вашего клиента Azure AD;
        - Дисковериресаурцеид = [необязательно] идентификатор приложения для облачной службы обнаружения Mopria в прокси-службе

        > Примечание. также можно ввести все необходимые значения параметров в командной строке.<br>
        **Publish-клаудпринтер** Синтаксис команд PowerShell: <br>
        Publish-Клаудпринтер-Printer \<строка\>-Manufacturer \<строка\>-Model \<строка\>-Орглокатион \<строка\>-SDDL \<String\>-Азуреклиентид \<строка\>-Азуретенантгуид \<строка\> [-DiscoveryResourceId \<String\>]\<\>\<\> <br>
        Пример команды: `publish-cloudprinter -Printer EcpPrintTest -Manufacturer Microsoft -Model FilePrinterEcp -OrgLocation '{"attrs": [{"category":"country", "vs":"USA", "depth":0}, {"category":"organization", "vs":"MyCompany", "depth":1}, {"category":"site", "vs":"MyCity, State", "depth":2}, {"category":"building", "vs":"Building 1", "depth":3}, {"category":"floor\_number", "vn":1, "depth":4}, {"category":"room\_name", "vs":"1111", "depth":5}]}' -Sddl "O:BAG:DUD:(A;OICI;FA;;;WD)" -DiscoveryEndpoint https://<services-machine-endpoint>/mcs -PrintServerEndpoint https://<services-machine-endpoint>/ecp -AzureClientId <Native Web App ID> -AzureTenantGuid <Azure AD Directory ID> -DiscoveryResourceId <Proxied Mopria Discovery Cloud Service App ID>`


## <a name="verifing-the-deployment"></a>Идет проверка узлами развертывание
На устройстве, присоединенном к Azure AD, для которого настроены политики MDM:
- Откройте веб-браузер и перейдите к https://&lt;Services-Machine-Endpoint&gt;/МКС/сервицес
- Вы должны увидеть текст JSON, описывающий набор функциональных возможностей этой конечной точки.
- Перейдите в раздел "Параметры ОС —\> устройства-\> принтеры & Сканеры".
    - Вы должны увидеть ссылку "Поиск по облачным принтерам"
    - Щелкните ссылку
    - Щелкните ссылку "выберите расположение для поиска".
        - Вы должны увидеть иерархию расположения устройств
    - Выберите расположение и нажмите кнопку " **ОК** ", а затем кнопку " **Поиск** ", чтобы найти принтеры.
    - Выберите принтер и нажмите кнопку " **Добавить устройство** "
    - После успешной установки принтера распечатайте его на принтере из избранного приложения.

>   Примечание. при использовании принтера "Екппринттест" выходной файл можно найти на компьютере сервера печати в папке "C:\\Екптестаутпут\\Екптестпринт. XPS".