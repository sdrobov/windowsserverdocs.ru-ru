---
ms.assetid: 38c9bcd3-c6f8-4153-8e42-5fd31568c65a
title: "Контрольный список - Настройка прокси-сервера федерации"
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 997ee901172eb2d873ad02fa8ce39da09c5171c7
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="checklist-setting-up-a-federation-server-proxy"></a>Контрольный список: Настройка прокси-сервера федерации

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Этот контрольный список содержит задачи развертывания для подготовки сервера под управлением Windows Server® 2012 для роли прокси-сервера федерации в \(AD FS\) служб федерации Active Directory.  
  
> [!NOTE]  
> Задачи в контрольном списке в порядке. Перехода по ссылке процедуры, вернитесь к данном разделу, после выполнения действия, описанные в этой процедуре, чтобы продолжить выполнение оставшихся задач контрольного списка.  
  
![настройки федеративного прокси-сервер](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**контрольный список: настройка прокси-сервера федерации**  
  
||Задача|Справочник по|  
|-|--------|-------------|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|Перед началом развертывания прокси-сервера федерации AD FS, просмотрите типы топологии развертывания AD FS и их связанных серверов и рекомендаций по разметке сети.|![настройки федеративного прокси-сервер](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[определение топологии развертывания AD FS](https://technet.microsoft.com/library/gg982491.aspx)<br /><br />![настройки федеративного прокси-сервер](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[планирование размещения прокси-сервера федерации](https://technet.microsoft.com/library/dd807130.aspx)<br /><br />![настройки федеративного прокси-сервер](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[место размещения прокси-сервера федерации](https://technet.microsoft.com/library/dd807048.aspx)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|Просмотрите емкости AD FS руководство по планированию, чтобы определить нужное число прокси-серверов федерации, который следует использовать в рабочей среде.|![настройки федеративного прокси-сервер](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Планирование емкости прокси-сервера федерации](https://technet.microsoft.com/library/gg749898.aspx)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|Определение лучше подходит для развертывания прокси-сервера федерации одного или ферму прокси-сервера федерации. **Примечание:** серверов федерации также выполнять обязанности прокси-сервера сервера федерации.|![настройки федеративного прокси-сервер](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[когда следует создавать прокси-сервера федерации](https://technet.microsoft.com/library/dd807032.aspx)<br /><br />![настройки федеративного прокси-сервер](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[когда следует создавать ферму прокси-сервера федерации](https://technet.microsoft.com/library/dd807082.aspx)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|Определите, будет ли создан этот прокси-сервера федерации в сети периметра организации партнера по учетным записям или в организации партнера по ресурсам.|![настройки федеративного прокси-сервер](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[сведения о роли прокси-сервера федерации в организации партнера по учетной записи](https://technet.microsoft.com/library/dd807109.aspx)<br /><br />![настройки федеративного прокси-сервер](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[сведения о роли прокси-сервера федерации в организации партнера по ресурсам](https://technet.microsoft.com/en-us/library/dd807052.aspx)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|Перед установкой на компьютере, который должен стать прокси-сервера федерации AD FS, сведения о важности получения сертификата проверки подлинности сервера — для фермы прокси-сервера федерации, добавив или совместного использования сертификатов для всех серверов в ферме.|![настройки федеративного прокси-сервер](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[требования к сертификатам для прокси-серверов федерации](https://technet.microsoft.com/library/dd807054.aspx)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|Просмотрите сведения в руководстве по проектированию AD FS об обновлении \(DNS\) доменных имен в сети периметра, может произойти успешное разрешение имен для серверов федерации и прокси-серверов федерации.|![настройки федеративного прокси-сервер](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[требования к разрешению имен для прокси-сервера федерации](https://technet.microsoft.com/library/dd807055.aspx)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|Определите, является ли прокси-сервер федерации должен быть присоединен к домену. Несмотря на то, что прокси-серверов федерации, присоединенных к домену не требуется, их легче управлять с помощью удаленного администрирования и возможности групповой политики, когда они присоединены к домену.|![настройки федеративного прокси-сервер](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[присоединить компьютер к домену](Join-a-Computer-to-a-Domain.md)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|В зависимости от настроек инфраструктуре DNS в сети периметра, выполните одну из процедур в разделах на непосредственно перед развертыванием прокси-сервера федерации в организации. **Примечание:** выполните обе процедуры. Чтение [требования к разрешению имен для прокси-серверов федерации](https://technet.microsoft.com/library/dd807055.aspx) для определения, какие процедуры наиболее подходящий требованиям вашей организации.|![настройки федеративного прокси-сервер](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[настроить разрешение имен для прокси-сервера федерации в зоне DNS, которая обслуживает только сеть периметра](Configure-Name-Resolution-for-a-Federation-Server-Proxy-in-a-DNS-Zone-That-Serves-Only-the-Perimeter-Network.md)<br /><br />![настройки федеративного прокси-сервер](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[настроить разрешение имен для прокси-сервера федерации в DNS зоны, выступает как сети периметра и Интернет-клиентов](Configure-Name-Resolution-for-a-Federation-Server-Proxy-in-a-DNS-Zone-That-Serves-Both-the-Perimeter-Network-and-Internet-Clients.md)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|После получения сертификата проверки подлинности сервера, необходимо установить его в \(IIS\) службы IIS на веб-сайте по умолчанию прокси-сервера федерации.|![настройки федеративного прокси-сервер](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Импорт сертификата проверки подлинности сервера на веб-сайт по умолчанию](Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|\(Optional\) в качестве альтернативы для получения сертификата проверки подлинности сервера из центра сертификации \(CA\), IIS можно использовать для получения сертификата пример для прокси-сервера федерации.<br /><br />Поскольку IIS создает многоразовый подписанный сертификат, который не берутся из надежного источника, используйте его для создания многоразовый подписанного сертификата только в следующих случаях:<br /><br />-Если необходимо создать \(SSL\) Secure Sockets Layer канал между сервером и ограничено, известные группы пользователей<br />-При наличии неполадок third\ субъекта сертификата **осторожность:** не является рекомендуемой мерой безопасности для развертывания прокси-сервера федерации в рабочей среде с помощью многоразовый подписью, сертификат проверки подлинности сервера.|![настройки федеративного прокси-сервер](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[IIS: Создание сертификата сервера Self\-Signed](https://go.microsoft.com/fwlink/?LinkID=108271)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|Установка службы роли прокси-агент службы федерации на компьютере, который должен стать прокси-сервера федерации.|![настройки федеративного прокси-сервер](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[установки службы роли прокси-сервера службы федерации](Install-the-Federation-Service-Proxy-Role-Service.md)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|Настройка AD FS программного обеспечения на компьютере, чтобы выступать в роли прокси-сервера федерации с помощью мастера настройки прокси-сервера AD FSFederation сервера.|![настройки федеративного прокси-сервер](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Настройка компьютера для роли прокси-сервера федерации](Configure-a-Computer-for-the-Federation-Server-Proxy-Role.md)|  
|![настройки федеративного прокси-сервера](media/icon_checkboxo.gif)|В средстве просмотра событий убедитесь, что служба прокси-сервера федерации была запущена.|![настройки федеративного прокси-сервер](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[убедитесь, что функционирования сервера федерации прокси-сервера](Verify-That-a-Federation-Server-Proxy-Is-Operational.md)|  