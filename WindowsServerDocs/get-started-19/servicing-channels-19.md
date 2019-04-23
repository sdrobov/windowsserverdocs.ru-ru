---
title: Каналы обслуживания
description: 'Объяснение каналы служб Windows Server: LTSC и SAC'
ms.prod: windows-server-threshold
ms.technology: server-general
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
ms.localizationpriority: high
ms.openlocfilehash: c4329339e37acbb0b589e767a570073f4ae1363f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59848735"
---
# <a name="windows-server-servicing-channels-ltsc-and-sac"></a>Windows Server каналы обслуживания: LTSC и SAC

>Область применения. Windows Server 2019, Windows Server 2016


**Два канала основного выпуска доступны клиентам Windows Server, канал долгосрочного обслуживания и Semi-Annual Channel.** 

Вы можете оставить сервера в канале Long-Term Servicing Channel (LTSC), перенести их в канал Semi-Annual Channel либо поместить разные сервера в разные каналы, в зависимости от того, что вам лучше подходит.


## <a name="long-term-servicing-channel-ltsc"></a>Long-Term Servicing Channel (LTSC)
Это модель выпуска, с которой вы уже знакомы (ранее она носила название "Long-Term Servicing *Branch*"), в рамках которой выпуск новой версии Windows Server происходит каждые 2–3 года. Пользователи имеют право на пять лет основной поддержки и пять лет расширенной поддержки. Этот канал подходит для систем, которым требуются более продолжительный период обслуживания и стабильность работы. Новые выпуски Semi-Annual Channel никак не затронут уже развернутые среды Windows Server 2016 и более ранние версии Windows Server. Канал Long-Term Servicing Channel продолжит получать обновления системы безопасности и не связанные с безопасностью обновления, но не получит новые функции и возможности.

> [!Note]  
> **Текущий продукт LTSC — Windows Server 2019**. Чтобы остаться в этом канале, необходимо установить (или продолжить использовать) ОС Windows Server 2019, которую можно установить в режиме основных серверных компонентов или в режиме сервера с возможностями рабочего стола.

## <a name="semi-annual-channel"></a>Semi-Annual Channel 
Полугодовой канал идеально подходит для клиентов, которые инновации быстро, чтобы воспользоваться преимуществами новых возможностей операционной системы в более быстром темпе, оба в приложениях – особенно построенных на контейнеров и микрослужб, а также в программно определяемых гибридный центр обработки данных. В рамках канала Semi-Annual Channel для продуктов Windows Server будут доступны новые выпуски два раза в год — весной и осенью. Для каждого выпуска в этом канале будет предоставляться поддержка в течение 18 месяцев, начиная с даты начального выпуска.

Большая часть функций, реализованных в канале Semi-Annual Channel, будет содержаться в следующем выпуске канала Long-Term Servicing для Windows Server. Редакции, функции и вспомогательное содержимое, входящие в состав выпусков, будут зависеть от отзывов клиентов.

Канал Semi-Annual Channel будет доступен корпоративным клиентам, участвующим в программе [Software Assurance](https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx), а также через Azure Marketplace или другого поставщика облачных услуг/услуг хостинга, а также в рамках программ лояльности, таких как подписки на Visual Studio.

> [!Note]  
> **Текущим выпуском канала Semi-Annual Channel является Windows Server версии 1809**. Чтобы поместить сервера в этот канал, необходимо установить ОС Windows Server версии 1809, которую можно установить в режиме Server Core или в виде сервера Nano Server, запущенного в контейнере. Обновления "на месте" с Windows Server 2016 до Windows Server версии 1809 не поддерживаются, поскольку эти ОС находятся в **разных каналах выпуска**. Windows Server версии 1809 не является обновлением Windows Server 2016 — это следующий выпуск Windows Server в Semi-Annual Channel.



В этой модели выпуски Windows Server идентифицируются по году и месяцу выпуска, например выпуск от 9-го месяца (сентября) 2017 года будет обозначаться как **версия 1709**. Новые выпуски Windows Server в канале Semi-Annual Channel появляются два раза в год. Срок поддержки для каждого выпуска будет составлять 18 месяцев.

## <a name="should-you-keep-servers-on-the-ltsc-or-move-them-to-the-semi-annual-channel"></a>Следует ли сохранить серверы в канале LTSC или переместить их в канал Semi-Annual Channel?
Ниже перечислены основные различия, которые следует принять во внимание.

