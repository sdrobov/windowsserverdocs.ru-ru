---
title: Подключаемые модули сборки с моделью оценки рисков AD FS 2019
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.reviewer: ''
ms.date: 04/16/2019
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 1a4569b1fa3791d1d3b412b0801f216c975aa4dc
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70867613"
---
# <a name="build-plug-ins-with-ad-fs-2019-risk-assessment-model"></a>Подключаемые модули сборки с моделью оценки рисков AD FS 2019

Теперь вы можете создавать собственные подключаемые модули для блокировки или назначения оценки риска запросам проверки подлинности в течение различных этапов — полученных запросов, предварительной проверки подлинности и после проверки подлинности. Это можно сделать с помощью новой модели оценки рисков, представленной в AD FS 2019. 

## <a name="what-is-the-risk-assessment-model"></a>Что такое модель оценки рисков?

Модель оценки рисков — это набор интерфейсов и классов, которые позволяют разработчикам читать заголовки запросов проверки подлинности и реализовывать собственную логику оценки рисков. Затем реализованный код (подключаемый модуль) выполняется в строке с AD FS процессом проверки подлинности. Например, используя интерфейсы и классы, включенные в модель, можно реализовать код для блокировки или разрешения запроса на проверку подлинности на основе IP-адреса клиента, включенного в заголовок запроса. AD FS будет выполнять код для каждого запроса проверки подлинности и предпринимать соответствующие действия в соответствии с реализованной логикой. 

Модель позволяет выполнять код подключаемого модуля на любом из трех этапов AD FS конвейера проверки подлинности, как показано ниже.

![модель](media/ad-fs-risk-assessment-model/risk1.png)

1.  **Стадия получения запроса** — позволяет создавать подключаемые модули, разрешающие или блокирующие запрос, когда AD FS получает запрос на проверку подлинности, т. е. до ввода учетных данных пользователем. Вы можете использовать контекст запроса (например, клиентский IP-адрес, метод HTTP, DNS-сервер и т. д.), доступный на этом этапе, для выполнения оценки рисков. Например, можно создать подключаемый модуль для считывания IP-адреса из контекста запроса и блокировать запрос проверки подлинности, если IP-адрес находится в предварительно определенном списке рискованных адресов. 

2.  **Этап предварительной проверки подлинности** — позволяет создавать подключаемые модули, разрешающие или блокирующие запрос в точке, где пользователь предоставляет учетные данные, но до того, как AD FS их оценивает. На этом этапе помимо контекста запроса у вас также есть сведения о контексте безопасности (например, маркер пользователя, идентификатор пользователя и т. д.) и контекст протокола (например, протокол проверки подлинности, ClientID, ResourceId и т. д.) для использования в логике оценки рисков. Например, можно создать подключаемый модуль, чтобы предотвратить атаки на распыление паролей, читая пароль пользователя из маркера пользователя и блокируя запрос проверки подлинности, если пароль находится в предварительно определенном списке рискованных паролей. 

3.  **После проверки подлинности** — включает создание подключаемого модуля для оценки риска после того, как пользователь предоставил учетные данные, а AD FS выполняет проверку подлинности. На этом этапе помимо контекста запроса, контекста безопасности и контекста протокола также имеются сведения о результатах проверки подлинности (успех или сбой). Подключаемый модуль может оценить показатель риска на основе доступных данных и передать оценку риска в правила утверждения и политики для дальнейшего ознакомления. 

Чтобы лучше понять, как создать подключаемый модуль оценки рисков и запустить его в соответствии с AD FS процессом, создадим пример подключаемого модуля, который блокирует запросы, поступающие от определенных IP-адресов **экстрасети** , зарегистрируйте подключаемый модуль с AD FS и, наконец, протестируйте функциональность. 

>[!NOTE]
>В этом пошаговом руководстве показано, как можно создать пример подключаемого модуля. Не означает, что мы создаем решение, готовое для предприятия.  

## <a name="building-a-sample-plug-in"></a>Создание примера подключаемого модуля

### <a name="pre-requisites"></a>Предварительные требования
Ниже приведен список предварительных требований, необходимых для создания этого примера подключаемого модуля.

- AD FS 2019 установлен и настроен
- .NET Framework 4,7 и выше
- Visual Studio

### <a name="build-plug-in-dll"></a>Библиотека DLL подключаемого модуля сборки
Приведенная ниже процедура поможет вам создать пример библиотеки DLL подключаемого модуля.

