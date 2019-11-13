---
title: Планирование удаленного доступа с проверкой подлинности OTP
description: Эта статья является частью руководств по развертыванию удаленного доступа с помощью проверки подлинности OTP в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 762bc463-eead-46ac-8b90-32355743c27c
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 69127ef86e1e14620f8cbb29322e930c6d921702
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404352"
---
# <a name="plan-remote-access-with-otp-authentication"></a>Планирование удаленного доступа с проверкой подлинности OTP

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

 Windows Server 2016 и Windows Server 2012 объединяют VPN DirectAccess и службы маршрутизации и удаленного доступа (RRAS) в одну роль удаленного доступа. В этом обзоре приводятся общие сведения о шагах настройки, необходимых для развертывания одного многосайтового развертывания Windows Server 2016 или Windows Server 2012 с удаленным доступом.  
  
  
-  Шаг 1. [развертывание одного сервера DirectAccess с дополнительными параметрами](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings). Этот шаг включает планирование инфраструктуры, необходимой для развертывания одного сервера. Он включает в себя планирование параметров сети и сервера, требования к сертификатам, параметры DNS, развертывание сервера сетевого расположения, серверы управления DirectAccess, параметры Active Directory и объекты групповая политика (GPO).  
  
-   [Шаг 2. Планирование развертывания сервера RADIUS](Step-2-Plan-the-RADIUS-Server-Deployment.md)  
  
-   [Шаг 3. Планирование развертывания сертификатов OTP](Step-3-Plan-OTP-Certificate-Deployment.md)  
  
-   [Шаг 4. Планирование OTP на сервере удаленного доступа](Step-4-Plan-for-OTP-on-the-Remote-Access-Server.md)  
  
После завершения этих этапов планирования см. раздел [Настройка удаленного доступа с использованием проверки подлинности OTP](https://technet.microsoft.com/windows-server-docs/networking/remote-access/ras/otp/configure/configure-ra-with-otp-authentication). Сведения о настройке многосайтового развертывания в качестве подтверждения концепции в лабораторной среде см. в разделе [руководство по тестированию: демонстрация DirectAccess с проверкой подлинности OTP и RSA SecurID](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/tlg-otp-securid/test-lab-guide-demonstrate-directaccess-with-otp-authentication-and-rsa-securid).  
  