- Вам необходимы быстрые инновации? Вам требуется ранний доступ к новейшим возможностям Windows Server? Вам необходимо поддерживать быстро меняющиеся гибридные приложения, интеграцию процессов эксплуатации и разработки,а также структуры Hyper-V? Если это так, вам следует **присоединиться к каналу Semi-Annual Channel**, установив **Windows Server версии 1809**. Как описано в этом разделе, вы будете получать новые версии два раза в год с 18-месячной основной производственной поддержкой для каждого выпуска. Вы можете получать их по программе корпоративного лицензирования, в виде служб по подписке Azure и Visual Studio. В настоящее время для выпусков в канале Semi-Annual Channel требуются корпоративное лицензирование и программа Software Assurance, если вы планируете запускать продукта в рабочей среде.
- Вам требуются стабильность и предсказуемость? Вам требуется запускать виртуальные машины и традиционные рабочие нагрузки на физических серверах? Если это так, вам следует **сохранить эти серверы в канале Long-Term Servicing Channel**. Текущий продукт LTSC — **Windows Server 2019**. Как описано в этом разделе, вы будете получать доступ к новым версиям каждые 2–3 года с 5-летней основной поддержкой и последующей 5-летней расширенной поддержкой для каждого выпуска. Выпуски LTSC доступны с помощью всех методов выпуска. Выпуски в канале LTSC доступны всем пользователям, независимо от применяемой модели лицензирования. 

В следующей таблице приведены основные различия между каналами.

|  | Long-Term Servicing Channel (Windows Server 2019) |Semi-Annual Channel (Windows Server) |
| ------------------- | ------------------------------------ | ------------------------------------------------- |
|Рекомендуемые сценарии | Файловые серверы общего назначения, рабочие нагрузки Microsoft и других производителей, традиционные приложения, инфраструктурные роли, программно-определяемые центры обработки данных и гиперконвергентная инфраструктура. | Контейнерные приложения, узлы контейнеров и сценарии с приложениями, где ускоренные инновации приносят пользу |
| Новые выпуски | Каждые 2–3 года |Каждые 6 месяцев |
| Поддержка |5 лет основной поддержки, а также 5 лет расширенной поддержки | 18 месяцев |
| Выпуски | Все доступные выпуски Windows Server | Выпуски Standard и Datacenter |
| Кому можно использовать | Все клиенты во всех каналах | Только облачные клиенты и Software Assurance |
| Параметры установки | Server Core и Server с возможностями рабочего стола | Server Core для узла контейнеров и образ контейнера Nano Server |                |


## <a name="device-compatibility"></a>Совместимость устройств
Если не будет указано иное, минимальные требования к оборудованию для запуска выпусков Semi-Annual Channel будут аналогичны минимальным требованиям, предъявляемым к последнему выпуску Long-Term Servicing Channel для Windows Server. Например, **текущим выпуском канала Long-Term Servicing Channel является Windows Server 2019**. Большинство драйверов оборудования продолжат работать в этих выпусках.

## <a name="servicing"></a>Обслуживание
Для обоих выпусков — Long-Term Servicing Channel и Semi-Annual Channel — будут доступны обновления системы безопасности, а также не связанные с безопасностью обновления. Выпуски будут отличаться лишь длительностью предоставления поддержки, как описано выше.

### <a name="servicing-tools"></a>Средства обслуживания
Существует множество средств, с помощью которых ИТ-специалисты могут обслуживать Windows Server. Каждый вариант имеет свои преимущества и недостатки с точки зрения возможностей, контроля, простоты и низких административных требований. Ниже приведены примеры средств обслуживания для управления обслуживающими обновлениями.

- **Обновления Windows (изолированный)**: Этот параметр доступен только для серверов, которые подключены к Интернету и имеют включено обновление Windows.
- **Windows Server Update Services (WSUS)** обеспечивают расширенный контроль над обновлениями Windows 10 и Windows Server и доступны в операционной системе Windows Server на уровне кода. Помимо возможности откладывать обновления организации могут также добавить уровень утверждения обновлений и развертывать их на конкретных компьютерах или в группах компьютеров по мере готовности.
- **System Center Configuration Manager** обеспечивает максимальный контроль над обслуживанием. ИТ-специалисты могут откладывать обновления, утверждать их и использовать различные возможности для целевых развертываний и контроля над использованием пропускной способности и временем развертывания.

Скорее всего, вы уже используете хотя бы один из этих вариантов, выбрав его с учетом имеющихся ресурсов, персонала и знаний. Вы можете продолжать использовать тот же процесс для выпусков Semi-Annual Channel: например, если вы уже используете System Center Configuration Manager для управления обновлениями, можно продолжать использовать его. Аналогичным образом, если вы используете WSUS, можно продолжать использовать эти службы.

## <a name="obtain-preview-releases-through-the-windows-insider-program"></a>Получение предварительных выпусков через программу предварительной оценки Windows
Тестирование предварительных сборок Windows Server помогает корпорации Microsoft и ее клиентам выявлять потенциальные проблемы до выпуска. Это также предоставляет клиентам уникальную возможность напрямую влиять на возможности продукта. 

