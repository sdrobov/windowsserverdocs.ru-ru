---
title: Обзор брандмауэра центра обработки данных
description: В этом разделе можно использовать для изучения брандмауэр центра обработки данных, который является сетевого уровня с пятью кортежами (номера протокола, исходного и конечного портов, исходный и конечный IP-адреса), управляются и с отслеживанием состояния брандмауэра в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 67576533-206b-428a-956c-ed8c53218d9b
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 0c9b9fb5b0fb9aa09ed783b2b66a8ad370a627c3
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="datacenter-firewall-overview"></a>Обзор брандмауэра центра обработки данных

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Брандмауэр центра обработки данных — это новая служба, входящая в состав Windows Server 2016. Это сетевого уровня с пятью кортежами (протокол, номера начального и конечного портов, исходный и конечный IP-адреса), с отслеживанием состояния, мультитенантный брандмауэр. После развертывания и предоставляется как служба поставщиком услуг, администраторы клиента можно установить и настроить политики брандмауэра для защиты своих виртуальных сетей с нежелательного трафика из Интернета и интрасети.  
  
![Брандмауэр центра обработки данных сетевого стека](../../../media/Datacenter-Firewall-Overview/MultitenantFirewallOverview2.png)  
  
Администратор поставщика службы или администратором клиента можно управлять политик брандмауэра центра обработки данных посредством сетевого контроллера и Северный API-интерфейсы.  
  
Брандмауэр центра обработки данных обеспечивает следующие преимущества для поставщиков облачных служб:  
  
-   Это решение широкими возможностями масштабирования, управляемость и diagnosable брандмауэр на основе программного обеспечения, которое могут предлагаться клиентам  
  
-   Свободно перемещать виртуальные машины клиента на разных вычислительные узлы, не нарушая политик брандмауэра клиента  
  
    -   Развернуть в качестве узла агента виртуальный коммутатор порта брандмауэра  
  
    -   Виртуальные машины клиента получения политик, которые назначены их брандмауэра агент узла виртуальный коммутатор  
  
    -   Настройка правил брандмауэра производятся каждого порта виртуального коммутатора, независимо от адреса узла, виртуальной машины под управлением  
  
-   Обеспечивает защиту для клиента виртуальных машин, независимо от операционной системы клиента  
  
Брандмауэр центра обработки данных обеспечивает следующие преимущества для клиентов:  
  
-   Возможность определения правил брандмауэра для защиты сети Интернет рабочих нагрузок в виртуальных сетях  
  
-   Возможность определения правил брандмауэра для защиты трафика между виртуальными машинами на одной L2 виртуальной подсети также между виртуальными машинами на различных виртуальных подсетей L2  
  
-   Возможность определения правил брандмауэра для защиты и изоляции сетевого трафика между клиента локальной сети и их виртуальные сети поставщика услуг  
  

