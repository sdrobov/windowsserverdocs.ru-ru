---
title: Использование политики DNS для балансировки нагрузки приложений
description: Этот раздел является частью DNS политики сценария руководство для Windows Server 2016
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-dns
ms.topic: article
ms.assetid: f9c313ac-bb86-4e48-b9b9-de5004393e06
ms.author: pashort
author: shortpatti
ms.openlocfilehash: dca60fc0e216b1b873bd4f94dd1b01174d80fc14
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66446439"
---
# <a name="use-dns-policy-for-application-load-balancing"></a>Использование политики DNS для балансировки нагрузки приложений

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе можно использовать, чтобы узнать, как настроить политики DNS для выполнения балансировки нагрузки приложения.

Предыдущие версии Windows Server DNS предоставляется только для балансировки нагрузки с помощью циклического перебора ответов; но со службой DNS в Windows Server 2016, можно настроить политики DNS для балансировки нагрузки приложения.

При развертывании нескольких экземпляров приложения, можно использовать политики DNS для балансировки нагрузки трафика между экземплярами приложений с различными, тем самым динамического выделения нагрузки трафика для приложения.

## <a name="example-of-application-load-balancing"></a>Пример метода балансировки нагрузки приложения

Ниже приведен пример того, как можно использовать политики DNS для балансировки нагрузки приложения.

В этом примере используется один вымышленной компании - Services подарок Contoso — которая предоставляет службы online gifing и содержит веб-сайт с именем **contosogiftservices.com**.

Contosogiftservices.com веб-сайт размещается в нескольких центрах обработки данных, каждый из которых содержит разные IP-адреса.

В Северной Америке, являющаяся первичной рынка для Contoso подарок служб, веб-сайт размещается в трех центрах обработки данных: Chicago, IL, Dallas, TX and Seattle, WA.

Сиэтл веб-сервера содержит оптимальной конфигурации оборудования и может обслуживать вдвое больше нагрузки, как на остальных двух сайтах. Службы подарок Contoso хочет приложения трафик, направленный следующим образом.

- Сиэтл веб-сервера включает больше ресурсов, половины клиентов приложения будут направляться на этот сервер
- Одна четверть клиентов приложения направляются в центр обработки данных Даллас, Техас
- Одна четверть приложения клиентов направляются в Чикаго, Иллинойс, центр обработки данных

Этот сценарий показан на следующем рисунке.

![DNS приложения балансировки нагрузки с помощью политики DNS](../../media/Dns-App-Lb/dns-app-lb.jpg)


### <a name="how-application-load-balancing-works"></a>Приложения балансировки Works

После настройки DNS-сервера с помощью политики DNS для приложения загрузки балансировки с помощью этот пример сценария, сервер DNS отвечает, 50% времени с Сиэтл адрес веб-сервера, 25% времени с помощью Dallas веб-адрес сервера, а 25% по времени Чикаго веб-адрес сервера.

Таким образом на каждые четыре запросы DNS-сервер получает, он дает ответ с двух ответов для Сиэтла и одному для каждого Dallas и Чикаго.

Одно из возможных осложнений, с помощью балансировки нагрузки с помощью политики DNS является кэширование записи DNS с помощью DNS-клиент и Сопоставитель/LDNS, которые могут мешать балансировку нагрузки, поскольку клиент или распознаватель не отправляют запрос на DNS-сервер.

Эффект такого поведения можно избежать, используя низкой время\-для\-Live \(TTL\) значение для записи DNS, должен быть сбалансирован.

### <a name="how-to-configure-application-load-balancing"></a>Настройка балансировки нагрузки приложений

Ниже показано, как настроить политики DNS для балансировки нагрузки приложения.

#### <a name="create-the-zone-scopes"></a>Создание области зоны

Во-первых, необходимо создать областей contosogiftservices.com зоны для центров обработки данных в их размещения.

