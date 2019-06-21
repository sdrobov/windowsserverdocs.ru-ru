---
title: ШАГ 7 тестового подключения при возврате к корпоративной сети
description: Этот раздел входит руководство по лаборатории тестирования — продемонстрировать DirectAccess в кластере с помощью Windows NLB для Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a7252d0-6db8-4a9d-98ee-75082ecd2929
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 477d11f0e6bf296c41fb7116a7aae43787df263c
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67283379"
---
# <a name="step-7-test-connectivity-when-returning-to-the-corpnet"></a>ШАГ 7 тестового подключения при возврате к корпоративной сети

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Многие ваши пользователи перемещаются между удаленных расположений и корпоративной сети, поэтому очень важно, что при возвращении к корпоративной сети, они смогут получать доступ к ресурсам без внесения какой-либо настройки изменяется. Удаленного доступа делает это возможным, поскольку клиент DirectAccess возвращается к корпоративной сети, при возможность создания подключений для сервера сетевых расположений. После успешного установления HTTPS-соединения для сервера сетевых расположений клиент DirectAccess отключает клиентскую конфигурацию DirectAccess и использует прямое подключение к корпоративной сети.  
  
### <a name="test-connectivity-on-client1"></a>Проверка подключения на CLIENT1  
  
1. Выключите компьютер CLIENT1, отключите CLIENT1 от подсети Homenet или виртуальный коммутатор и подключить его к подсети Corpnet или виртуального коммутатора. Включите на компьютере CLIENT1 и войдите в систему как CORP\User1.  
  
2. Откройте окно с повышенными привилегиями Windows PowerShell, введите **ipconfig/all**, и нажмите клавишу ВВОД. Вывод покажет, что CLIENT1 локальный IP-адрес, и это не active 6to4, Teredo или IP-HTTPS туннеля.  
  
3. Проверить возможность подключения к сетевой папке в APP2. На **запустить** введите<strong>\\\APP2\Files</strong>, и нажмите клавишу ВВОД. Можно открыть файл в этой папке.  
  


