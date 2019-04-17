---
ms.assetid: 6618b3ce-0e94-4009-b887-d8e05453358b
title: "Ферма серверов федерации с использованием SQL Server"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: a0fff975b9cb278e59686323d2bd72e641597573
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="federation-server-farm-using-sql-server"></a>Ферма серверов федерации с использованием SQL Server

>Область применения: Windows Server 2012

Данная топология для служб федерации Active Directory \(AD FS\) отличается от фермы серверов федерации с использованием топологии развертывания \(WID\) внутренней базы данных Windows, в том, что она не реплицирует данные для каждого сервера федерации в ферме. Вместо этого все серверы федерации в ферме можно чтения и записи данных в общей базы данных, который хранится на сервере под управлением Microsoft SQL Server, который находится в корпоративной сети.  
  
## <a name="deployment-considerations"></a>Рекомендации по развертыванию  
В этом разделе приведены основные аспекты, которые об целевая аудитория, преимущества и ограничения, связанные с этой топологии развертывания.  
  
### <a name="who-should-use-this-topology"></a>Кому следует использовать эту топологию?  
  
-   Больших организациях с более 100 отношений доверия, которые необходимо предоставить доступ в рамках единого входа на \(SSO\) федеративных приложений или служб и их внутренних пользователей, так и для внешних пользователей  
  
-   Организациям, уже используется SQL Server и хотите воспользоваться преимуществами их существующих средств и опыта  
  
### <a name="what-are-the-benefits-of-using-this-topology"></a>В чем заключаются преимущества использования этой топологии?  
  
-   Поддержка отношения доверия с большим количеством \(more than 100\)  
  
-   Поддержка обнаружение воспроизведения токенов \(a security feature\) и разрешение артефактов \ (часть \(SAML\) Security Assertion Markup Language 2.0 protocol\)  
  
-   Поддержка всеми преимуществами SQL Server, например зеркального отображения, средства отказоустойчивой кластеризации, отчетов и управления  
  
### <a name="what-are-the-limitations-of-using-this-topology"></a>Что такое ограничений использования этой топологии  
  
-   В этой топологии не обеспечивают избыточность базы данных по умолчанию. Несмотря на то, что ферме серверов федерации с топологией WID автоматически реплицирует базы данных WID, на каждый сервер федерации в ферме, ферма серверов федерации с топологией SQL Server содержит только одну копию базы данных  
  
> [!NOTE]  
> SQL Server поддерживает многие другие данные и параметры избыточности приложения, в том числе отказоустойчивой кластеризации, зеркального отображения базы данных и различных типов репликации SQL Server.  
  
Отдела информационных технологий \(IT\) использует зеркального отображения базы данных SQL Server в режиме \(synchronous\) сценарии высокой безопасности и отказоустойчивой кластеризации для обеспечения поддержки сценарии высокой доступности для экземпляра SQL Server. \(Peer\-to\-peer\) транзакций SQL Server и репликации слиянием не проводила тестирование группы разработчиков AD FS в корпорации Майкрософт. Дополнительные сведения о SQL Server см. в разделе [Обзор решений высокой доступности](https://go.microsoft.com/fwlink/?LinkId=179853) или [выбора соответствующих типов репликации](https://go.microsoft.com/fwlink/?LinkId=214648).  
  
### <a name="supported-sql-server-versions"></a>Поддерживаемые версии SQL Server  
AD FS, установленные с Windows Server 2012 поддерживаются следующие версии SQL server.  
  
-   SQL Server 2008 \ / R2  
  
-   SQL Server 2012  
  
## <a name="server-placement-and-network-layout-recommendations"></a>Рекомендации для макета сервера размещения и сети  
Как ферма серверов федерации с топологией WID, все серверы федерации в ферме настроены для использования одного имени кластера \(DNS\) доменных имен \ (представляет имя службы федерации) и IP-адрес одного кластера в составе конфигурации кластера балансировки сетевой нагрузки \(NLB\). Это помогает узле балансировки сетевой Нагрузки распределения клиентских запросов между отдельными серверами федерации. Прокси-серверы федерации можно использовать для клиентских запросов прокси-сервера федерации в ферму серверов федерации.  
  
На следующем рисунке показано, как вымышленная компания Contoso Pharmaceuticals развернуть его фермы серверов федерации с топологией SQL Server в корпоративной сети. В нем также показано, как настроить эту компанию сети периметра с доступом к DNS-сервера, дополнительные узла балансировки сетевой Нагрузки, использующий же \(fs.contoso.com\) кластера DNS имя, используемое на кластера балансировки сетевой Нагрузки корпоративной сети, и два прокси-сервера федерации \(fsp1 and fsp2\).  
  
![Ферма серверов с использованием SQL](media/FarmSQLProxies.gif)  
  
Дополнительные сведения о том, как настроить сетевую среду для использования с серверами федерации или прокси-сервера федерации см. в разделе [требования к разрешению имен для серверов федерации](Name-Resolution-Requirements-for-Federation-Servers.md) или [требования к разрешению имен для прокси-серверов федерации](Name-Resolution-Requirements-for-Federation-Server-Proxies.md).  
  
## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)