1. Скачайте пример подключаемого модуля, используйте Git Bash и введите следующее: 

   ```
   git clone https://github.com/Microsoft/adfs-sample-RiskAssessmentModel-RiskyIPBlock
   ```

2. Создайте **CSV** -файл в любом месте на AD FS сервере (в моем случае я создал файл **аусконфигдб. csv** по адресу **к:\екстенсионс**) и добавит в него IP-адреса, которые нужно заблокировать. 

   Пример подключаемого модуля блокирует все запросы проверки подлинности, поступающие из **IP-адресов экстрасети** , перечисленных в этом файле. 

   >{! Примечание.] при наличии фермы AD FS можно создать файл на любом или на всех серверах AD FS. Любой из файлов можно использовать для импорта рискованных IP-адресов в AD FS. Процесс импорта подробно описан в разделе [Регистрация библиотеки DLL подключаемого модуля с помощью AD FS](#register-the-plug-in-dll-with-ad-fs) ниже. 

3. Открытие проекта `ThreatDetectionModule.sln` с помощью Visual Studio

4. Удалите `Microsoft.IdentityServer.dll` из обозревателя решений, как показано ниже.</br>
   ](media/ad-fs-risk-assessment-model/risk2.png) модели ![

5. Добавьте ссылку на `Microsoft.IdentityServer.dll` AD FS, как показано ниже.

   а)   Щелкните правой кнопкой мыши **ссылку** в **обозревателе решений** и выберите команду **Добавить ссылку...**</br>модель ![ 
   ](media/ad-fs-risk-assessment-model/risk3.png)
   
   б.   В окне **Диспетчер ссылок** выберите **Обзор**. В списке **выберите файлы для ссылки...** Выберите `Microsoft.IdentityServer.dll` из папки установки AD FS (в моем случае **к:\виндовс\адфс**) и нажмите кнопку **Добавить**.
   
   >[!NOTE]
   >В моем случае я создам подключаемый модуль на самом сервере AD FS. Если среда разработки находится на другом сервере, скопируйте `Microsoft.IdentityServer.dll` из папки установки AD FS на AD FS сервере в поле разработки.</br> 
   
   ![модель](media/ad-fs-risk-assessment-model/risk4.png)
   
   в.   Нажмите кнопку **ОК** в окне " **Диспетчер ссылок** ", убедившись, что установлен флажок `Microsoft.IdentityServer.dll`</br>
   ](media/ad-fs-risk-assessment-model/risk5.png) модели ![
 
6. Все классы и ссылки теперь используются для создания сборки.   Однако, поскольку выходные данные этого проекта являются библиотекой DLL, ее необходимо установить в **глобальный кэш сборок**или глобальном кэше сборок (GAC) сервера AD FS, а библиотека DLL должна быть подписана первой. Это можно сделать следующим образом.

   а)   Щелкните **правой кнопкой мыши** имя проекта среатдетектионмодуле. В меню выберите пункт **Свойства**.</br>
   ](media/ad-fs-risk-assessment-model/risk6.png) модели ![
   
   б.   На странице **Свойства** щелкните **подпись**слева и установите флажок **подписать сборку**. В раскрывающемся меню **выберите файл ключа строгого имени**: выберите **< создать... >**</br>
   ](media/ad-fs-risk-assessment-model/risk7.png) модели ![

   в.   В **диалоговом окне Создание ключа строгого имени**введите имя для ключа (можно выбрать любое имя), снимите флажок **защитить файл ключа паролем**. Затем нажмите кнопку **ОК**.
   ](media/ad-fs-risk-assessment-model/risk8.png) модели ![</br>
 
   г)   Сохраните проект, как показано ниже.</br>
   ](media/ad-fs-risk-assessment-model/risk9.png) модели ![

7. Выполните сборку проекта, щелкнув **Сборка** , а затем **Перестроить решение** , как показано ниже.</br>
   ](media/ad-fs-risk-assessment-model/risk10.png) модели ![
 
   Проверьте **окно вывода**в нижней части экрана, чтобы узнать, произошли ли ошибки.</br>
   ](media/ad-fs-risk-assessment-model/risk11.png) модели ![


Теперь подключаемый модуль (DLL) готов к использованию и находится в папке **\bin\Debug** папки проекта (в моем случае это **к:\екстенсионс\среатдетектионмодуле\бин\дебуг\среатдетектионмодуле.длл**). 

Следующий шаг — зарегистрировать эту библиотеку DLL с AD FS, чтобы она выполнялась в AD FS процессе проверки подлинности. 

### <a name="register-the-plug-in-dll-with-ad-fs"></a>Зарегистрируйте библиотеку DLL подключаемого модуля с помощью AD FS

Необходимо зарегистрировать библиотеку DLL в AD FS с помощью команды `Register-AdfsThreatDetectionModule` PowerShell на AD FS сервере, однако перед регистрацией необходимо получить маркер открытого ключа. Этот маркер открытого ключа был создан при создании ключа и подписании библиотеки DLL с помощью этого ключа. Чтобы узнать, что такое маркер открытого ключа для библиотеки DLL, можно использовать **файл Sn. exe** , как показано ниже.

1. Скопируйте DLL-файл из папки **\bin\Debug** в другое место (в моем случае, скопировав его в **к:\екстенсионс**).

2. Запустите **Командная строка разработчика** для Visual Studio и перейдите в каталог, содержащий файл **Sn. exe** (в моем случае каталог — **C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.7.2 tools**) ![Model](media/ad-fs-risk-assessment-model/risk12.png)

3. Выполните команду **SN** с параметром **-T** и расположением файла (в моем случае `SN -T “C:\extensions\ThreatDetectionModule.dll”`) ![модели](media/ad-fs-risk-assessment-model/risk13.png)</br>
   Команда предоставит маркер открытого ключа (для меня **маркером открытого ключа является 714697626ef96b35**)

4. Добавьте библиотеку DLL в **глобальный кэш сборок** AD FS Server. Мы рекомендуем создать правильный установщик для проекта и добавить этот файл в GAC с помощью установщика. Другое решение — использовать **gacutil. exe** (Дополнительные сведения о **gacutil. exe** доступны [здесь](https://docs.microsoft.com/dotnet/framework/tools/gacutil-exe-gac-tool)) на компьютере разработчика.  Так как я использую Visual Studio на том же сервере, что и AD FS, я буду использовать **gacutil. exe** следующим образом.

   а)   В Командная строка разработчика для Visual Studio и перейдите в каталог, содержащий **gacutil. exe** (в моем случае каталог **C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.7.2 Tools**)

   б.   Выполните команду **gacutil** (в моем случае `Gacutil /IF C:\extensions\ThreatDetectionModule.dll`) ![модель](media/ad-fs-risk-assessment-model/risk14.png)
 
   >[!NOTE]
   >Если у вас есть ферма AD FS, необходимо выполнить описанные выше шаги на каждом сервере AD FS в ферме. 

5. Откройте **Windows PowerShell** и выполните следующую команду, чтобы зарегистрировать библиотеку DLL.
   ```
   Register-AdfsThreatDetectionModule -Name "<Add a name>" -TypeName "<class name that implements interface>, <dll name>, Version=10.0.0.0, Culture=neutral, PublicKeyToken=< Add the Public Key Token from Step 2. above>" -ConfigurationFilePath "<path of the .csv file>”
   ```
   В моем случае команда: 
   ```
   Register-AdfsThreatDetectionModule -Name "IPBlockPlugin" -TypeName "ThreatDetectionModule.UserRiskAnalyzer, ThreatDetectionModule, Version=10.0.0.0, Culture=neutral, PublicKeyToken=714697626ef96b35" -ConfigurationFilePath "C:\extensions\authconfigdb.csv”
   ```
 
   >[!NOTE]
   >Необходимо зарегистрировать библиотеку DLL только один раз, даже если у вас AD FS ферма. 

6. Перезапуск службы AD FS после регистрации библиотеки DLL

Итак, Библиотека DLL зарегистрирована в AD FS и готова к использованию!

 >[!NOTE]
 > Если в подключаемый модуль вносятся какие-либо изменения и проект перестраивается, то обновленная библиотека DLL должна быть повторно зарегистрирована. Перед регистрацией необходимо отменить регистрацию текущей библиотеки DLL с помощью следующей команды:</br></br>
 >`
  UnRegister-AdfsThreatDetectionModule -Name "<name used while registering the dll in 5. above>"
 >`</br></br> В моем случае команда:
 >``` 
 >UnRegister-AdfsThreatDetectionModule -Name "IPBlockPlugin"
 >```

### <a name="testing-the-plug-in"></a>Тестирование подключаемого модуля

1. Откройте файл **аусконфиг. csv** , созданный ранее (в моем случае в расположении **к:\екстенсионс**), и добавьте **IP-адреса экстрасети** , которые нужно заблокировать. Каждый IP-адрес должен находиться в отдельной строке, и в конце не должно быть пробелов.</br>
   ](media/ad-fs-risk-assessment-model/risk18.png) модели ![
 
2. Сохраните и закройте файл.

3. Импортируйте обновленный файл в AD FS, выполнив следующую команду PowerShell: 

   ```
   Import-AdfsThreatDetectionModuleConfiguration -name "<name given while registering the dll>" -ConfigurationFilePath "<path of the .csv file>"
   ```
 
   В моем случае команда: 
   ```
   Import-AdfsThreatDetectionModuleConfiguration -name "IPBlockPlugin" -ConfigurationFilePath "C:\extensions\authconfigdb.csv")
   ```
 
4. Инициируйте запрос проверки подлинности с сервера с тем же IP-адресом, который вы добавили в **аусконфиг. csv**.

   Для этой демонстрации я буду использовать для инициации запроса [инструмент AD FS Help Claims X-Ray](https://adfshelp.microsoft.com/ClaimsXray/TokenRequest) . Если вы хотите использовать средство X-Ray, следуйте инструкциям. 

   Введите экземпляр сервера федерации и нажмите кнопку **Проверка подлинности** проверки нажатия.</br>модель ![ 
   ](media/ad-fs-risk-assessment-model/risk15.png) 

5. Проверка подлинности блокируется, как показано ниже.</br>
   ](media/ad-fs-risk-assessment-model/risk16.png) модели ![
 
Теперь, когда мы осведомлены о том, как создать и зарегистрировать подключаемый модуль, давайте пошаговым кодом подключаемого модуля, чтобы понять реализацию с помощью новых интерфейсов и классов, представленных в модели. 

## <a name="plug-in-code-walkthrough"></a>Пошаговое руководство по коду подключаемого модуля

Откройте проект `ThreatDetectionModule.sln` с помощью Visual Studio, а затем откройте основной файл **UserRiskAnalyzer.CS** в **обозревателе решений** в правой части экрана.</br>
](media/ad-fs-risk-assessment-model/risk17.png) модели ![
 
Файл содержит класс main Усеррисканализер, который реализует абстрактный класс [среатдетектионмодуле](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule?view=adfs-2019) и интерфейс [ирекуестрецеиведсреатдетектионмодуле](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule?view=adfs-2019) для считывания IP-адреса из контекста запроса, сравнения полученного IP-адреса с IP-адресами, загруженными из AD FS DB, и блокировки запроса при совпадении IP-адресов. Давайте рассмотрим эти типы более подробно.

### <a name="threatdetectionmodule-abstract-class"></a>Абстрактный класс Среатдетектионмодуле

Этот абстрактный класс загружает подключаемый модуль в конвейер AD FS, что позволяет запускать код подключаемого модуля в строке с AD FS процессом. 

```
public abstract class ThreatDetectionModule 
{ 
    protected ThreatDetectionModule(); 
 
    public abstract string VendorName { get; } 
    public abstract string ModuleIdentifier { get; } 
 
 public abstract void OnAuthenticationPipelineLoad(ThreatDetectionLogger logger, ThreatDetectionModuleConfiguration configData); 
 public abstract void OnAuthenticationPipelineUnload(ThreatDetectionLogger logger); 
  public abstract void OnConfigurationUpdate(ThreatDetectionLogger logger, ThreatDetectionModuleConfiguration configData); 
 }   
```
Класс включает следующие методы и свойства.

|Метод |Тип|Определение|
|-----|-----|-----| 
|[онаусентикатионпипелинелоад](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineload?view=adfs-2019) |Void|Вызывается с помощью AD FS при загрузке подключаемого модуля в конвейер| 
|[онаусентикатионпипелинеунлоад](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineunload?view=adfs-2019) |Void|Вызывается AD FS при выгрузке подключаемого модуля из конвейера| 
|[онконфигуратионупдате](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onconfigurationupdate?view=adfs-2019)| Void|Вызывается с помощью AD FS при обновлении конфигурации |
|**Свойства** |**Тип** |**Определение**|
|[ИмяПоставщика](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.vendorname?view=adfs-2019)|Строка |Возвращает имя поставщика, владеющего подключаемым модулем.|
|[модулеидентифиер](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.moduleidentifier?view=adfs-2019)|Строка |Возвращает идентификатор подключаемого модуля.|

В нашем примере подключаемого модуля мы используем методы [онаусентикатионпипелинелоад](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineload?view=adfs-2019) и [онконфигуратионупдате](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onconfigurationupdate?view=adfs-2019) для чтения предварительно определенных ip-адресов из AD FS DB. [Онаусентикатионпипелинелоад](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineload?view=adfs-2019) вызывается, когда подключаемый модуль регистрируется в AD FS во время вызова [онконфигуратионупдате](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onconfigurationupdate?view=adfs-2019) при импорте CSV-файла с помощью командлета `Import-AdfsThreatDetectionModuleConfiguration`. 

#### <a name="irequestreceivedthreatdetectionmodule-interface"></a>Интерфейс Ирекуестрецеиведсреатдетектионмодуле

Этот [интерфейс](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule?view=adfs-2019) позволяет реализовать оценку рисков в точке, где AD FS получает запрос на проверку подлинности, но до того, как пользователь введет учетные данные, т. е. на этапе получения запроса проверки подлинности. 
 
```
public interface IRequestReceivedThreatDetectionModule
{
Task<ThrottleStatus> EvaluateRequest (
ThreatDetectionLogger logger, 
RequestContext requestContext );
}
```

Интерфейс включает метод [евалуатерекуест](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule.evaluaterequest?view=adfs-2019) , который позволяет использовать контекст запроса проверки подлинности, переданный в входном параметре RequestContext, для записи логики оценки рисков. Параметр requestContext имеет тип [RequestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019). 

Переданный входной параметр — это средство ведения журнала, которое имеет тип [среатдетектионлогжер](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionlogger?view=adfs-2019). Параметр можно использовать для записи ошибок, аудита и/или отладки сообщений в AD FS журналов. 

Метод возвращает [сроттлестатус](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.throttlestatus?view=adfs-2019) (0, если нотевалуатед, 1 to Block и 2 для разрешения), чтобы AD FS, который затем либо блокирует, либо разрешает запрос.

В нашем примере подключаемого модуля реализация метода [евалуатерекуест](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule.evaluaterequest?view=adfs-2019) анализирует [ClientIpAddress](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext.clientipaddresses?view=adfs-2019#Microsoft_IdentityServer_Public_ThreatDetectionFramework_RequestContext_ClientIpAddresses) из параметра [RequestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019) и сравнивает его со всеми IP-адресами, загруженными из AD FS DB. Если совпадение найдено, метод возвращает 2 для **Block**, в противном случае возвращает 1 для **allow**. В зависимости от возвращаемого значения AD FS либо блокирует, либо разрешает запрос. 

>[!NOTE]
>Пример подключаемого модуля, описанный выше, реализует только интерфейс Ирекуестрецеиведсреатдетектионмодуле. Однако модель оценки рисков предоставляет два дополнительных интерфейса — Ипреаусентикатионсреатдетектионмодуле (для реализации логики оценки рисков процессе до этапа предварительной проверки подлинности) и Ипостаусентикатионсреатдетектионмодуле (для реализации риска Логика оценки на этапе последующей проверки подлинности). Ниже приведены подробные сведения о двух интерфейсах. 

#### <a name="ipreauthenticationthreatdetectionmodule-interface"></a>Интерфейс Ипреаусентикатионсреатдетектионмодуле 

Этот [интерфейс](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipreauthenticationthreatdetectionmodule?view=adfs-2019) позволяет реализовать логику оценки рисков в том месте, где пользователь предоставляет учетные данные, но до того, как AD FS оценивает их, т. е. этап предварительной проверки подлинности. 

```
public interface IPreAuthenticationThreatDetectionModule
{
Task<ThrottleStatus> EvaluatePreAuthentication (
ThreatDetectionLogger logger, 
RequestContext requestContext, 
SecurityContext securityContext, 
ProtocolContext protocolContext, 
IList<Claim> additionalClams
);
}
```
Интерфейс включает метод [евалуатепреаусентикатион](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipreauthenticationthreatdetectionmodule.evaluatepreauthentication?view=adfs-2019) , который позволяет использовать сведения, передаваемые в входных параметрах [RequestContext RequestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019), [SecurityContext SecurityContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext?view=adfs-2019), [протоколконтекст протоколконтекст](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext?view=adfs-2019)и [IList<Claim> аддитионалкламс](https://docs.microsoft.com/dotnet/api/system.collections.generic.ilist-1?view=netframework-4.7.2) , для написания логики оценки риска перед проверкой подлинности. 

>[!NOTE]
>Список свойств, переданных с каждым типом контекста, см. в определениях классов [RequestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019), [SecurityContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext?view=adfs-2019)и [протоколконтекст](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext?view=adfs-2019) . 

Переданный входной параметр — это средство ведения журнала, которое имеет тип [среатдетектионлогжер](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionlogger?view=adfs-2019). Параметр можно использовать для записи ошибок, аудита и/или отладки сообщений в AD FS журналов.

Метод возвращает [сроттлестатус](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.throttlestatus?view=adfs-2019) (0, если нотевалуатед, 1 to Block и 2 для разрешения), чтобы AD FS, который затем либо блокирует, либо разрешает запрос. 

#### <a name="ipostauthenticationthreatdetectionmodule-interface"></a>Интерфейс Ипостаусентикатионсреатдетектионмодуле

Этот [интерфейс](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipostauthenticationthreatdetectionmodule?view=adfs-2019) позволяет реализовать логику оценки рисков после того, как пользователь предоставил учетные данные, а AD FS выполнил проверку подлинности, т. е. этап последующей проверки подлинности. 

```
public interface IPostAuthenticationThreatDetectionModule
{
Task<RiskScore> EvaluatePostAuthentication (
ThreatDetectionLogger logger, 
RequestContext requestContext, 
SecurityContext securityContext, 
ProtocolContext protocolContext, 
AuthenticationResult authenticationResult, 
IList<Claim> additionalClams
);
}
```

Интерфейс включает метод [евалуатепостаусентикатион](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipostauthenticationthreatdetectionmodule.evaluatepostauthentication?view=adfs-2019) , который позволяет использовать сведения, передаваемые в входных параметрах [RequestContext RequestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019), [SecurityContext SecurityContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext?view=adfs-2019), [протоколконтекст протоколконтекст](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext?view=adfs-2019)и [IList<Claim> аддитионалкламс](https://docs.microsoft.com/dotnet/api/system.collections.generic.ilist-1?view=netframework-4.7.2) , для написания логики оценки риска после проверки подлинности. 

>[!NOTE]
> Полный список свойств, передаваемых с каждым типом контекста, см. в разделе определения классов [RequestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019), [SecurityContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext?view=adfs-2019)и [протоколконтекст](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext?view=adfs-2019) . 

Переданный входной параметр — это средство ведения журнала, которое имеет тип [среатдетектионлогжер](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionlogger?view=adfs-2019). Параметр можно использовать для записи ошибок, аудита и/или отладки сообщений в AD FS журналов. 

Метод возвращает [оценку риска](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.authentication.riskscoreconstants?view=adfs-2019) , которую можно использовать в правилах политики AD FS и утверждений. 

>[!NOTE]
>Для работы подключаемого модуля в основном классе (в данном случае Усеррисканализер) должен быть производный абстрактный класс [среатдетектионмодуле](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule?view=adfs-2019) , который должен реализовывать по крайней мере один из трех описанных выше интерфейсов. После регистрации библиотеки DLL AD FS проверяет, какие интерфейсы реализуются и вызывают их на соответствующем этапе в конвейере.

### <a name="faqs"></a>Вопросы и ответы

**Зачем создавать эти подключаемые модули?**</br>
Ответ **.** Эти подключаемые модули не только предоставляют дополнительную возможность защитить среду от атак, таких как атаки типа «распыление паролей», но также предоставляют гибкие возможности создания собственной логики оценки рисков на основе ваших требований. 

**Где записываются журналы?**</br>
Ответ **.** Вы можете записывать журналы ошибок в журнал событий "AD FS/Admin" с помощью метода Вритеадминложеррормессаже, вести журналы аудита в журнал безопасности AD FS аудита с помощью метода Вритеаудитмессаже и журналов отладки в журнал отладки "AD FS трассировки с помощью метода Вритедебугмессаже. 

**Можно ли добавить эти подключаемые модули увеличить задержку процесса проверки подлинности AD FS?**</br>
Ответ **.** Влияние на задержку будет определяться временем, затраченным на выполнение реализуемой логики оценки рисков. Рекомендуется оценить влияние задержки перед развертыванием подключаемого модуля в рабочей среде. 

**Почему не может AD FS предложить список рискованных IP-адресов, пользователей и т. д.**</br>
Ответ **.** В настоящее время мы работаем над созданием аналитической аналитики для предложения рискованных IP-адресов, пользователей и т. д. в модели оценки подключаемых рисков. Вскоре мы будем предоставлять вам даты запуска. 
