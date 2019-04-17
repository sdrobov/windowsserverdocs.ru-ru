---
ms.assetid: cc2834ec-8f66-4209-aba3-402d710cd1bd
title: "Расположение контроллера домена"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 198453099336954ee44447a79fec267266caa99a
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="domain-controller-location"></a>Расположение контроллера домена

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Клиенты используют доменных имен (DNS) для поиска контроллеров домена до завершения операции, такие как обработка запросов на вход или поиск в каталоге для опубликованных ресурсов. Контроллеры домена регистрируют разнообразные записей в DNS, чтобы помочь клиентам, и их размещении других компьютеров. Эти записи вместе называются записей локатора.  
  
Чтобы найти контроллеры домена и выполнять задачи, такие как репликация, контроллеров домена также использовать DNS. Процесс, в котором контроллеры домена найти другие контроллеры домена совпадает с процессом, с помощью которого клиенты находить контроллеры домена.  
  


