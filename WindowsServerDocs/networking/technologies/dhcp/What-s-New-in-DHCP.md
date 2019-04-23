---
title: Новые возможности DHCP
description: Здесь представлен обзор новых функций для конфигурации протокола DHCP (Dynamic Host) в Windows Server 2016.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-dhcp
ms.topic: get-started-article
ms.assetid: c6f36998-5b64-45d1-b1f0-0f0d6604dbe3
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 73cc5134f7af5063c912ad578fa7d660b3194aa1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59840235"
---
# <a name="whats-new-in-dhcp"></a>Новые возможности DHCP

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе описываются возможности конфигурации протокола DHCP (Dynamic Host), которые являются новыми или измененными в Windows Server 2016.
  
Протокол DHCP является стандартом Internet Engineering Task Force (IETF), которая позволяет снизить административную нагрузку и упрощения настройки узлов по протоколу TCP/IP\-сети, например частной интрасети. С использованием службы DHCP-сервера процесс настройки протокола TCP/IP на DHCP-клиентах происходит автоматически.

В следующих разделах сведения о новых возможностях и изменениях в функциональных возможностях для DHCP.

## <a name="dhcp-subnet-selection-options"></a>Параметры выбора подсети DHCP

Протокол DHCP, теперь поддерживает параметры 118 и 82 \(подзапроса параметр 5\). Эти параметры можно использовать прокси-сервер DHCP-клиентов и агентов ретрансляции для запроса IP-адрес для конкретной подсети, а также из определенного диапазона IP-адресов и область.


При использовании агента DHCP-ретрансляции, который настроен с параметром DHCP 82 sub\-вариант 5, агент ретрансляции может запросить аренду IP-адреса для DHCP-клиентов из определенного диапазона IP-адресов.

Дополнительные сведения см. в разделе [параметры Выбор подсети DHCP](dhcp-subnet-options.md).

## <a name="new-logging-events-for-dns-registration-failures-by-the-dhcp-server"></a>Новые события ведения журнала для ошибки при регистрации DNS, DHCP-сервер

DHCP теперь включает ведение журнала событий в тех случаях, в какие DHCP Сбой регистрации записей DNS сервера на DNS-сервере.

Дополнительные сведения см. в разделе [события ведения журнала DHCP-сервера для регистрации записи DNS](dhcp-dns-events.md).

## <a name="dhcp-nap-is-not-supported-in-windows-server-2016"></a>DHCP NAP не поддерживается в Windows Server 2016

Защита доступа к сети \(NAP\) является устаревшим в Windows Server 2012 R2 и в Windows Server 2016 роли DHCP-сервера больше не поддерживает NAP. Дополнительные сведения см. в разделе [Features Removed or Deprecated in Windows Server 2012 R2](https://technet.microsoft.com/library/dn303411.aspx).  
  
Поддержка защиты доступа к сети была введена в роль DHCP-сервера с помощью Windows Server 2008 и поддерживается в Windows клиентских и серверных операционных систем до Windows 10 и Windows Server 2016. В следующей таблице перечислены поддержка защиты доступа к сети в Windows Server.  
  
|Операционная система|Поддержка NAP|  
|--------------------|---------------|  
| Windows Server 2008 |Поддерживается|  
| Windows Server 2008 R2 |Поддерживается|  
| Windows Server 2012 |Поддерживается|  
| Windows Server 2012 R2 |Поддерживается|  
| Windows Server 2016|Не поддерживается.|  
  
При развертывании защиты доступа к сети DHCP-сервер под управлением операционной системы, которая поддерживает NAP может функционировать в качестве точки NAP для метода принудительного применения NAP DHCP. Дополнительные сведения о DHCP в NAP, см. в разделе [контрольный список: Реализация DHCP Enforcement Design](https://technet.microsoft.com/library/dd314186.aspx).  
  
В Windows Server 2016, DHCP-серверы не применять политики защиты доступа к сети и DHCP-области не может быть NAP\-включена. DHCP клиентских компьютеров, которые также являются клиенты NAP отправки состояния работоспособности \(SoH\) с запросом DHCP. Если DHCP-сервер работает под управлением Windows Server 2016, эти запросы обрабатываются в том случае, так как при наличии SoH. DHCP-сервер предоставляет клиенту обычный аренды DHCP. 

Если серверы, работающих под управлением Windows Server 2016 RADIUS-прокси, которые пересылают запросы проверки подлинности сервера политики сети \(NPS\) с поддержкой защиты доступа к сети, эти клиенты NAP вычисляются на сервере политики сети как NAP не\-, поддержка и Произошел сбой обработки защиты доступа к сети.
  
## <a name="see-also"></a>См. также  
  
-   [Dynamic Host Configuration Protocol (DHCP)](Dynamic-Host-Configuration-Protocol--DHCP-.md)  
  

