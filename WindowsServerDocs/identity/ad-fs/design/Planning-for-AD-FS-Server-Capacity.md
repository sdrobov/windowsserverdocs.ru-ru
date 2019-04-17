---
ms.assetid: ef91f1d8-2991-4d90-b687-5fa189737c88
title: "Планирование производительности сервера AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 484dd08edef85b91e777f8963f175a6172c75430
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="planning-for-ad-fs-server-capacity"></a>Планирование производительности сервера AD FS

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

  
> [!NOTE]  
> Информация в этом разделе не отражает результаты фактического тестирования на серверах под управлением Windows Server 2012. В этом разделе будет обновлен после проведения необходимых тестов.  
  
Для служб федерации Active Directory для планирования емкости \(AD FS\) — это процесс прогнозирования периодов пикового использования службы федерации и планирования или scaling\ до развертывания серверов AD FS в соответствии с указанными требованиями к нагрузке.  
  
В этом разделе содержатся рекомендации по развертыванию для сервера федерации и в роли прокси-сервера сервера федерации и основан на результаты лабораторных тестов, проведенных командой разработчиков AD FS в корпорации Майкрософт. Это содержимое предназначено помогут вам:  
  
-   Точно Оцените аппаратных требований для развертывания определенных Служб федерации Active Directory вашей организации, например количество серверов AD FS.  
  
-   Точно спрогнозировать ожидаемые пиковые периоды для одной запросов, спланировать расширение системы и убедитесь, что развертывание AD FS может обработать эту пиковую нагрузку.  
  
Прежде чем приступить к прочтению раздела о планировании емкости, рекомендуется выполнить задачи в указанном порядке, в следующих двух таблицах. В первой таблице представлены ссылки на рекомендованные задачи, которые помогут создать релевантный контекст для обсуждения проблемы планирования емкости.  
  