Область зоны — это уникальный экземпляр зоны. Зоны DNS может иметь несколько областей зоны, с каждой из областей зоны, содержащий собственный набор записей DNS. Та же запись могут присутствовать в нескольких областях, различные IP-адреса или же IP-адреса.

>[!NOTE]
>По умолчанию области зоны существует для зон DNS. Эта область зоны имеет то же имя, что зона и устаревших работы DNS работать в этой области.

Следующие команды Windows PowerShell можно использовать для создания области зоны.
    
    Add-DnsServerZoneScope -ZoneName "contosogiftservices.com" -Name "SeattleZoneScope"
    
    Add-DnsServerZoneScope -ZoneName "contosogiftservices.com" -Name "DallasZoneScope"
    
    Add-DnsServerZoneScope -ZoneName "contosogiftservices.com" -Name "ChicagoZoneScope"

Дополнительные сведения см. в разделе [DnsServerZoneScope добавить](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverzonescope?view=win10-ps)

#### <a name="bkmk_records"></a>Добавление записей в области зоны

Теперь необходимо добавить записи, представляющий узел веб-сервера в области зоны.

В **SeattleZoneScope**, вы можете добавить записи www.contosogiftservices.com с IP-адресом 192.0.0.1, который находится в Сиэтле центра обработки данных.

В **ChicagoZoneScope**, можно добавить ту же запись \(www.contosogiftservices.com\) с IP-адресом 182.0.0.1 в Чикаго центра обработки данных.

Аналогичным образом в **DallasZoneScope**, вы можете добавить запись \(www.contosogiftservices.com\) с IP-адресом 162.0.0.1 в Чикаго центра обработки данных.

Следующие команды Windows PowerShell можно использовать для добавления записей в области зоны.
    
    Add-DnsServerResourceRecord -ZoneName "contosogiftservices.com" -A -Name "www" -IPv4Address "192.0.0.1" -ZoneScope "SeattleZoneScope
    
    Add-DnsServerResourceRecord -ZoneName "contosogiftservices.com" -A -Name "www" -IPv4Address "182.0.0.1" -ZoneScope "ChicagoZoneScope"
    
    Add-DnsServerResourceRecord -ZoneName "contosogiftservices.com" -A -Name "www" -IPv4Address "162.0.0.1" -ZoneScope "DallasZoneScope"
    

Дополнительные сведения см. в разделе [Add-DnsServerResourceRecord](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverresourcerecord?view=win10-ps).

#### <a name="bkmk_policies"></a>Создайте политики DNS

После создания секций (области зоны) и добавления записей, необходимо создать политики DNS, которые распределяют входящие запросы в этих областях, таким образом, 50% запросов для contosogiftservices.com получение ответа с IP-адрес веб-приложений сервер в Сиэтле центра обработки данных, а остальные равномерно распределяются между Чикаго и Далласе центрах обработки данных.

Чтобы создать политику DNS, которая распределяет трафик приложения между этими тремя центрами обработки данных, можно использовать следующие команды Windows PowerShell.

>[!NOTE]
>В примере команды ниже, выражение – зонаобласть «SeattleZoneScope, 2; ChicagoZoneScope, 1; DallasZoneScope, 1" настраивает DNS-сервер с массивом, содержащим сочетание параметров \<зонаобласть\>,\<вес\>.
    
    Add-DnsServerQueryResolutionPolicy -Name "AmericaPolicy" -Action ALLOW -ZoneScope "SeattleZoneScope,2;ChicagoZoneScope,1;DallasZoneScope,1" -ZoneName "contosogiftservices.com"
    

Дополнительные сведения см. в разделе [DnsServerQueryResolutionPolicy добавить](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverqueryresolutionpolicy?view=win10-ps).  

Вы успешно создали политику DNS, которая обеспечивает как балансировку приложения на веб-серверов в трех разных центрах обработки данных.

Можно создать тысячи политик DNS в соответствии с трафиком требований к управлению, а все новые политики применяются динамически — без перезапуска DNS-сервер — на входящих запросов.
