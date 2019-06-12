---
title: Использование политики DNS для балансировки нагрузки приложений с помощью сведений о географическом расположении
description: Этот раздел является частью DNS политики сценария руководство для Windows Server 2016
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-dns
ms.topic: article
ms.assetid: b6e679c6-4398-496c-88bc-115099f3a819
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 9f76163e6b064ac3225ab4d755afd548e1cb720b
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66446408"
---
# <a name="use-dns-policy-for-application-load-balancing-with-geo-location-awareness"></a>Использование политики DNS для балансировки нагрузки приложений с помощью сведений о географическом расположении

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе можно использовать, чтобы узнать, как настроить политики DNS для балансировки приложения с учетом географического расположения.

Предыдущей темы в этом руководстве [помощью политики DNS для балансировки нагрузки приложения](https://technet.microsoft.com/windows-server-docs/networking/dns/deploy/app-lb), использует пример вымышленной компании - Services подарок Contoso -, который предоставляет online внутриигровую служб и содержит веб-сайт с именем contosogiftservices.com. Службы Contoso подарок балансирует нагрузку от их online веб-приложений между серверами в Северной Америке центрах обработки данных, расположенных в Сиэтле, штат Вашингтон, Чикаго, Иллинойс и Даллас, штат Техас.

>[!NOTE]
>Рекомендуется ознакомиться с разделом [помощью политики DNS для балансировки нагрузки приложения](https://technet.microsoft.com/windows-server-docs/networking/dns/deploy/app-lb) перед выполнением инструкции в этом сценарии.

В этом разделе использует же вымышленной компании и сетевой инфраструктуры в качестве основы для нового развертывания пример, включающий awareness географического расположения.

В этом примере Contoso подарок службы успешно расширяет их присутствия по всему миру.

Как и в Северной Америке, у компании теперь есть веб-серверов, размещенных в европейских центрах обработки данных.

Contoso подарок служб DNS требуется настроить приложение балансировки нагрузки в европейских центрах обработки данных так же, как для реализации политики DNS в Соединенных Штатах, с трафиком приложений, распределенных между веб-серверами, которые находятся в папке Дублин, Ирландия, Амстердам, Голландия и в других местах.

Администраторы DNS имеет смысл также все запросы из других расположений в мире, распределены поровну между всеми свои центры обработки данных.

В следующих разделах рассказывается, как для достижения целей, аналогичные тем, администраторов DNS Contoso в вашей собственной сети.

## <a name="how-to-configure-application-load-balancing-with-geo-location-awareness"></a>Как настроить приложение балансировки нагрузки с помощью географического местоположения

Ниже показано, как настроить политики DNS для балансировки приложения с учетом географического расположения.

>[!IMPORTANT]
>В следующих разделах приведены примеры команд Windows PowerShell, которые содержат примеры значений для многих параметров. Убедитесь, что примеры значений в этих командах замените значения, которые подходят для развертывания, прежде чем вы выполните следующие команды.

### <a name="bkmk_clientsubnets"></a>Создание подсетей клиента DNS

Во-первых, необходимо определить подсети и пространства IP-адресов области Северной Америки и Европы.

Эти сведения можно получить из maps Geo-IP. На основе этих Geo-IP версий, необходимо создать подсети клиента DNS.

Подсеть клиента DNS — это логическая группа подсети IPv4 или IPv6, из которых запросы отправляются на DNS-сервер.

Можно использовать следующие команды Windows PowerShell для создания подсетей клиента DNS. 

    
    Add-DnsServerClientSubnet -Name "AmericaSubnet" -IPv4Subnet 192.0.0.0/24,182.0.0.0/24
    Add-DnsServerClientSubnet -Name "EuropeSubnet" -IPv4Subnet 141.1.0.0/24,151.1.0.0/24
    
Дополнительные сведения см. в разделе [DnsServerClientSubnet добавить](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverclientsubnet?view=win10-ps).

### <a name="bkmk_zscopes2"></a>Создание области зоны

После подсетей клиента находятся в месте, необходимо секционировать contosogiftservices.com зоны в другую зону области, для каждого центра обработки данных.

Область зоны — это уникальный экземпляр зоны. Зоны DNS может иметь несколько областей зоны, с каждой из областей зоны, содержащий собственный набор записей DNS. Та же запись могут присутствовать в нескольких областях, различные IP-адреса или же IP-адреса.

>[!NOTE]
>По умолчанию области зоны существует для зон DNS. Эта область зоны имеет то же имя, что зона и устаревших работы DNS работать в этой области.

Предыдущий сценарий для балансировки нагрузки приложения показано, как настроить три области зоны для центров обработки данных в Северной Америке.

С помощью приведенных ниже команд можно создать две дополнительные зоны области, по одной для в Дублине и Амстердам центрах обработки данных. 

Три существующих областей зоны Северной Америки в той же зоне, можно добавить эти области зоны, не сохраняя изменения. Кроме того после создания эти области зоны, вам не нужно перезапускать DNS-сервера.

Следующие команды Windows PowerShell можно использовать для создания области зоны.

    
    Add-DnsServerZoneScope -ZoneName "contosogiftservices.com" -Name "DublinZoneScope"
    Add-DnsServerZoneScope -ZoneName "contosogiftservices.com" -Name "AmsterdamZoneScope"
    

Дополнительные сведения см. в разделе [DnsServerZoneScope добавить](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverzonescope?view=win10-ps)

### <a name="bkmk_records2"></a>Добавление записей в области зоны

Теперь необходимо добавить записи, представляющий узел веб-сервера в области зоны.

Записи, касающиеся в центрах обработки данных в Америке были добавлены в предыдущем сценарии. Следующие команды Windows PowerShell можно использовать для добавления записей в области зоны для европейских центрах обработки данных.
 
    
    Add-DnsServerResourceRecord -ZoneName "contosogiftservices.com" -A -Name "www" -IPv4Address "151.1.0.1" -ZoneScope "DublinZoneScope”
    Add-DnsServerResourceRecord -ZoneName "contosogiftservices.com" -A -Name "www" -IPv4Address "141.1.0.1" -ZoneScope "AmsterdamZoneScope"
    

Дополнительные сведения см. в разделе [Add-DnsServerResourceRecord](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverresourcerecord?view=win10-ps).

### <a name="bkmk_policies2"></a>Создайте политики DNS

После создания секций (области зоны) и добавления записей, необходимо создать политики DNS, которые распределяют входящие запросы в этих областях.

В этом примере запрос распространения на серверах приложений в разных центрах обработки данных удовлетворяет следующим требованиям.

1. При получении запроса DNS из источника в подсети клиента Северной Америки, 50% ответов DNS точки в центр обработки данных в Сиэтле, 25% ответов пункты Чикаго центра обработки данных и выберите остальные 25% ответов в Далласе центр обработки данных.
2. При получении запроса DNS из источника в подсети клиента европейских 50% ответов DNS пункты Dublin центра обработки данных, и 50% ответов DNS укажите Амстердам центра обработки данных.
3. При запрос поступил из любому другому месту в мире, ответы DNS распределяются по всем пяти центрам обработки данных.

Следующие команды Windows PowerShell можно использовать для реализации этих политик DNS.

    
    Add-DnsServerQueryResolutionPolicy -Name "AmericaLBPolicy" -Action ALLOW -ClientSubnet "eq,AmericaSubnet" -ZoneScope "SeattleZoneScope,2;ChicagoZoneScope,1; TexasZoneScope,1" -ZoneName "contosogiftservices.com" –ProcessingOrder 1
    
    Add-DnsServerQueryResolutionPolicy -Name "EuropeLBPolicy" -Action ALLOW -ClientSubnet "eq,EuropeSubnet" -ZoneScope "DublinZoneScope,1;AmsterdamZoneScope,1" -ZoneName "contosogiftservices.com" -ProcessingOrder 2
    
    Add-DnsServerQueryResolutionPolicy -Name "WorldWidePolicy" -Action ALLOW -FQDN "eq,*.contoso.com" -ZoneScope "SeattleZoneScope,1;ChicagoZoneScope,1; TexasZoneScope,1;DublinZoneScope,1;AmsterdamZoneScope,1" -ZoneName "contosogiftservices.com" -ProcessingOrder 3
    
    

Дополнительные сведения см. в разделе [DnsServerQueryResolutionPolicy добавить](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverqueryresolutionpolicy?view=win10-ps).

Вы успешно создали политику DNS, которая обеспечивает как балансировку приложения на веб-серверов, расположенных в пяти разных центрах обработки данных на нескольких континентах.

Можно создать тысячи политик DNS в соответствии с трафиком требований к управлению, а все новые политики применяются динамически — без перезапуска DNS-сервер — на входящих запросов.