Процесс разработки сборок и внесение в них изменений зависят от отзывов пользователей, получаемых корпорацией Майкрософт. Раннее тестирование и отзывы являются важным аспектом быстрого выпуска сборок.

Дополнительные сведения о том, как зарегистрироваться в программе предварительной оценки Windows см. в [документации к программе предварительной оценки Windows для Windows Server](https://docs.microsoft.com/windows-insider/at-work/).

## <a name="to-identify-windows-server-2019-and-windows-server-version-1809"></a>Идентификация Windows Server 2019 и Windows Server, версия 1809

>[!Note]  
> Инструкции ниже помогут идентифицировать LTSC и SAC и выявить различия между ними в целях управления жизненным циклом и общей инвентаризации.  Они не предназначены для определения совместимости приложений или представления поверхности определенного API.  Для обеспечения совместимости разработчикам приложений следует использовать другие инструкции, так как в течение срока эксплуатации системы могут добавляться компоненты, API и функции, либо они могут быть еще недоступны. [Версия операционной системы](https://docs.microsoft.com/windows/desktop/SysInfo/operating-system-version) — оптимальная отправная точка для разработчиков приложений.

Откройте Powershell и используйте командлет Get-ItemProperty или командлет Get-ComputerInfo, чтобы проверить соответствующие свойства в реестре.  Вместе с номером сборки вы сможете найти информацию о наличии или отсутствии LTSC или SAC по году выпуска, например 2019.  Это свойственно LTSC и не свойственно SAC.  Также вы узнаете время выпуска по идентификатору ReleaseId или WindowsVersion, например 1809, а также тип установки: основные серверные компоненты или сервер с возможностями рабочего стола. 

**Windows Server 2019 Datacenter Edition (LTSC) с примером возможностей рабочего стола:**

````PowerShell
Get-ItemProperty -Path "HKLM:\Software\Microsoft\Windows NT\CurrentVersion" | Select ProductName, ReleaseId, InstallationType, CurrentMajorVersionNumber,CurrentMinorVersionNumber,CurrentBuild
````

````
ProductName               : Windows Server 2019 Datacenter
ReleaseId                 : 1809
InstallationType          : Server
CurrentMajorVersionNumber : 10
CurrentMinorVersionNumber : 0
CurrentBuild              : 17763
````

**Windows Server, пример ядро сервера Standard Edition version 1809 (зоны SAC):**

````PowerShell
Get-ItemProperty -Path "HKLM:\Software\Microsoft\Windows NT\CurrentVersion" | Select ProductName, ReleaseId, InstallationType, CurrentMajorVersionNumber,CurrentMinorVersionNumber,CurrentBuild
````

````
ProductName               : Windows Server Standard
ReleaseId                 : 1809
InstallationType          : Server Core
CurrentMajorVersionNumber : 10
CurrentMinorVersionNumber : 0
CurrentBuild              : 17763
````

**Пример 2019 Standard Edition (LTSC) ядра сервера Windows Server.**


````PowerShell
Get-ComputerInfo | Select WindowsProductName, WindowsVersion, WindowsInstallationType, OsServerLevel, OsVersion, OsHardwareAbstractionLayer
````

````
WindowsProductName            : Windows Server 2019 Standard
WindowsVersion                : 1809
WindowsInstallationType       : Server Core
OsServerLevel                 : ServerCore
OsVersion                     : 10.0.17763
OsHardwareAbstractionLayer    : 10.0.17763.107
````

Чтобы уточнить наличие на сервере новой [функции совместимости приложений основных серверных компонентов по требованию](https://docs.microsoft.com/windows-server/get-started-19/install-fod-19), воспользуйтесь командлетом [Get-WindowsCapability](https://docs.microsoft.com/powershell/module/dism/get-windowscapability?view=win10-ps) и найдите:
````
Name    :     ServerCore.AppCompatibility~~~~0.0.1.0
State   :     Installed
````

# <a name="related-topics"></a>См. также
[Изменения в Nano Server в Windows Server Semi-Annual Channel](../get-started/nano-in-semi-annual-channel.md)

[Жизненный цикл поддержки Windows Server](https://support.microsoft.com/lifecycle)

[Определение того, работает ли основных серверных компонентов](https://msdn.microsoft.com/library/hh846315%28v=vs.85%29.aspx?f=255&MSPPError=-2147217396)

[Функция GetProductInfo](https://docs.microsoft.com/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getproductinfo)

[Командлеты инвентаризации программного обеспечения](https://docs.microsoft.com/powershell/module/softwareinventorylogging/?view=winserver2012R2-ps)
