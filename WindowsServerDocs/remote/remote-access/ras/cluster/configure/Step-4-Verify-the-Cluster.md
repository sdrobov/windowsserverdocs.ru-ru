---
title: Шаг 4. Проверка кластера
description: Этот раздел является частью руководств по развертыванию удаленного доступа в кластере в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f22dcf10-b453-4664-a9ef-e40e95c72f63
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 738b7d6aad1c9684ac1e12981213caaf3f745c2c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71367401"
---
# <a name="step-4-verify-the-cluster"></a>Шаг 4. Проверка кластера

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе описывается, как проверить правильность настройки развертывания кластера DirectAccess.  
  
### <a name="to-verify-access-to-internal-resources-through-the-cluster"></a>Проверка доступа к внутренним ресурсам через кластер  
  
1.  Подключите клиентский компьютер с DirectAccess к корпоративной сети и получите групповую политику.  
  
2.  Подключите клиентский компьютер к внешней сети и попытайтесь получить доступ к внутренним ресурсам.  
  
    Вам должны быть доступны все корпоративные ресурсы.  
  
3.  Протестируйте возможность подключения через каждый сервер в кластере, отключив или отключая внешнюю сеть, все серверы кластера, кроме одного. Попытайтесь получить доступ к корпоративным ресурсам на клиентском компьютере. Повторите тест на другом сервере кластера.  
  
    Вы должны иметь доступ ко всем корпоративным ресурсам через каждый сервер кластера.  
  


