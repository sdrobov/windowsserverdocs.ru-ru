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
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 51ce3fa1a72420f7272141bb5361b20360b7000c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404905"
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
  
## <a name="BKMK_Links"></a>Предыдущий шаг  
  
-   [Шаг 2. Настройка серверов DirectAccess](Step-2-Configuring-DirectAccess-Servers.md)  
  


