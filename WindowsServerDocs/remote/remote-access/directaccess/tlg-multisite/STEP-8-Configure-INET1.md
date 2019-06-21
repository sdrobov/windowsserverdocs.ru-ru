---
title: ШАГ 8 Настройка INET1
description: Этот раздел входит руководство по лаборатории тестирования — продемонстрировать DirectAccess многосайтового развертывания для Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 693acb5c-dffc-4484-8286-163bb67724c9
ms.author: coreyp
author: coreyp-at-msft
ms.openlocfilehash: d6967b975b3a950c90de465872832d623755a494
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67281417"
---
# <a name="step-8-configure-inet1"></a>ШАГ 8. Настройка INET1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Чтобы предоставить клиентским компьютерам подключаться к серверам удаленного доступа через Интернет, необходимо настроить записи DNS для 2-EDGE1 на INET1.  
  
### <a name="to-create-the-2-edge1-dns-entry"></a>Чтобы создать запись DNS 2 EDGE1  
  
1.  На **запустить** введите**dnsmgmt.msc**, и нажмите клавишу ВВОД.  
  
2.  В дереве консоли откройте **зоны прямого просмотра**, нажмите кнопку **contoso.com**, щелкните правой кнопкой мыши **contoso.com**, а затем нажмите кнопку **новый узел (A или AAAA)** .  
  
3.  В **имя**, тип **2 EDGE1**. В **IP-адрес**, тип **131.107.0.20**. Щелкните **Добавить узел**, после чего нажмите **OK**, а затем — **Готово**.  
  


