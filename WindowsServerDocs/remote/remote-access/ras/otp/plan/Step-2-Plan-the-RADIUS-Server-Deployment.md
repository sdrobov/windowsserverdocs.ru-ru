---
title: Шаг 2. Планирование развертывания сервера RADIUS
description: Эта статья является частью руководств по развертыванию удаленного доступа с помощью проверки подлинности OTP в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2d6ad863-02a5-49b0-9aff-d189e78b2b80
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 44f8514bd046d2c5f526e85309af430383bf1ec1
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80313571"
---
# <a name="step-2-plan-the-radius-server-deployment"></a>Шаг 2. Планирование развертывания сервера RADIUS

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

После развертывания одного сервера удаленного доступа запланируйте сервер проверки подлинности одноразового пароля (OTP).  
  
|Задача|Описание|  
|----|--------|  
|2,1. Планирование сервера RADIUS|Для сервера проверки подлинности OTP удаленный доступ в Windows Server 2016 и Windows Server 2012 поддерживает любой сервер OTP с поддержкой RADIUS, поддерживающий протокол проверки пароля (PAP).|  
  
## <a name="21-plan-the-radius-server"></a><a name="BKMK_1.1"></a>2,1. Планирование сервера RADIUS  
При планировании RADIUS-сервера для проверки подлинности OTP Обратите внимание на следующее:  
  
-   Для большинства типов развертываний OTP необходимо настроить сервер удаленного доступа в качестве агента RADIUS. Дополнительные сведения см. в документации по поставщику OTP.  
  
-   Для всех развертываний OTP необходимо синхронизировать Active Directory пользователей с сервером RADIUS.  
  
-   Сервер RADIUS не обязательно должен быть членом домена.  
  
-   При развертывании сервера RADIUS настраивается общий секрет и номер порта для трафика RADIUS. Запишите эти сведения. они необходимы при настройке сервера удаленного доступа.  
  
Пример лабораторного руководства по тестированию, который настраивает проверку подлинности OTP с помощью сервера RSA SecurID, можно просмотреть в разделе [руководство по тестированию: демонстрация DirectAccess с проверкой подлинности OTP и RSA SecurID](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/tlg-otp-securid/test-lab-guide-demonstrate-directaccess-with-otp-authentication-and-rsa-securid).  
  
  
  


