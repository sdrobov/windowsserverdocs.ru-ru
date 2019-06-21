---
title: Шаг 2 Планирование развертывания сервера RADIUS
description: Этот раздел является частью руководства развертывание удаленного доступа с проверкой подлинности OTP в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2d6ad863-02a5-49b0-9aff-d189e78b2b80
ms.author: pashort
author: shortpatti
ms.openlocfilehash: f74a83c3962c7accd76fbf07307216742ada863d
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280833"
---
# <a name="step-2-plan-the-radius-server-deployment"></a>Шаг 2 Планирование развертывания сервера RADIUS

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

После развертывания на одном сервере удаленного доступа, планирование для сервера проверки подлинности одноразового пароля (OTP).  
  
|Задача|Описание|  
|----|--------|  
|2.1. Планирование сервера RADIUS|Для сервера проверки подлинности OTP удаленного доступа в Windows Server 2016 и Windows Server 2012 поддерживает любой сервер с поддержкой RADIUS OTP, который поддерживает протокол проверки подлинности пароль (PAP).|  
  
## <a name="BKMK_1.1"></a>2.1. Планирование сервера RADIUS  
При планировании сервер RADIUS для проверки подлинности OTP, обратите внимание на следующее:  
  
-   Для большинства типов развертываний OTP агентом RADIUS необходимо настроить сервер удаленного доступа. Дополнительные сведения см. в документации поставщика OTP.  
  
-   Для всех развертываний OTP необходимо синхронизировать пользователей Active Directory с сервером RADIUS.  
  
-   RADIUS-сервер не требуется быть членом домена.  
  
-   При развертывании сервера RADIUS, можно настроить общий секрет и номер порта для RADIUS-трафика. Запомните или запишите эти сведения; они необходимы при настройке сервера удаленного доступа.  
  
Можно просмотреть руководство по лаборатории тестирования пример, предназначенной для настройки проверки подлинности OTP с сервером RSA SecurID в [руководство по лаборатории тестирования: Демонстрация DirectAccess с проверкой подлинности OTP и RSA SecurID](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/tlg-otp-securid/test-lab-guide-demonstrate-directaccess-with-otp-authentication-and-rsa-securid).  
  
  
  


