---
title: Шаг 4. Проверка кластера
description: Этот раздел является частью руководств по развертыванию удаленного доступа в кластере в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: f22dcf10-b453-4664-a9ef-e40e95c72f63
ms.author: lizross
author: eross-msft
ms.openlocfilehash: c31db158856eb3c3881a36c29e40d1227116201f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855267"
---
# <a name="step-4-verify-the-cluster"></a>Шаг 4. Проверка кластера

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе описывается, как проверить правильность настройки развертывания кластера DirectAccess.  
  
### <a name="to-verify-access-to-internal-resources-through-the-cluster"></a>Проверка доступа к внутренним ресурсам через кластер  
  
1.  Подключите клиентский компьютер с DirectAccess к корпоративной сети и получите групповую политику.  
  
2.  Подключите клиентский компьютер к внешней сети и попытайтесь получить доступ к внутренним ресурсам.  
  
    Вам должны быть доступны все корпоративные ресурсы.  
  
3.  Протестируйте возможность подключения через каждый сервер в кластере, отключив или отключая внешнюю сеть, все серверы кластера, кроме одного. Попытайтесь получить доступ к корпоративным ресурсам на клиентском компьютере. Повторите тест на другом сервере кластера.  
  
    Вы должны иметь доступ ко всем корпоративным ресурсам через каждый сервер кластера.  
  