|Рекомендованная задача|Описание|Справочник по|  
|--------------------|---------------|-------------|  
|Сведения о требованиях к развертыванию серверов федерации AD FS и прокси-серверов федерации|Изучите важные аппаратные и программные требования, необходимые для развертывания сервера федерации и прокси-серверов федерации.|[Приложение a. Анализ требований AD FS](Appendix-A--Reviewing-AD-FS-Requirements.md)|  
|Выберите тип базы данных конфигурации AD FS, которая будет развернута в вашей организации|Прежде чем начать, использованию данных о планировании емкости из этого раздела, сначала необходимо определить, какой тип базы данных конфигурации AD FS развертывается, \(WID\) внутренней базы данных Windows или \(SQL\) языка базы данных.|[Роль базы данных конфигурации AD FS](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md);<br /><br />[Некоторые аспекты топологии развертывания AD FS](AD-FS-Deployment-Topology-Considerations.md)|  
|Определите тип структуры топологии, который будет использоваться с новой Выбор базы данных конфигурации AD FS|После выбора типа базы данных конфигурации AD FS для использования в вашем развертывании, необходимо будет принять во внимание какая топология развертывания наиболее точно соответствует, где необходимо будет федерация размещения серверов федерации и прокси-серверов в рабочей среде.|[Определение топологии развертывания AD FS](Determine-Your-AD-FS-Deployment-Topology.md)|  
|Понимание ключа AD FS, связанных с планированием загрузки|Изучите определения общих терминов, которые используются в обсуждении планирования емкости AD FS планирования емкости.|См. раздел [терминов планирования емкости AD FS](Planning-for-AD-FS-Server-Capacity.md#bk_terms) в этом разделе|  
  
Изучив содержимое предыдущей таблицы, можно выполнять обязательные задачи из следующей таблицы.  
  
|Обязательная задача|Описание|Справочник по|  
|---------------------|---------------|-------------|  
|Загрузите электронную таблицу масштабов для планирования емкости AD FS|Электронная таблица масштабов для планирования AD FS загрузки поможет вам определить число серверов федерации, необходимых для развертывания фермы серверов федерации AD FS. Инструкции по использованию этой электронной таблицей доступны по ссылке ниже, в следующей задаче.|[Таблицу планирования емкости AD FS](http://adfsdocs.blob.core.windows.net/adfs/ADFSCapacityPlanning.xlsx)|  
|Сбор данных о количестве пользователей, которым требуется единого входа на \(SSO\) доступ к в целевое приложение с поддержкой claims\ и ожидаемые пиковые периоды использования, связанные с этим доступом.|Собираемые данные этого пользователя будет использоваться в качестве входных значений в контексте AD FS масштабов электронной таблице планирования емкости.|[Рассчитайте необходимое количество серверов федерации для вашей организации](Planning-for-Federation-Server-Capacity.md#bk_estimatefs)|  
|AD FS емкости электронной таблице планирования для Windows Server 2016|Обновленный лист планирования для Windows Server 2016|[AD FS Windows Server 2016 планирования](http://adfsdocs.blob.core.windows.net/adfs/ADFSCapacity2016.xlsx)  
  
## <a name="bk_terms"></a>AD FS с планированием емкости  
В следующей таблице описаны важные понятия, которые часто используются в этом разделе планированию емкости AD FS Design Guide. Более полный список терминов AD FS см. в разделе [Understanding Key AD FS Concepts](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md).  
  
|Термин|Определение|  
|--------|--------------|  
|Число параллельных пользователей|Предполагаемое число пользователей, отправляющих запросы в службу в течение заданного периода времени, как правило периода пиковой активности.|  
|Активные пользователи|Примерное среднее число пользователей, которые являются активными в системе, но не обязательно подающих запросы, в течение указанного периода времени.|  
|Определенные пользователи|Теоретическое максимальное число пользователей, обычно в зависимости от числа пользователей с определенными учетными записями в системе.|  
|Запросов в секунду|Число запросов, отправляемых клиентами либо \ (в контексте нагрузки на записи во) или обрабатываемых серверами \ (в контексте throughput\ сервера) в секунду. Этот параметр используется в планировании емкости сервера процессора и памяти.|  
|Сервер целевое время реагирования и использование|Показатели работоспособности системы, определяющие допустимый диапазон производительности сервера. Как правило если реагирования ниже, а использование сервера выше целевого, система считается перегруженной, и требуется дополнительная емкость.|  
|Внутренней базы данных Windows \(WID\)|По умолчанию AD FS базы данных конфигурации, можно использовать как альтернативу SQL Server в определенных развертываниях Служб федерации Active Directory.|  
  
## <a name="configuration-environment-used-during-ad-fs-testing"></a>Среда конфигурации, используемая в тестировании AD FS  
В этом разделе описывается среда конфигурации, используемые группы разработчиков AD FS для проведения тестов. Команда использует следующую аппаратную, программное обеспечение и конфигурации сети для сбора производительности данных и масштабируемости при тестировании сервера федерации.  
  
-   Два четырехъядерных процессора 2,27 ГГц \(GHz\) \(8 cores\)  
  
-   БИБЛИОТЕКИ ГБ ОЗУ  
  
-   Windows Server 2008 R2 Enterprise Edition  
  
-   Сетевое подключение Gigabit  
  
> [!NOTE]  
> Несмотря на то, что 16 ГБ ОЗУ использовался на сервере федерации, во время тестирования, для большинства развертываний AD FS можно использовать более скромных ресурсов памяти, например 4 ГБ оперативной памяти на каждом сервере федерации. Рекомендации, которые предоставляются в этом AD FS планирования производительности и результаты, предоставляемые AD FS электронной таблице планирования емкости основаны на допущении, которые каждый сервер федерации будет использовать примерно на 4 ГБ ОЗУ для большинства рабочих сред AD FS.  
  
Команда специалистов по разработке использует следующую конфигурацию для сбора данных масштабируемости и производительности для тестирования прокси-сервера федерации:  
  
-   Два четырехъядерных процессора 2,24 ГГц \(4 cores\)  
  
-   4\ ГБ ОЗУ  
  
-   Windows Server 2008 R2 Enterprise Edition  
  
-   Сетевое подключение Gigabit  
  
> [!NOTE]  
> Рекомендации в отношении серверов AD FS емкости может сильно зависеть от, характеристики, которые вы выбираете для аппаратной и сетевой конфигурации, используемой в данной среде. Как контрольной точки рекомендации по масштабу в данном разделе основана на целевого показателя использования 80 процентов на компьютерах, было показано ранее.  
  
## <a name="measure-ad-fs-server-capacity"></a>Измерение емкости сервера AD FS  
Как правило влияют на производительность и масштабируемость сервера аппаратные компоненты: ЦП, памяти, дисков и сетевых адаптеров. К счастью все компоненты службы федерации Active Directory требуется незначительного количества ресурсов памяти и места на диске. Сетевого подключения — Очевидное требование. Следовательно Нагрузочные тесты, выполняемые на серверах федерации и прокси-серверов федерации сосредоточиться на две основные области измерение емкости сервера:  
  
-   **Пиковое количество запросов AD FS в секунду:** число запросов входа в систему, обрабатываемых в секунду на серверах федерации. Этот параметр помогает определить, сколько одновременных пользователи могут входить в данный сервер. Этот параметр в сочетании с количество потребляемых ресурсов ЦП позволяют понять этот параметр не влияет на производительность.  
  
-   **Потребление ресурсов ЦП:** процентное отношение, используемое ЦП для измерения емкости. Этот параметр помогает определить общую нагрузку на ЦП на основе числа входящих запросов в одной в секунду.  
  
## <a name="continue-reading-more-about-ad-fs-capacity-planning"></a>Узнайте больше о планировании емкости AD FS  
После завершения обязательные задачи и ознакомившись с соответствующими определениями и аппаратными требованиями, можно использовать следующие дополнительные планированию емкости, чтобы определить Рекомендованное количество серверов AD FS, необходимых для развертывания:  
  
-   [Планирование емкости сервера федерации](Planning-for-Federation-Server-Capacity.md)  
  
-   [Планирование емкости прокси-сервера федерации](Planning-for-Federation-Server-Proxy-Capacity.md)  
  
## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)