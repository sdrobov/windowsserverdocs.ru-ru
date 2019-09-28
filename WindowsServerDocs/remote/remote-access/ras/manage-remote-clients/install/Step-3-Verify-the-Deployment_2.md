---
title: Шаг 3. Проверка развертывания
description: Этот раздел является частью руководств по удаленному управлению клиентами DirectAccess в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a78a078-d2e7-4cbd-b8d5-20cfb6d1524b
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 81ac8bf7321df915330d8d706fa5ba3912b8f54c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71367293"
---
# <a name="step-3-verify-the-deployment"></a>Шаг 3. Проверка развертывания

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе описывается, как проверить правильность настройки развертывания для удаленного управления клиентами DirectAccess.  
  
### <a name="to-verify-proper-deployment"></a>Проверка правильности развертывания  
  
1.  Подключите клиентский компьютер DirectAccess к корпоративной сети и получите объект групповая политика.  
  
2.  На клиентском компьютере щелкните значок " **Сетевые подключения** " в области уведомлений, чтобы получить доступ к диспетчеру носителей DirectAccess.  
  
3.  Щелкните **подключение DirectAccess**, и вы увидите, что состояние **подключено локально**.  
  
4.  Удалите компьютер из корпоративной сети и подключите его к общедоступной сети.  
  
5.  В командной строке введите команду **nltest/dsgetdc: [полное доменное имя]** . Эта команда проверит доступность корпоративной сети для клиента. Если контроллер домена недоступен, в следующем сообщении об ошибке Отобразится сообщение о том, что домен не существует: ERROR_NO_SUCH_DOMAIN.  
  


