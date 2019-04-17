---
ms.assetid: 02580b2f-a339-4470-947c-d700b2d55f3f
title: "Когда следует создавать ферму серверов федерации"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 2e7c991cf87bc0e6914e158f0878bcadbede3c22
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="when-to-create-a-federation-server-farm"></a>Когда следует создавать ферму серверов федерации

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Рассмотрите возможность создания фермы серверов федерации в \(AD FS\) служб федерации Active Directory, если у вас есть широкого развертывания Служб федерации Active Directory, и вы хотите обеспечить отказоустойчивость, балансировку load\ и масштабируемость в службе федерации вашей организации. Процесс создания двух или более серверов федерации в одной сети, настройка каждого из них для использования той же службы федерации и добавление открытого ключа сертификатов для подписи token\ каждого сервера управления AD FS оснастка создает ферму серверов федерации.  
  
Можно создать ферму серверов федерации или установить дополнительные серверы федерации в существующей ферме с помощью мастера конфигурации сервера AD FS федерации. Дополнительные сведения см. в разделе [When to Create a Federation Server](When-to-Create-a-Federation-Server.md).  
  
> [!NOTE]  
> Если выбран вариант создания **новой фермы серверов федерации** с помощью мастера конфигурации сервера AD FS федерации, мастер попытается создать объект-контейнер \(for sharing certificates\) в Active Directory. Таким образом важно при первом входе компьютер, где настраивается роль сервера федерации с учетной записью, которая имеет достаточные разрешения в Active Directory, чтобы создать этот объект-контейнер.  
  
Прежде чем серверы федерации могут быть сгруппированы в ферму, их необходимо кластеризовать, чтобы запросы, поступающие на один полное доменное имя \(FQDN\) направляются различным серверам федерации в ферме серверов. Можно создать кластер серверов, развернув \(NLB\) балансировки сетевой нагрузки в корпоративной сети. В этом руководстве предполагается, что балансировки сетевой Нагрузки была должным образом настроена для кластеризации каждого из серверов федерации в ферме.  
  
Дополнительные сведения о настройке FQDN кластера с помощью технологии Microsoft NLB см. в разделе [Указание параметров кластера](https://go.microsoft.com/fwlink/?LinkID=74651).  
  
## <a name="best-practices-for-deploying-a-federation-server-farm"></a>Рекомендации по развертыванию фермы серверов федерации  
Мы рекомендуем следующие рекомендации по развертыванию сервера федерации в рабочей среде.  
  
-   Если вы будете развертывать несколько серверов федерации в то же время, или вы знаете, что вы будут добавлены дополнительные серверы в ферму со временем, рассмотрите возможность создания образа существующего сервера федерации в ферме и последующей установкой из этого образа, когда вам нужно быстро создать дополнительные серверы федерации.  
  
    > [!NOTE]  
    > Если вы решаете использовать образ сервера для развертывания дополнительных серверов федерации, у вас для выполнения задач в [Checklist: Setting Up a Federation Server](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server.md) каждый раз, чтобы добавить новый сервер к ферме.  
  
-   Используйте балансировки сетевой Нагрузки или другие формы кластеризации, чтобы выделить один IP-адрес для многих компьютеры серверов федерации.  
  
-   Зарезервируйте статический IP-адрес для каждого сервера федерации в ферме и в зависимости от конфигурации \(DNS\) доменных имен, вставьте исключение для каждого IP-адреса в \(DHCP\) Dynamic Host Configuration Protocol. Технология балансировки сетевой Нагрузки Майкрософт требует, что каждому серверу, входящему в кластер балансировки сетевой Нагрузки был назначен статический IP-адрес.  
  
-   Если база данных конфигурации AD FS будет храниться в базе данных SQL, избегайте изменения базы данных SQL из нескольких серверов федерации в то же время.  
  
## <a name="configuring-federation-servers-for-a-farm"></a>Настройка серверов федерации для фермы  
В следующей таблице описаны задачи, которые необходимо выполнить, чтобы каждый сервер федерации может участвовать в среде с фермой.  
  
|Задача|Описание|  
|--------|---------------|  
|Если вы используете SQL Server для хранения базы данных конфигурации AD FS|Ферма серверов федерации состоит из двух или более серверов федерации, которые совместно используют одну и ту же конфигурацию AD FS базы данных и сертификаты для подписи token\. База данных конфигурации может храниться в любой внутренней базе данных Windows или в базе данных SQL Server. Если вы планируете база данных конфигурации хранится в базе данных SQL, убедитесь, что база данных конфигурации доступна, чтобы его можно доступны для всех серверов федерации, которые участвуют в ферме. **Примечание:** для сценариев фермы важно, чтобы база данных конфигурации находилась на компьютере, который не участвует в качестве сервера федерации в ферме. Microsoft NLB не допускает компьютеров, участвующих в ферме, взаимодействовать друг с другом. **Примечание:** убедитесь, что удостоверение AppPool AD FS, в \(IIS\)\) служб IIS на каждом сервере федерации, который участвует в ферме, имеет доступ на чтение к базе данных конфигурации.|  
|Получение и совместное использование сертификатов|Сертификат можно получить один сервер проверки подлинности из общедоступного центра сертификации \ (CA\) — например, VeriSign. Затем можно настроить сертификат, чтобы все серверы федерации тот же закрытый ключ сертификата. Дополнительные сведения о совместном использовании сертификатов см. в разделе [Checklist: Setting Up a Federation Server](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server.md). **Примечание:** управления AD FS оснастка расценивает сертификаты проверки подлинности для серверов федерации как сертификаты связи служб.<br /><br />Дополнительные сведения см. в разделе [требования к сертификатам для серверов федерации](Certificate-Requirements-for-Federation-Servers.md).|  
|Наведите курсор на том же экземпляре SQL Server|Если база данных конфигурации AD FS будет храниться в базе данных SQL, новый сервер федерации должен указывать на тот же экземпляр SQL Server, используемый для других серверов федерации в ферме, чтобы новый сервер мог участвовать в ферме.|  
  
## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)