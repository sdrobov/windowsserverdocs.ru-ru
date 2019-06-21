---
title: Планирование удаленного доступа с проверкой подлинности OTP
description: Этот раздел является частью руководства развертывание удаленного доступа с проверкой подлинности OTP в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 762bc463-eead-46ac-8b90-32355743c27c
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 328e092dff23495203ee21fccbace1f7f36918d2
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280814"
---
# <a name="plan-remote-access-with-otp-authentication"></a>Планирование удаленного доступа с проверкой подлинности OTP

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

 Windows Server 2016 и Windows Server 2012 объединить в единую роль удаленного доступа DirectAccess и маршрутизации и удаленного доступа (RRAS) VPN. Данный обзор представляет введение в шаги настройки, необходимые для развертывания одного Windows Server 2016 или удаленного доступа Windows Server 2012 многосайтового развертывания.  
  
  
-  Шаг 1. [Развертывание одиночного сервера DirectAccess с расширенными параметрами](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings). Этот этап включает планирование инфраструктуры, необходимой для развертывания одного сервера. Он включает в себя Планирование сети и параметры сервера, требования к сертификатам, параметры DNS, развертывание сервера сетевых расположений, серверы управления DirectAccess, параметры Active Directory и объектов групповой политики (GPO).  
  
-   [Шаг 2. Планирование развертывания сервера RADIUS](Step-2-Plan-the-RADIUS-Server-Deployment.md)  
  
-   [Шаг 3. Планирование развертывания сертификата OTP](Step-3-Plan-OTP-Certificate-Deployment.md)  
  
-   [Шаг 4. Планирование OTP на сервере удаленного доступа](Step-4-Plan-for-OTP-on-the-Remote-Access-Server.md)  
  
После завершения описанных этапов планирования, см. в разделе [Настройка удаленного доступа с проверкой подлинности OTP](https://technet.microsoft.com/windows-server-docs/networking/remote-access/ras/otp/configure/configure-ra-with-otp-authentication). Сведения о настройке многосайтового развертывания подтверждения концепции в лабораторной среде, см. в разделе [руководство по лаборатории тестирования: Демонстрация DirectAccess с проверкой подлинности OTP и RSA SecurID](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/tlg-otp-securid/test-lab-guide-demonstrate-directaccess-with-otp-authentication-and-rsa-securid).  
  


