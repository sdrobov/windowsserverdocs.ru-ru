---
title: Протокол пограничного шлюза (BGP)
description: В этом разделе можно использовать, чтобы узнать, какие из пограничного шлюза протокола (BGP) в Windows Server 2016, включая топологиях развертывания BGP поддерживается и его компонентах и возможностях.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78cc2ce3-a48e-45db-b402-e480b493fab1
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 65af14e3adfacd96334e2326f8dd0b346e27034a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59850185"
---
# <a name="border-gateway-protocol-bgp"></a>Протокол пограничного шлюза (BGP)

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

В этом разделе вы можете получить представление о протоколе BGP, в том числе о поддерживаемых им топологиях развертывания, а также его компонентах и возможностях.  
  
> [!NOTE]  
> Дополнение к данному разделу доступна следующая документация по BGP.  
>   
> -   [Справочник по командам PowerShell Windows BGP](../../remote-access/bgp/BGP-Windows-PowerShell-Command-Reference.md)  
  
Эта статья содержит следующие разделы.  
  
-   [BGP поддерживаемые топологии развертывания](#bkmk_top)  
  
-   [Возможности BGP](#bkmk_features)  
  
При настройке на Windows Server 2016 службы удаленного доступа \(RAS\) шлюза в мультитенантном режиме протокола пограничного шлюза (BGP) дает возможность управлять маршрутизацией сетевого трафика между сетями виртуальных Машин клиентов и их удаленными сайтами. Можно также использовать BGP для развертывания шлюза RAS одного клиента, а также при развертывании удаленного доступа к локальной сети \(LAN\) маршрутизатора.  
  
Протокол BGP снижает потребность в ручной настройке маршрутов в маршрутизаторах, так как является протоколом динамической маршрутизации и автоматически определяет маршруты между сайтами, связанными с помощью межсайтовых подключений VPN.  
  
Для использования маршрутизации BGP, необходимо установить **службы удаленного доступа \(RAS\)**  и/или **маршрутизации** службой роли из роли сервера удаленного доступа на компьютере или виртуальной машины \(Виртуальной Машины\) -тип используемой системы зависит от того, является ли развертывание мультитенантным:  
  
-   В мультитенантном развертывании рекомендуется устанавливать на один или несколько виртуальных машин шлюза RAS. Использование нескольких виртуальных машин обеспечивает высокий уровень доступности. Шлюз RAS может обрабатывать несколько подключений от нескольких клиентов и состоит из узла Hyper-V и виртуальной Машине, которая настроена как шлюз. Этот шлюз настраивается с помощью VPN-подключения сеть сеть как мультитенантный маршрутизатор BGP в клиенте exchange и поставщика облачных служб \(CSP\) маршрутов подсети.  
  
-   Для развертывания шлюза edge одного клиента или развертывание маршрутизатора локальной сети шлюз RAS можно установить на физическом компьютере или виртуальной Машины.  
  
> [!IMPORTANT]  
> При установке шлюза RAS необходимо указать, включен ли протокол BGP для каждого клиента с помощью **Enable-RemoteAccessRoutingDomain** команду Windows PowerShell с **тип** значение параметра  **Все**. Для установки удаленного доступа в качестве маршрутизатора локальной сети с поддержкой BGP без многопользовательских возможности, можно использовать команду **Install-RemoteAccess - VpnType RoutingOnly**.  
>   
> В следующем примере кода показано, как для установки удаленного доступа в мультитенантном режиме со всеми функциями удаленного доступа (типа "точка сеть" сеть сеть VPN и BGP маршрутизации) включена для двух клиентов: Contoso и Fabrikam.  
  
```  
$Contoso_RoutingDomain = "ContosoTenant"  
$Fabrikam_RoutingDomain = "FabrikamTenant"  
  
Install-RemoteAccess -MultiTenancy  
  
Enable-RemoteAccessRoutingDomain -Name $Contoso_RoutingDomain -Type All -PassThru  
Enable-RemoteAccessRoutingDomain -Name $Fabrikam_RoutingDomain -Type All -PassThru  
```  
  
## <a name="bkmk_top"></a>BGP поддерживаемые топологии развертывания  
Ниже перечислены поддерживаемые топологии развертывания, в которых сайты предприятия подключены к центру обработки данных поставщика облачных услуг (CSP).  
  
Во всех сценариях шлюзом CSP является шлюз удаленного доступа Windows Server 2016 на границе. Шлюз RAS, который способен обрабатывать несколько подключений от нескольких клиентов, состоит из узла Hyper-V и виртуальной Машине, которая настроена как шлюз. Этот пограничный шлюз настраивается для межсайтовых подключений VPN как мультитенантный маршрутизатор BGP, служащий для обмена маршрутами между предприятием и подсетью CSP.  
  
Клиенты подключаются к своим ресурсам в центре обработки данных CSP с помощью межсайтовых (S2S) подключений VPN. Кроме того, протокол маршрутизации BGP развертывается для динамического обмена информацией о маршрутизации между предприятием и шлюзами CSP.  
  
Поддерживаются указанные ниже топологии развертывания.  
  
-   [Шлюз VPN удаленного доступа сайт-сайт с использованием BGP на границе сайта предприятия](#bkmk_top1)  
  
-   [Сторонний шлюз с BGP на границе сайта предприятия](#bkmk_top2)  
  
-   [Несколько сайтов предприятия со сторонними шлюзами](#bkmk_top3)  
  
-   [Отдельные точки завершения для BGP и VPN](#bkmk_top4)  
  
В дальнейших подразделах приведены дополнительные сведения о каждой поддерживаемой топологии BGP.  
  
### <a name="bkmk_top1"></a>Шлюз VPN удаленного доступа сайт-сайт с использованием BGP на границе сайта предприятия  
В этой топологии представлен сайт предприятия, подключенный к CSP. Топология маршрутизации предприятия включает внутренний маршрутизатор, шлюз удаленного доступа Windows Server 2016 настроен для подключения сеть сеть VPN с CSP и устройство пограничного брандмауэра. Шлюз RAS завершает соединения S2S VPN и BGP.  
  
![Сеть сеть шлюза VPN удаленного доступа](../../media/Border-Gateway-Protocol-BGP/bgp_01.jpg)  
  
Оба сайта подключаются по протоколу eBGP, который позволяет передавать данные между маршрутизаторами с поддержкой BGP в отдельных автономных системах. Для этого необходимо, чтобы у предприятия и CSP были отдельные номера автономных систем (ASN), что является неотъемлемым параметром протокола BGP.  
  
В этом сценарии протокол BGP работает описанным ниже образом.  
  
-   Пограничное устройство сайта предприятия определяет маршруты виртуализованной подсети (10.2.1.0/24), размещенной в облаке, с помощью BGP. Это устройство также сообщает маршруты локальной подсети (10.1.1.0/24) для Мультитенантного шлюза RAS CSP.  
  
-   Пограничный маршрутизатор клиента определяет внутренние локальные маршруты одним из указанных ниже способов.  
  
    -   Пограничное устройство использует протокол BGP с внутренним маршрутизатором и определяет внутренние маршруты (в этом примере это 10.1.1.0/24). Тем временем внутренний маршрутизатор узнает внутренние маршруты (например, 10.2.1.0/24) от пограничного устройства и должен предоставить эти маршруты другим локальным маршрутизаторам с помощью протокола IGP, такого как OSPF или RIP.  
  
    -   В пограничном устройстве можно настроить статические маршруты или интерфейсы для выбора маршрутов, которые должны объявляться посредством BGP. Пограничное устройство также сообщает внешние маршруты другим локальным маршрутизаторам с помощью IGP.  
  
### <a name="bkmk_top2"></a>Сторонний шлюз с BGP на границе сайта предприятия  
В этой топологии представлен сайт предприятия, который использует сторонний пограничный маршрутизатор для подключения к CSP. Пограничный маршрутизатор также служит шлюзом для межсайтовых подключений VPN.  
  
![Сторонний шлюз с BGP на границе сайта предприятия](../../media/Border-Gateway-Protocol-BGP/bgp_02.jpg)  
  
Пограничный маршрутизатор предприятия определяет внутренние локальные маршруты одним из указанных ниже способов.  
  
-   Пограничное устройство использует протокол BGP с внутренним маршрутизатором и определяет внутренние маршруты (в этом случае это 10.1.1.0/24).  
  
-   Пограничное устройство реализует протокол IGP и непосредственно участвует во внутренней маршрутизации.  
  
### <a name="bkmk_top3"></a>Несколько сайтов предприятия, подключения к CSP облако центра обработки данных  
В этой топологии представлено несколько сайтов предприятия, которые используют сторонние шлюзы для подключения к CSP. Сторонние пограничные устройства выступают в роли шлюзов для межсайтовых подключений VPN и в роли маршрутизаторов BGP.  
  
![Несколько сайтов предприятия, подключения к CSP облако центра обработки данных](../../media/Border-Gateway-Protocol-BGP/bgp_03.jpg)  
  
Пограничные маршрутизаторы клиента определяют внутренние локальные маршруты одним из указанных ниже способов.  
  
-   Пограничное устройство использует протокол BGP с внутренним маршрутизатором и определяет внутренние маршруты (в этом случае это 10.1.1.0/24).  
  
-   Пограничное устройство реализует протокол IGP и непосредственно участвует во внутренней маршрутизации.  
  
Каждый сайт предприятия узнает маршруты от другого сайта посредством прямого подключения eBGP.  
  
Каждый сайт предприятия получает сведения о маршрутах в размещенной сети напрямую и от другого сайта предприятия, а затем выбирает оптимальный маршрут на основе его стоимости.  
  
Если маршрутизатор BGP на сайте 1 предприятия не удается подключиться с маршрутизатором BGP 2 сайта предприятия, так как произошел сбой подключения, маршрутизатор BGP 1 сайта начинает динамически получать сведения о маршрутах к сети узла Enterprise 2 от маршрутизатора BGP CSP, а трафик — без проблем пересылаются из узла 1 на сайт 2 через маршрутизатор BGP Windows Server на CSP.  
  
### <a name="bkmk_top4"></a>Отдельные точки завершения для BGP и VPN  
В этой топологии представлено предприятие, в котором в качестве конечной точки BGP и конечной точки межсайтовых подключений VPN используются два разных маршрутизатора. Сеть сеть VPN прерывает для шлюза RAS Windows Server 2016 завершается внутренний маршрутизатор BGP. На стороне CSP подключений CSP завершает подключений VPN и BGP со шлюзом удаленного доступа. В такой конфигурации оборудование внутреннего стороннего маршрутизатора должно поддерживать повторное распространение маршрутов IGP в BGP, а также повторное распространение маршрутов BGP в IGP.  
  
![Отдельные точки завершения для BGP и VPN](../../media/Border-Gateway-Protocol-BGP/bgp_04.jpg)  
  
Внутренний маршрутизатор определяет маршруты предприятия одним из указанных ниже способов.  
  
-   BGP  
  
-   Протокол IGP, например OSPF или RIP  
  
-   Настройка статических маршрутов  
  
При использовании любого протокола IGP на сайте предприятия внутренний маршрутизатор должен повторно распространять маршруты IGP в BGP, а также повторно распространять маршруты BGP в IGP для обеспечения связи между виртуальными сетями CSP и локальными подсетями предприятия.  
  
С этим развертыванием шлюза RAS Enterprise имеет VPN-подключения сеть сеть со шлюзом CSP RAS, который предоставляет корпоративного шлюза RAS маршруты к шлюзу CSP. Затем внутренний маршрутизатор узнает этот маршрут к шлюзу CSP посредством iBGP корпоративного шлюза RAS. По этой причине внутренний маршрутизатор предприятия затем сможет установить сеанс пиринга с маршрутизатором BGP шлюза RAS CSP.  
  
С этого момента внутренний маршрутизатор предприятия и шлюз RAS CSP обмениваются информацией о маршрутизации. И маршрутизатор BGP RAS предприятия узнает маршруты CSP и маршрутах предприятия для физической маршрутизации пакетов между сетями.  
  
## <a name="bkmk_features"></a>Возможности BGP  
Ниже перечислены возможности маршрутизатора BGP шлюза RAS.  
  
**Маршрутизация BGP в качестве службы роли удаленного доступа**. Теперь вы можете установить **маршрутизации** службой роли из роли сервера удаленного доступа, не устанавливая **удаленного доступа (RAS)** службы роли, если вы хотите использовать удаленный доступ как маршрутизатор BGP по локальной сети.  Это уменьшает объем памяти маршрутизатора BGP и устанавливает только компоненты, необходимые для динамической маршрутизации BGP. Служба роли маршрутизации полезна при только для виртуальной Машины маршрутизатора BGP является обязательным, и не требуют использования DirectAccess или VPN. Кроме того с помощью удаленного доступа в качестве маршрутизатора локальной сети с использованием BGP позволяет динамической маршрутизации преимущества BGP во внутренней сети.  
  
**Статистика BGP (счетчики сообщений, счетчики маршрутов)**. Маршрутизатор BGP поддерживает отображение статистики по сообщениями и маршрутам, если это необходимо, с помощью команды **Get-BgpStatistics** среды Windows PowerShell.  
  
**Поддержка маршрутизации на основе множественных маршрутов равной стоимости (ECMP)**. Маршрутизатор BGP поддерживает ECMP, и в его таблице и стеке маршрутизации BGP может быть несколько маршрутов равной стоимости. Если маршрутизация ECMP включена, маршрутизатор BGP выбирает маршрут для передачи пакетов данных случайным образом.  
  
**Настройка значения HoldTime**. Маршрутизатор BGP поддерживает настройку значения HoldTimer в соответствии с требованиями сети. Этот таймер можно динамически изменять для обеспечения взаимодействия с устройствами сторонних производителей или для задания определенного времени ожидания для сеанса пиринга BGP.  
  
**Поддержка iBGP и eBGP**. Маршрутизатор BGP поддерживает пиринг iBGP и eBGP. Для его настройки необходимо назначить соответствующие номера ASN локальному и удаленному маршрутизаторам BGP. Во всех четырех топологиях развертывания BGP используется пиринг eBGP, а в четвертой топологии также применяется пиринг iBGP.  
  
**Взаимодействие с решениями сторонних производителей**. Маршрутизатор BGP основан на последней спецификации BGP версии 4 и был проверен на возможность взаимодействия с большинством основных устройств маршрутизации BGP сторонних производителей. Подробнее см .в документе RFC 4271 [Протокол BGP версии 4](https://tools.ietf.org/html/rfc4271).  
  
**Поддержка пиринга транспорта IPv4 и IPv6**. Маршрутизатор BGP поддерживает пиринг IPv4 и IPv6. Однако идентификатор BGP нужно настроить как IPv4-адрес маршрутизатора BGP. Для всех топологий развертывания маршрутизатора BGP можно использовать любой из двух типов пиринга (IPV4 или IPv6).  
  
**Возможность одноадресного получения и объявления маршрутов IPv4 и IPv6 (мультипротокольная информация сетевого уровня о доступности сети (NLRI))**. Независимо от используемого транспорта маршрутизатор BGP может обмениваться сведениями о маршрутах IPv4 и IPv6, если соответствующая возможность была объявлена другими маршрутизаторами BGP при создании сеанса. Чтобы настроить маршрутизацию IPv6, нужно включить параметр IPv6Routing и настроить локальный глобальный IPv6-адрес на уровне маршрутизатора.  
  
**Пиринг в смешанном и пассивном режимах**. Можно настроить сеансы пиринга BGP в либо в смешанном режиме - где маршрутизатор BGP выступает в качестве инициатор и отвечающее устройство — либо в пассивном режиме, в котором маршрутизатор BGP не инициирует пиринг, но отвечать на входящие запросы. Смешанный режим используется по умолчанию и рекомендуется для пиринга BGP. Это верно во всех случаях, кроме тех, когда нужно использовать пассивный режим в целях отладки или диагностики. Во всех топологиях развертывания маршрутизатора BGP пиринг в смешанном режиме необходим для обеспечения автоматического перезапуска в случае сбоев.  
  
**Возможность перезаписи атрибутов маршрутизатора**. С помощью политик маршрутизации BGP можно добавлять, изменять и удалять следующие атрибуты из входящих и исходящих объявлений маршрутов маршрутизатора BGP: Next-Hop, MED, Local-Pref и Community.  
  
**Фильтрация маршрутов**. Маршрутизатор BGP поддерживает фильтрацию входящих и исходящих объявлений маршрутов на основе различных атрибутов маршрутов, таких как Prefix, ASN-Range, Community и Next-Hop.  
  
**Клиент Рефлектора маршрутов (RR) и RR**. Маршрутизатор BGP может выступать как Рефлектора маршрутов и клиента Ресурса. Это полезно в сложные топологии, где RR можно упростить сети, формирующие RR кластеров.  
  
**Поддержка обновления маршрутов**. Маршрутизатор BGP поддерживает обновление маршрутов и по умолчанию объявляет эту возможность при пиринге. Он способен отправлять новый набор обновленных маршрутов при запросе одноранговым узлом посредством сообщения route-refresh, а также для отправки обновления маршрутов для обновления его таблицы маршрутизации в событиях, например изменения политики маршрутизации для однорангового узла. Это позволяет сценарий, изменение или обновление политик маршрутизации BGP в Windows Server 2016 без перезапуска пиринг.  
  
**Поддержка настройки статических маршрутов**. Статические маршруты и интерфейсы в маршрутизаторе BGP можно настроить с помощью команды **Add-BgpCustomRoute** среды Windows PowerShell. Настраиваемые статические маршруты могут быть префиксами или именами интерфейсов, из которых выбираются маршруты. Однако только маршруты с разрешаемыми следующими прыжками включаются в таблицы маршрутизации BGP и объявляются для одноранговых узлов.  
  
**Поддержка транзитной маршрутизации**. Маршрутизатор BGP поддерживает транзитную маршрутизацию для iBGP для подключений iBGP, iBGP – eBGP подключений, а также eBGP – eBGP подключений.  
  
**Маршрутизация гашение Flap**. Службы гашение Flap маршрута для маршрутизации BGP в Windows Server 2016 обеспечивает поддержку гашение flap маршрута. Например, при маршрут постоянно объявляется и списания, что делает ее маршрутизации нестабильной, можно настроить маршрутизатор BGP, назначьте вес отбрасывания маршрута и отслеживать ее надрез - и соответствующим образом отключить или отмену-отключать их при необходимости. Благодаря этому с обслуживанием таблицу маршрутизации стабильной и менее обработки маршрутизатора BGP.  
  
**Маршрутизация статистической обработки**. Метод агрегирования данных маршрута на маршрутизаторе BGP дает возможность настроить агрегированные маршруты, так и для замены более детализированные объявления маршрутов с маршрутами суммарных или статистических для одноранговых узлов. Это приводит к меньшее количество сообщений объявления маршрутов, передаваемых в сети.  
  
> [!NOTE]  
> В System Center шлюз RAS называется шлюз Windows Server.  
  

  
