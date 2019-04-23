---
title: ШАГ 8 Настройка INET1
description: Этот раздел входит руководство по лаборатории тестирования — продемонстрировать DirectAccess многосайтового развертывания для Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 693acb5c-dffc-4484-8286-163bb67724c9
ms.author: coreyp
author: coreyp-at-msft
ms.openlocfilehash: 707591604a1d030b3abba9395081d2c2e4b7fb1c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59838815"
---
# <a name="step-8-configure-inet1"></a>ШАГ 8. Настройка INET1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Чтобы предоставить клиентским компьютерам подключаться к серверам удаленного доступа через Интернет, необходимо настроить записи DNS для 2-EDGE1 на INET1.  
  
### <a name="to-create-the-2-edge1-dns-entry"></a>Чтобы создать запись DNS 2 EDGE1  
  
1.  На **запустить** введите**dnsmgmt.msc**, и нажмите клавишу ВВОД.  
  
2.  В дереве консоли откройте **зоны прямого просмотра**, нажмите кнопку **contoso.com**, щелкните правой кнопкой мыши **contoso.com**, а затем нажмите кнопку **новый узел (A или AAAA)**.  
  
3.  В **имя**, тип **2 EDGE1**. В **IP-адрес**, тип **131.107.0.20**. Щелкните **Добавить узел**, после чего нажмите **OK**, а затем — **Готово**.  
  


