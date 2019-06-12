---
title: Создавать подключаемые модули с моделью 2019 оценки риска AD FS
description: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.reviewer: ''
ms.date: 04/16/2019
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: e43f505a02ec2241a84f74ff57e217c2fb95157b
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66445354"
---
# <a name="build-plug-ins-with-ad-fs-2019-risk-assessment-model"></a>Создавать подключаемые модули с моделью 2019 оценки риска AD FS

Теперь можно создавать собственные подключаемые модули для блокирования или назначить оценки риска запросы проверки подлинности во время различных этапов — запрос, полученных, предварительная проверка подлинности и последующей проверки подлинности. Это можно сделать с помощью новую модель оценки риска, представленную службами AD FS 2019. 

## <a name="what-is-the-risk-assessment-model"></a>Что такое модель оценки риска?

Модель оценки риска — это набор интерфейсы и классы, которые позволяют разработчикам выполнять чтение заголовков запроса проверки подлинности и реализовывать собственную логику оценки риска. Реализованный код (подключаемый модуль) выполняется в соответствии с процессом проверки подлинности AD FS. Например, используя интерфейсы и классы, включенные в модель, можно реализовать код, либо блок или разрешить запрос проверки подлинности в зависимости от IP-адрес клиента, включенные в заголовке запроса. AD FS будет выполнять код для каждого запроса проверки подлинности и предпринять соответствующие действия согласно логике. 

Модель позволяет подключаемого кода на любом из трех этапов конвейера проверки подлинности AD FS, как показано ниже

![модель](media/ad-fs-risk-assessment-model/risk1.png)

1.  **Запрос получен этап** — позволяет создавать подключаемые модули, чтобы разрешить или заблокировать запрос, если службы федерации Active Directory получает запрос на проверку подлинности т. е. Прежде чем пользователь вводит учетные данные. Можно использовать контекст запроса (например, IP-адрес клиента, метод Http, прокси-сервер DNS, т. д.) доступны на этом этапе, чтобы выполнить оценку рисков. Например, можно построения подключаемый модуль для чтения IP-адрес из контекста запроса и блокирует запрос на проверку подлинности, если IP-адрес находится в списке предварительно определенных опасных IP-адресов. 

2.  **Этап предварительной проверки подлинности** — позволяет создавать подключаемые модули, для разрешения или запрета запроса в точке, там, где пользователь предоставляет учетные данные, но прежде чем AD FS оценивает их. На этом этапе в дополнение к контекст запроса вы получаете сведения о безопасности (например, токен пользователя, идентификатор пользователя, и т.д.) и протокола контекста (например, протокол проверки подлинности, clientid, resourceid, и т.д.) для использования в логике оценки риска. Например, можно построения подключаемый модуль для предотвращения атак Распылитель пароль путем чтения пароля пользователя из маркера пользователя и блокирует запрос на проверку подлинности, если пароль указан в списке предварительно определенных рискованные паролей. 

3.  **После проверки подлинности** — позволяет создавать подключаемые модули, оценки рисков, после того как пользователь предоставил учетные данные и AD FS прошел проверку подлинности. На этом этапе, помимо контекст запроса, контекст безопасности и протокола контекста вы можете сведения на результат проверки подлинности (успех или сбой). Подключаемый модуль для вычисления оценки рисков на основе доступных данных и передачи оценку риска для утверждения и правила политики для дальнейшей оценки. 

Чтобы лучше понять, как создать подключаемый модуль оценки рисков и запустите его в соответствии с AD FS процесса, давайте создадим образец подключаемого модуля, блокирует запросы, поступающие от определенных **экстрасети** IP-адресов считается опасно, регистрация подключаемого модуля с AD FS и наконец, протестируйте функциональные возможности. 

>[!NOTE]
>Это пошаговое руководство предназначено только для того, чтобы показать, как можно создать образец подключаемого модуля. Отнюдь не является решением, мы создаем корпоративное решение Готово.  

## <a name="building-a-sample-plug-in"></a>Построение примера плагина

### <a name="pre-requisites"></a>Предварительные требования
Ниже приведен список предварительных требований, необходимых для построения этого образца подключаемого модуля

- AD FS 2019 г. установлен и настроен
- .NET framework 4.7 и более поздних версий
- Visual Studio

