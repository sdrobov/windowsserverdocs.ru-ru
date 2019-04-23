---
title: Шаг 3 Проверка развертывания
description: Этот раздел является частью руководства клиенты DirectAccess управление удаленно в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a78a078-d2e7-4cbd-b8d5-20cfb6d1524b
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 89b9e53b7321ebeddda50a448829ad73395eeed0
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59835615"
---
# <a name="step-3-verify-the-deployment"></a>Шаг 3 Проверка развертывания

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

В этом разделе описывается убедитесь, что вы правильно настроили развертывания для удаленного управления клиентами DirectAccess.  
  
### <a name="to-verify-proper-deployment"></a>Для проверки правильного развертывания  
  
1.  Подключение компьютера клиента DirectAccess к корпоративной сети и получить объект групповой политики.  
  
2.  На клиентском компьютере, нажмите кнопку **сетевых подключений** значок в области уведомлений, чтобы получить доступ к DirectAccess, Media Manager.  
  
3.  Нажмите кнопку **подключения DirectAccess**, и вы увидите, что находится в состоянии **локально подключенных**.  
  
4.  Удаление компьютера из корпоративной сети и подключить его к общедоступной сети.  
  
5.  В командной строке введите **nltest/dsgetdc: [полное доменное имя]**. Эта команда проверит, что корпоративной сети доступен клиенту. Если контроллер домена недоступен, сообщение об ошибке для отображения отчетов, домен не существует: ERROR_NO_SUCH_DOMAIN.  
  


