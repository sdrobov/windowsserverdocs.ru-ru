---
title: Шаги по настройке лаборатории тестирования DirectAccess Cluster-NLB
description: Этот раздел входит руководство по лаборатории тестирования — продемонстрировать DirectAccess в кластере с помощью Windows NLB для Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e508d3ee-ffa6-463f-a3dd-9e35e745c005
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 3a243debf79d2c9d12de511153b74f23c5a44cce
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59880745"
---
# <a name="steps-for-configuring-the-directaccess-cluster-nlb-test-lab"></a>Шаги по настройке лаборатории тестирования DirectAccess Cluster-NLB

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Ниже описывается настройка инфраструктуры удаленного доступа, настроить серверы удаленного доступа и клиенты и проверка подключения DirectAccess из Интернета и Homenet подсетей.  
  
В этом тестовом руководстве вы создадите сетевой балансировки нагрузки (NLB) кластером с поддержкой удаленного доступа, выполнив следующие действия:  
  
-   [Шаг 1 завершение настройки DirectAccess](STEP-1-Complete-the-DirectAccess-Configuration.md). Выполните все шаги в [руководство по лаборатории тестирования: Демонстрации настройки отдельного сервера DirectAccess в смешанной IPv4 и IPv6](https://go.microsoft.com/fwlink/p/?LinkId=237004).  
  
-   [ШАГ 2. Настройка EDGE1](STEP-2-Configure-EDGE1.md). Настройка роли удаленного доступа на EDGE1 для балансировки нагрузки.  
  
-   [ШАГ 3. Установка и настройка EDGE2](STEP-3-Install-and-Configure-EDGE2.md). EDGE2 выступает в качестве второго сервера удаленного доступа в кластере удаленного доступа.  
  
-   [ШАГ 4. Создание кластера удаленного доступа с балансировкой нагрузки сети](STEP-4-Create-the-Network-Load-Balanced-Remote-Access-Cluster.md)-EDGE1 настроен как первый сервер в кластере удаленного доступа. EDGE2 присоединяется к кластеру и балансировки сетевой Нагрузки настроен для кластера.  
  
-   [ШАГ 5. Проверка подключения DirectAccess через Интернет и через кластер](STEP-5-Test-DirectAccess-Connectivity-from-the-Internet-and-Through-the-Cluster.md). После завершения настройки балансировки сетевой Нагрузки и кластера можно проверить подключения клиентов DirectAccess через кластер с балансировкой нагрузки.  
  
-   [ШАГ 6. Проверка подключения клиента DirectAccess из-за устройства NAT](STEP-6-Test-DirectAccess-Client-Connectivity-from-Behind-a-NAT-Device.md). Переместите клиентский компьютер за устройством NAT для имитации тестирования подключения клиентов DirectAccess из-за пределов домашний маршрутизатор.  
  
-   [ШАГ 7. Проверка подключения, при возврате к корпоративной сети](STEP-7-Test-Connectivity-When-Returning-to-the-Corpnet.md). Убедитесь, что клиентский компьютер может по-прежнему доступ к корпоративным ресурсам при возврате к корпоративной сети.  
  
-   [ШАГ 8. Сделайте снимок конфигурации,](da-cluster-nlb-s8-snapshot.md). После завершения лаборатории тестирования, создание снимка работающий кластер балансировки сетевой Нагрузки для удаленного доступа, который позволит вернуться к нему позже для проверки дополнительных сценариев.  
  


