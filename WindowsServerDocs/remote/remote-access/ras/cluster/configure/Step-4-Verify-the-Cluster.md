---
title: Шаг 4 проверка кластера
description: Этот раздел является частью руководства развертывание удаленного доступа в кластере в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f22dcf10-b453-4664-a9ef-e40e95c72f63
ms.author: pashort
author: shortpatti
ms.openlocfilehash: b449197265befb7caf7d8d3a5b56accf5c52aef9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821845"
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
  