### <a name="build-plug-in-dll"></a>Создать библиотеку dll подключаемого модуля
Следующая процедура поможет выполнить построение образца библиотеки dll подключаемого модуля.

1. Загрузите образец подключаемого модуля, используйте Git Bash и введите следующую команду: 

   ```
   git clone https://github.com/Microsoft/adfs-sample-RiskAssessmentModel-RiskyIPBlock
   ```

2. Создание **.csv** файл в любом расположении на сервере AD FS (в моем случае я создал **authconfigdb.csv** файл **C:\extensions**) и добавьте IP-адреса, чтобы заблокировать в этот файл. 

   Образец подключаемого модуля заблокирует любые запросы проверки подлинности, поступающих от **экстрасети IP-адреса** перечисленные в этом файле. 

   >{! Примечание] Если у вас есть фермы AD FS, можно создать файл на любой или все серверы AD FS. Любой из файлов можно использовать для импорта опасных IP-адресов в AD FS. Мы обсудим процесс импорта подробно [зарегистрировать библиотеку dll подключаемого модуля с AD FS](#register-the-plug-in-dll-with-ad-fs) разделе ниже. 

3. Откройте проект `ThreatDetectionModule.sln` с помощью Visual Studio

4. Удалить `Microsoft.IdentityServer.dll` из обозревателя решений, как показано ниже:</br>
   ![Модель](media/ad-fs-risk-assessment-model/risk2.png)

5. Добавьте ссылку на `Microsoft.IdentityServer.dll` AD FS, как показано ниже

   1.   Щелкните правой кнопкой мыши **ссылки** в **обозревателя решений** и выберите **добавить ссылку...**</br> 
   ![Модель](media/ad-fs-risk-assessment-model/risk3.png)
   
   2.   На **диспетчер ссылок** выберите окно **Обзор**. В **выберите файлы, которые нужно установить ссылки...** диалоговое окно, выберите `Microsoft.IdentityServer.dll` из папки установки AD FS (в моем случае **C:\Windows\ADFS**) и нажмите кнопку **добавить**.
   
   >[!NOTE]
   >В моем случае я создаю подключаемый модуль на самом сервере AD FS. Если среды разработки на другом сервере, скопируйте `Microsoft.IdentityServer.dll` из папки установки AD FS на сервере AD FS в среде разработки.</br> 
   
   ![модель](media/ad-fs-risk-assessment-model/risk4.png)
   
   В.   Нажмите кнопку **ОК** на **диспетчер ссылок** окна, убедившись в том `Microsoft.IdentityServer.dll` флажок</br>
   ![Модель](media/ad-fs-risk-assessment-model/risk5.png)
 
6. Все классы и ссылки стали на месте, к сборке.   Тем не менее, так как выходные данные этого проекта представляет собой библиотеку dll, он должен устанавливаться в **глобальный кэш сборок**, или в глобальном кэше СБОРОК, сервера AD FS и библиотеки dll должны быть подписаны сначала. Это можно сделать следующим образом:

   1.   **Щелкните правой кнопкой мыши** на имя проекта, ThreatDetectionModule. В меню **свойства**.</br>
   ![Модель](media/ad-fs-risk-assessment-model/risk6.png)
   
   2.   Из **свойства** щелкните **подписывание**, слева и проверьте флажок помечен **подписать сборку**. Из **выберите файл ключа строгого имени**: выпадающем меню выберите **< создать... >**</br>
   ![Модель](media/ad-fs-risk-assessment-model/risk7.png)

   В.   В **диалоговой Создание ключа строгого имени**, введите имя (можно выбрать любое имя) для ключа, снимите этот флажок, **защитить мой файл ключей паролем**. Затем нажмите кнопку **ОК**.
   ![Модель](media/ad-fs-risk-assessment-model/risk8.png)</br>
 
   Г.   Сохраните проект, как показано ниже</br>
   ![Модель](media/ad-fs-risk-assessment-model/risk9.png)

7. Постройте проект, нажав кнопку **построения** и затем **Перестроить решение** как показано ниже</br>
   ![Модель](media/ad-fs-risk-assessment-model/risk10.png)
 
   Проверьте **окно вывода**, в нижней части экрана, чтобы увидеть, если ошибок</br>
   ![Модель](media/ad-fs-risk-assessment-model/risk11.png)


Теперь готов для использования подключаемого модуля (dll) и в **\bin\Debug** папке проекта (в данном случае это **C:\extensions\ThreatDetectionModule\bin\Debug\ThreatDetectionModule.dll**). 

Следующим шагом является регистрация эту библиотеку dll с AD FS, так чтобы он работал в соответствии с процессом проверки подлинности AD FS. 

### <a name="register-the-plug-in-dll-with-ad-fs"></a>Зарегистрировать библиотеку dll подключаемого модуля с AD FS

Нам нужно зарегистрировать библиотеку dll в AD FS с помощью `Register-AdfsThreatDetectionModule` команду PowerShell на сервере AD FS, тем не менее, прежде чем мы регистрируем, нам нужно получить токена открытого ключа. Был создан этот токен открытого ключа, когда мы создали ключ и подписываются с помощью этого ключа. Чтобы узнать о возможностях токена открытого ключа для библиотеки dll, можно использовать **SN.exe** следующим образом

1. Скопируйте DLL-файл из **\bin\Debug** папку в другое место (в моем случае, скопировать его **C:\extensions**)

2. Запуск **Командная строка разработчика** для Visual Studio и перейдите к каталогу, содержащему **sn.exe** (в моем случае является каталог **C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A средства \bin\NETFX 4.7.2**) ![модели](media/ad-fs-risk-assessment-model/risk12.png)

3. Запустите **SN** с **-T** параметра и расположение файла (в моем случае `SN -T “C:\extensions\ThreatDetectionModule.dll”`) ![модели](media/ad-fs-risk-assessment-model/risk13.png)</br>
   Команда предоставит вам маркер открытого ключа (для меня, **токена открытого ключа — 714697626ef96b35**)

4. Добавьте библиотеку dll для **глобальный кэш сборок** сервера AD FS наших лучше создать установщик, подходящий для проекта и добавьте его в глобальный кэш сборок с помощью установщика. Другим решением является использование **Gacutil.exe** (Дополнительные сведения о **Gacutil.exe** доступных [здесь](https://docs.microsoft.com/dotnet/framework/tools/gacutil-exe-gac-tool)) на компьютере разработки.  Поскольку у меня есть visual studio на одном сервере с AD FS, я буду использовать **Gacutil.exe** следующим образом

   1.   На Командная строка разработчика для Visual Studio и перейдите к каталогу, содержащему **Gacutil.exe** (в моем случае является каталог **C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.7.2 Tools**)

   2.   Запустите **Gacutil** команды (в моем случае `Gacutil /IF C:\extensions\ThreatDetectionModule.dll`) ![модели](media/ad-fs-risk-assessment-model/risk14.png)
 
   >[!NOTE]
   >Если ферма AD FS, указанных выше должен выполняться на каждом сервере AD FS в ферме. 

5. Откройте **Windows PowerShell** и выполните следующую команду, чтобы зарегистрировать библиотеку dll
   ```
   Register-AdfsThreatDetectionModule -Name "<Add a name>" -TypeName "<class name that implements interface>, <dll name>, Version=10.0.0.0, Culture=neutral, PublicKeyToken=< Add the Public Key Token from Step 2. above>" -ConfigurationFilePath "<path of the .csv file>”
   ```
   В моем случае команда выглядит так: 
   ```
   Register-AdfsThreatDetectionModule -Name "IPBlockPlugin" -TypeName "ThreatDetectionModule.UserRiskAnalyzer, ThreatDetectionModule, Version=10.0.0.0, Culture=neutral, PublicKeyToken=714697626ef96b35" -ConfigurationFilePath "C:\extensions\authconfigdb.csv”
   ```
 
   >[!NOTE]
   >Необходимо зарегистрировать библиотеку dll только один раз, даже если ферма AD FS. 

6. Перезапустите службу AD FS после регистрации библиотеки dll

Таким образом, библиотека dll зарегистрирован с AD FS и готов к использованию!

 >[!NOTE]
 > Если любые изменения, внесенные в подключаемый модуль, проект перестраивается обновленной библиотеки dll необходимо зарегистрировать повторно. Перед регистрацией, необходимо отменить регистрацию текущей dll, используя следующую команду:</br></br>
 >`
  UnRegister-AdfsThreatDetectionModule -Name "<name used while registering the dll in 5. above>"
 >`</br></br> В моем случае команда выглядит так:
 >``` 
 >UnRegister-AdfsThreatDetectionModule -Name "IPBlockPlugin"
 >```

### <a name="testing-the-plug-in"></a>Проверка подключаемого модуля

1. Откройте **authconfig.csv** файл, созданный ранее (в моем случае в расположении **C:\extensions**) и добавьте **экстрасети IP-адреса** нужно заблокировать. Каждый IP-адрес должен находиться в отдельной строке и не должно быть пробелов в конце</br>
   ![Модель](media/ad-fs-risk-assessment-model/risk18.png)
 
2. Сохраните и закройте файл

3. Импортируйте обновленный файл в AD FS, выполнив следующую команду PowerShell 

   ```
   Import-AdfsThreatDetectionModuleConfiguration -name "<name given while registering the dll>" -ConfigurationFilePath "<path of the .csv file>"
   ```
 
   В моем случае команда выглядит так: 
   ```
   Import-AdfsThreatDetectionModuleConfiguration -name "IPBlockPlugin" -ConfigurationFilePath "C:\extensions\authconfigdb.csv")
   ```
 
4. Запрос на проверку подлинности от сервера с тем же IP-адресом, добавленного при изучении **authconfig.csv**.

   Для этой демонстрации я буду использовать [средство рентгеновские помочь утверждений AD FS](https://adfshelp.microsoft.com/ClaimsXray/TokenRequest) инициации запроса. Если вы хотите использовать средство рентгеновский снимок, см. инструкции 

   Экземпляр сервера федерации, нажмите **тестирование проверки подлинности** кнопки.</br> 
   ![Модель](media/ad-fs-risk-assessment-model/risk15.png) 

5. Проверка подлинности блокируется, как показано ниже.</br>
   ![Модель](media/ad-fs-risk-assessment-model/risk16.png)
 
Теперь, когда мы знаем, как создать и зарегистрировать подключаемый модуль, давайте пошаговом руководстве код подключаемого модуля для понимания реализации с помощью новых интерфейсов и классов появилась в модели. 

## <a name="plug-in-code-walkthrough"></a>Подключаемый модуль код пошагового руководства

Откройте проект `ThreatDetectionModule.sln` с помощью Visual Studio, а затем откройте главный файл **UserRiskAnalyzer.cs** из **обозревателя решений** в правой части экрана</br>
![Модель](media/ad-fs-risk-assessment-model/risk17.png)
 
Файл содержит основной класс UserRiskAnalyzer, который реализует абстрактный класс [ThreatDetectionModule](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule?view=adfs-2019) и интерфейс [IRequestReceivedThreatDetectionModule](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule?view=adfs-2019) для чтения IP-адрес из запроса контекст, сравнить полученный IP-адрес с IP-адресов, загруженных из базы данных AD FS и блокирует запрос, если имеется совпадение IP-адрес. Давайте подробнее рассмотрим эти типы подробно

### <a name="threatdetectionmodule-abstract-class"></a>Абстрактный класс ThreatDetectionModule

Этот абстрактный класс загружает подключаемый модуль в AD FS конвейера, что позволяет выполнить код подключаемого модуля в соответствии с AD FS процесса. 

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
Этот класс включает следующие методы и свойства.

|Метод |Тип|Определение|
|-----|-----|-----| 
|[OnAuthenticationPipelineLoad](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineload?view=adfs-2019) |void|Вызывается службами AD FS, при загрузке подключаемого модуля в его конвейер| 
|[OnAuthenticationPipelineUnload](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineunload?view=adfs-2019) |void|Вызывается средой AD FS, когда подключаемый модуль выгружается из своего конвейера| 
|[OnConfigurationUpdate](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onconfigurationupdate?view=adfs-2019)| void|Вызывается службами AD FS на обновление конфигурации |
|**Свойство** |**Тип** |**Определение**|
|[ИмяПоставщика](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.vendorname?view=adfs-2019)|Строка |Получает имя поставщика, которой принадлежит подключаемого модуля|
|[ModuleIdentifier](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.moduleidentifier?view=adfs-2019)|Строка |Получает идентификатор подключаемого модуля|

В наш пример подключаемого модуля, мы используем [OnAuthenticationPipelineLoad](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineload?view=adfs-2019) и [OnConfigurationUpdate](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onconfigurationupdate?view=adfs-2019) методы для чтения предварительно определенных IP-адреса из базы данных AD FS. [OnAuthenticationPipelineLoad](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onauthenticationpipelineload?view=adfs-2019) вызывается, когда подключаемый модуль регистрируется с помощью AD FS при [OnConfigurationUpdate](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule.onconfigurationupdate?view=adfs-2019) вызывается при импорте CSV-файл с помощью `Import-AdfsThreatDetectionModuleConfiguration` командлета. 

#### <a name="irequestreceivedthreatdetectionmodule-interface"></a>Интерфейс IRequestReceivedThreatDetectionModule

Это [интерфейс](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule?view=adfs-2019) дает возможность реализовывать оценки рисков в точке, где службы федерации Active Directory получает запрос на проверку подлинности, но прежде чем пользователь вводит учетные данные т. е. на этапе получения запроса проверки подлинности. 
 
```
public interface IRequestReceivedThreatDetectionModule
{
Task<ThrottleStatus> EvaluateRequest (
ThreatDetectionLogger logger, 
RequestContext requestContext );
}
```

Интерфейс включает [EvaluateRequest](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule.evaluaterequest?view=adfs-2019) метод, который позволяет использовать контекст запроса на аутентификацию передается во входном параметре requestContext, чтобы реализовать логику оценки риска. RequestContext параметр имеет тип [RequestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019). 

Входной параметр, передаваемый является средство ведения журнала, который является типом [ThreatDetectionLogger](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionlogger?view=adfs-2019). Параметр может использоваться для записи ошибок, аудита и/или сообщения в AD FS журналы отладки. 

Этот метод возвращает [ThrottleStatus](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.throttlestatus?view=adfs-2019) (0, если NotEvaluated 1 блок и 2, чтобы разрешить) для AD FS чего блокирует или разрешает запроса.

В нашем примере подключаемого модуля [EvaluateRequest](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.irequestreceivedthreatdetectionmodule.evaluaterequest?view=adfs-2019) анализирует реализацию метода [clientIpAddress](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext.clientipaddresses?view=adfs-2019#Microsoft_IdentityServer_Public_ThreatDetectionFramework_RequestContext_ClientIpAddresses) из [requestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019) параметр и сравнивает его со всех IP-адресов загрузить из базы данных AD FS. Если соответствие найдено, метод возвращает 2 в параметре **блок**, в противном случае возвращается значение 1 для **Разрешить**. На основе возвращаемого значения, AD FS, блокирует или разрешает запроса. 

>[!NOTE]
>Образец подключаемого модуля описанных выше единственный интерфейс IRequestReceivedThreatDetectionModule реализует. Тем не менее, модель оценки риска предоставляет два дополнительных интерфейсов — IPreAuthenticationThreatDetectionModule (для реализации этапа предварительной проверки подлинности duing логики риск) и IPostAuthenticationThreatDetectionModule (для реализации рисками Оценка логики во время этапа после проверки подлинности). Ниже приведены сведения о двух интерфейсов. 

#### <a name="ipreauthenticationthreatdetectionmodule-interface"></a>Интерфейс IPreAuthenticationThreatDetectionModule 

Это [интерфейс](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipreauthenticationthreatdetectionmodule?view=adfs-2019) дает возможность реализовывать логику оценки риска в точке, где пользователь предоставляет учетные данные, но прежде чем AD FS оценивает их этап т. е. предварительной проверки подлинности. 

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
Интерфейс включает [EvaluatePreAuthentication](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipreauthenticationthreatdetectionmodule.evaluatepreauthentication?view=adfs-2019) переданный метод, позволяющий использовать информацию [RequestContext requestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019), [SecurityContext securityContext ](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext?view=adfs-2019), [ProtocolContext protocolContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext?view=adfs-2019), и [IList<Claim> additionalClams](https://docs.microsoft.com/dotnet/api/system.collections.generic.ilist-1?view=netframework-4.7.2) входные параметры, чтобы реализовать логику оценки риска предварительной проверки подлинности. 

>[!NOTE]
>Список свойств, передается с каждым типом контекста, см. в статье [RequestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019), [SecurityContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext?view=adfs-2019), и [ProtocolContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext?view=adfs-2019) определения классов. 

Входной параметр, передаваемый является средство ведения журнала, который является типом [ThreatDetectionLogger](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionlogger?view=adfs-2019). Параметр может использоваться для записи ошибок, аудита и/или сообщения в AD FS журналы отладки.

Этот метод возвращает [ThrottleStatus](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.throttlestatus?view=adfs-2019) (0, если NotEvaluated 1 блок и 2, чтобы разрешить) для AD FS чего блокирует или разрешает запроса. 

#### <a name="ipostauthenticationthreatdetectionmodule-interface"></a>Интерфейс IPostAuthenticationThreatDetectionModule

Это [интерфейс](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipostauthenticationthreatdetectionmodule?view=adfs-2019) дает возможность реализовывать логику оценки риска, после того как пользователь предоставил учетные данные и AD FS выполнил проверку подлинности, т. е. этап после проверки подлинности. 

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

Интерфейс включает [EvaluatePostAuthentication](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.ipostauthenticationthreatdetectionmodule.evaluatepostauthentication?view=adfs-2019) переданный метод, позволяющий использовать информацию [RequestContext requestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019), [SecurityContext securityContext ](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext?view=adfs-2019), [ProtocolContext protocolContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext?view=adfs-2019), и [IList<Claim> additionalClams](https://docs.microsoft.com/dotnet/api/system.collections.generic.ilist-1?view=netframework-4.7.2) входные параметры, чтобы реализовать логику оценки риска пост-проверки подлинности. 

>[!NOTE]
> Полный список свойств, передается с каждым типом контекста, см. в разделе [RequestContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.requestcontext?view=adfs-2019), [SecurityContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.securitycontext?view=adfs-2019), и [ProtocolContext](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.protocolcontext?view=adfs-2019) определения классов. 

Входной параметр, передаваемый является средство ведения журнала, который является типом [ThreatDetectionLogger](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionlogger?view=adfs-2019). Параметр может использоваться для записи ошибок, аудита и/или сообщения в AD FS журналы отладки. 

Этот метод возвращает [оценку риска](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.authentication.riskscoreconstants?view=adfs-2019) которого может использоваться в AD FS политики и правил утверждений. 

>[!NOTE]
>Для подключаемого модуля для работы основного класса (в данном случае UserRiskAnalyzer) должно быть производным [ThreatDetectionModule](https://docs.microsoft.com/dotnet/api/microsoft.identityserver.public.threatdetectionframework.threatdetectionmodule?view=adfs-2019) абстрактный класс, а также должны реализовывать хотя бы один из трех интерфейсов, описанных выше. После регистрации библиотеки dll, службы федерации Active Directory проверяет, какие интерфейсы реализуются и вызывает их в соответствующий этап в конвейере.

### <a name="faqs"></a>Вопросы и ответы

**Зачем создавать эти плагины?**</br>
**Ответ.** Эти модули не только предоставляют дополнительные возможности для защиты вашей среды от атак, таких как атаки Распылитель пароль, но также обеспечивают гибкость, чтобы создавать собственную логику оценки риска, на основе требований. 

**Где записываются журналы?**</br>
**Ответ.** Журналы ошибок можно написать с помощью метода WriteAdminLogErrorMessage журнал событий «AD FS/Admin», журналы аудита безопасности «Аудит AD FS» войдите с помощью метода WriteAuditMessage и отладочный журналы с помощью метода WriteDebugMessage журнал отладки «Трассировка AD FS». 

**Можно добавить эти плагины увеличить задержка процесса проверки подлинности AD FS?**</br>
**Ответ.** Влияние задержки будет определяться время, затраченное на выполнение логики оценки риска, которые реализовать. Рекомендуется проверить влияние задержки перед развертыванием подключаемый модуль в рабочей среде. 

**Почему AD FS не может предложить список опасных IP-адресов, пользователей и т. д?**</br>
**Ответ.** Хотя в настоящее время недоступно, мы работаем над построения аналитики, чтобы предложить опасных IP-адресов, пользователей, т. д., в подключаемой модели оценки риска. Мы будем публиковать запуск дат в ближайшее время. 
