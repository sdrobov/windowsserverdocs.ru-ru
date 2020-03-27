---
title: Шаг 3. Проверка расширенного развертывания DirectAccess
description: Эта статья является частью руководств по развертыванию одного сервера DirectAccess с дополнительными параметрами для Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ae8bbff0-c981-4bc6-8df1-861621d0627f
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 6d8f9b5ecbc322de12cb00179a4ebb044fbd2baf
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80309094"
---
# <a name="step-3-verify-the-advanced-directaccess-deployment"></a>Шаг 3. Проверка расширенного развертывания DirectAccess

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе описывается, как проверить правильность настройки развертывания DirectAccess.  
  
### <a name="to-verify-access-to-internal-resources-through-directaccess"></a>Проверка доступа к внутренним ресурсам с помощью DirectAccess  
  
1.  Подключите клиентский компьютер DirectAccess к корпоративной сети и получите объект групповая политика.  
  
2.  Щелкните значок **Сетевые подключения** в области уведомлений, чтобы получить доступ к диспетчеру носителей DirectAccess.  
  
3.  Щелкните **подключение DirectAccess**, и вы увидите, что состояние **подключено локально**.  
  
4.  Подключите клиентский компьютер к внешней сети и попытайтесь получить доступ к внутренним ресурсам.  
  
    Вам должны быть доступны все корпоративные ресурсы.  
  
## <a name="previous-step"></a><a name="BKMK_Links"></a>Предыдущий шаг  
  
-   [Шаг 2. Настройка серверов DirectAccess](Step-2-Configuring-DirectAccess-Servers.md)  
  


