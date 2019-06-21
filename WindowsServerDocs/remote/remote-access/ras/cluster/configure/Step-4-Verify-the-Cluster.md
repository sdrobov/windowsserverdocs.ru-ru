---
title: Шаг 4 проверка кластера
description: Этот раздел является частью руководства развертывание удаленного доступа в кластере в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f22dcf10-b453-4664-a9ef-e40e95c72f63
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 424c4f881c168ea691dd51cd2d86a4a234c41075
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67282981"
---
# <a name="step-4-verify-the-cluster"></a>Шаг 4 проверка кластера

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

В этом разделе описывается убедитесь, что вы правильно настроили развертывание кластера DirectAccess.  
  
### <a name="to-verify-access-to-internal-resources-through-the-cluster"></a>Чтобы проверить доступ к внутренним ресурсам через кластер  
  
1.  Подключите клиентский компьютер с DirectAccess к корпоративной сети и получите групповую политику.  
  
2.  Подключите клиентский компьютер к внешней сети и попытайтесь получить доступ к внутренним ресурсам.  
  
    Вам должны быть доступны все корпоративные ресурсы.  
  
3.  Проверка подключения через каждый сервер в кластере, отключение или отсоединение из внешней сети, все, кроме одного из серверов кластера. На клиентском компьютере попытка получить доступ к корпоративным ресурсам. Повторите тест на сервере другой кластер.  
  
    Можно получить доступ ко всем корпоративным ресурсам через каждый сервер кластера.  
  


