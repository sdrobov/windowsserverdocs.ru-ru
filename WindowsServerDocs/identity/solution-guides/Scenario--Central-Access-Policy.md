---
ms.assetid: 7f285c9f-c3e8-4aae-9ff4-a9123815114e
title: Политика централизованного доступа к сценарию
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: a22592e5c8af9fa23725de90a14a9a8a46c286d7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80861157"
---
# <a name="scenario-central-access-policy"></a>Сценарий: централизованная политика доступа

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Централизованные политики доступа для файлов позволяют организациям централизованно развертывать политики авторизации, содержащие условные выражения, использующие группы пользователей, утверждения пользователей, заявки на доступ и свойств ресурсов, а также управлять этими политиками. (Утверждения — это заявления об атрибутах объекта, с которым они связаны.) Например, для доступа к данным, имеющим значительное влияние на бизнес (HBI), пользователь должен быть штатным сотрудником и войти с помощью смарт-карты. Эти политики задаются и размещаются в доменных службах Active Directory (AD DS).  
  
Политики доступа в организации определяются требованиями соответствия и нормативными требованиями бизнеса. Например, если бизнес-требования организации включают разрешение доступа к персональным данным в файлах только владельцу файла и сотрудникам отдела кадров, которым разрешено просматривать персональные данные, эта политика применяется к файлам персональных данных, на каком бы из файловых серверов организации они ни располагались. В данном примере вы должны иметь следующие возможности.  
  
-   Идентифицировать и пометить файлы, содержащие личные сведения.  
  
-   Идентифицировать группу сотрудников отдела кадров, которой разрешен просмотр личных сведений.  
  
-   Создать централизованную политику доступа, которая применяется ко всем файлам, содержащим персональные данные, на каких бы файловых серверах в организации они ни находились.  
  
Желание развернуть и применить политику авторизации может возникнуть по многим причинам и на различных уровнях организации. Ниже приводится несколько примеров типов политик.  
  
-   **Политика авторизации на уровне организации.** Чаще всего применение политики авторизации инициирует отдел информационной безопасности для соблюдения нормативных или высокоуровневых корпоративных требований. Она применяется на уровне всего предприятия. Например, файлы данных, имеющих значительное влияние на бизнес, доступны только штатным сотрудникам.  
  
-   **Политика авторизации на уровне подразделения.** В каждом отделе организации имеются некоторые специальные требования к обработке данных, которые необходимо применить. Например, финансовый отдел может захотеть разрешить доступ к финансовым серверам только сотрудникам финансового отдела.  
  
-   **Отдельная политика управления данными.** Такая политика обычно связана с нормативными или бизнес-требованиями и нацелена на защиту доступа к управляемой информации. Например, в финансовых учреждениях может применяться политика, согласно которой у аналитиков не должно быть доступа к данным брокеров, а у брокеров — к данным аналитиков.  
  
-   **Политика служебной необходимости.** Этот тип политики авторизации обычно используется в сочетании с предыдущими типами политики. Например, поставщикам следует предоставить доступ для чтения и редактирования только файлов, связанных с проектом, над которым они работают.  
  
Реальные среды также учат нас, что каждая политика авторизации должна иметь исключения, чтобы организации могли быстро реагировать при возникновении важных бизнес-требований. Например, руководители, которые не смогли найти свои смарт-карты и при этом нуждаются в быстром доступе к данным, имеющим значительное влияние на бизнес, могут позвонить в службу поддержки, чтобы получить временное исключение для доступа к этим сведениям.  
  
Централизованные политики доступа служат "зонтиками" безопасности, прикрывающими все серверы. Эти политики дополняют (но не заменяют) политики локального доступа или списки управления доступом на уровне пользователей (DACL), применяемые к файлам и папкам. Например, если DACL для файла разрешает доступ конкретному пользователю, но централизованная политика, применяемая к этому файлу, ограничивает доступ тому же пользователю, то пользователь не сможет получить доступ к файлу. Если централизованная политика доступа разрешает доступ, а DACL запрещает, пользователь тоже не сможет получить доступ к файлу.  
  
