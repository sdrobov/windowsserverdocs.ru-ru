---
title: Шаги по настройке лаборатории тестирования DirectAccess Cluster-NLB
description: Этот раздел является частью руководства по тестовой лаборатории. демонстрация DirectAccess в кластере с Windows NLB для Windows Server 2016
manager: brianlic
ms.prod: windows-server
ms.technology: networking-da
ms.topic: article
ms.assetid: e508d3ee-ffa6-463f-a3dd-9e35e745c005
ms.author: lizross
author: eross-msft
ms.openlocfilehash: c4f683cd9745bdb61ee95d89bcfc37622a4acf2c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853017"
---
# <a name="steps-for-configuring-the-directaccess-cluster-nlb-test-lab"></a>Шаги по настройке лаборатории тестирования DirectAccess Cluster-NLB

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Следующие шаги описывают настройку инфраструктуры удаленного доступа, настройку серверов и клиентов удаленного доступа и проверку подключения DirectAccess из подсетей Интернета и Хоменет.  
  
В этом руководстве по тестированию вы создадите кластер удаленного доступа с поддержкой балансировки сетевой нагрузки (NLB), выполнив следующие действия.  
  
-   [Шаг 1. Завершение настройки DirectAccess](STEP-1-Complete-the-DirectAccess-Configuration.md). Выполните все действия, описанные в [руководстве по тестовой лаборатории: демонстрация настройки отдельного сервера DirectAccess с использованием смешанных IPv4 и IPv6](https://go.microsoft.com/fwlink/p/?LinkId=237004).  
  
-   [Шаг 2. Настройка EDGE1](STEP-2-Configure-EDGE1.md). Настройте роль удаленного доступа в EDGE1 для балансировки нагрузки.  
  
-   [Шаг 3. Установка и настройка EDGE2](STEP-3-Install-and-Configure-EDGE2.md). EDGE2 выступает в качестве второго сервера удаленного доступа в кластере удаленного доступа.  
  
-   [Шаг 4. Создание кластера удаленного доступа с балансировкой сетевой нагрузки](STEP-4-Create-the-Network-Load-Balanced-Remote-Access-Cluster.md)— EDGE1 настраивается как первый сервер в кластере удаленного доступа. EDGE2 присоединяется к кластеру, и для кластера настроена балансировка сетевой нагрузки.  
  
-   [Шаг 5. Проверка подключения DirectAccess из Интернета и через кластер](STEP-5-Test-DirectAccess-Connectivity-from-the-Internet-and-Through-the-Cluster.md). После завершения настройки балансировки сетевой нагрузки и кластера можно проверить возможность подключения клиентов DirectAccess через кластер с балансировкой нагрузки.  
  
-   [Шаг 6. Проверка подключения клиента DirectAccess от устройства NAT](STEP-6-Test-DirectAccess-Client-Connectivity-from-Behind-a-NAT-Device.md). Переместите клиентский компьютер за пределами устройства NAT, чтобы имитировать возможность подключения клиентов DirectAccess через домашний маршрутизатор.  
  
-   [Шаг 7. Проверка подключения при возврате к корпоративной сети](STEP-7-Test-Connectivity-When-Returning-to-the-Corpnet.md). Убедитесь, что клиентский компьютер по-прежнему может получать доступ к корпоративным ресурсам при возврате к корпоративной сети.  
  
-   [Шаг 8. Создание моментального снимка конфигурации](da-cluster-nlb-s8-snapshot.md). После завершения лабораторной работы сделайте снимок работающего кластера балансировки сетевой нагрузки с удаленным доступом, чтобы можно было вернуться к нему позже, чтобы протестировать дополнительные сценарии.  
  