Правило централизованной политики доступа состоит из следующих логических частей.  
  
-   **Область применения.** Условие, определяющее, к каким данным применяется политика, например, Resource.BusinessImpact=High.  
  
-   **Условия доступа.** Список из элементов управления доступом (ACE), определяющих, кто может обращаться к данным, таких как Allow | Full Control | User.EmployeeType=FTE.  
  
-   **Исключения.** Дополнительный список из элементов управления доступом, определяющих исключения для этой политики, например, MemberOf(HBIExceptionGroup).  
  
На следующих двух рисунках показан рабочий процесс в централизованной политике доступа и в политике аудита.  
  
![руководства по решениям](media/Scenario--Central-Access-Policy/DynamicAccessControl_RevGuide.JPG)  
  
**Рис. 1** Концепции централизованной политики доступа и политики аудита  
  
![руководства по решениям](media/Scenario--Central-Access-Policy/DynamicAccessControl_RevGuide_2.JPG)  
  
**Рис. 2** Рабочий процесс централизованной политики доступа  
  
В централизованную политику авторизации входят следующие компоненты.  
  
-   Список централизованно определенных правил доступа, предназначенных для определенных типов данных, например данных, имеющих значительное влияние на бизнес, или персональных данных.  
  
-   Централизованно определенная политика, содержащая список правил.  
  
-   Идентификатор политики, назначенный каждому файлу на файловых серверах для указания конкретной централизованной политики доступа, которая должна применяться во время авторизации доступа.  
  
На следующем рисунке показано, как можно объединить политики в списки политик для централизованного управления доступом к файлам.  
  
![руководства по решениям](media/Scenario--Central-Access-Policy/DynamicAccessControl_RevGuide3.JPG)  
  
**ис. 3** Объединение политик  
  
## <a name="in-this-scenario"></a>Содержание сценария  
Следующие рекомендации предоставляются для централизованных политик доступа.  
  
-   [Планирование развертывания централизованной политики доступа](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f)  
  
-   [Демонстрационные шаги по развертыванию централизованной политики &#40;доступа&#41;](Deploy-a-Central-Access-Policy--Demonstration-Steps-.md)  
  
-   [Динамический контроль доступа: обзор сценария](Dynamic-Access-Control--Scenario-Overview.md)  
  
## <a name="roles-and-features-included-in-this-scenario"></a><a name="BKMK_NEW"></a>Роли и компоненты, входящие в этот сценарий  
В следующей таблице перечислены роли и компоненты, являющиеся частью данного сценария, и описано, как они поддерживают его.  
  
|Роль/компонент|Способ поддержки сценария|  
|-----------------|---------------------------------|  
|Роль доменных служб Active Directory|AD DS в Windows Server 2012 представляет собой платформу авторизации на основе заявок, которая позволяет создавать заявки пользователей и заявки на устройства, составные удостоверения, (утверждения пользователя и устройства), новые модели централизованного доступа (CAP) и использовать сведения о классификации файлов при принятии решений об авторизации.|  
|Роль сервера файловых служб и служб хранилища|Роль «Файловые службы и службы хранилища» предоставляет технологии, предназначенные для настройки одного или нескольких файловых серверов (и управления ими), занимающих центральное расположение в сети, где можно хранить файлы и использовать их совместно с другими пользователями. Если пользователям требуется доступ к одним и тем же файлам и приложениям или если организации необходимо централизованное управление файлами и архивированием, то один или несколько компьютеров следует настроить как файловый сервер, установив роль "Файловые службы и службы хранения" и соответствующие службы роли.|  
|Клиентский компьютер Windows|Пользователи могут обращаться к файлам и папкам в сети через клиентский компьютер.|  
  


