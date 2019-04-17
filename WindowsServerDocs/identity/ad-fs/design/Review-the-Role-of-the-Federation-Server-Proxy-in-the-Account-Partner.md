---
ms.assetid: 1b3a03c0-5558-4177-9b2f-e9d6ce3271cd
title: "Сведения о роли прокси-сервера федерации в организации партнера по учетной записи"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: d2b60ce593c2ca7eb902595ee6a42850cb7605d9
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="review-the-role-of-the-federation-server-proxy-in-the-account-partner"></a>Сведения о роли прокси-сервера федерации в организации партнера по учетной записи

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Основная роль прокси-сервера федерации в сети периметра организации партнера по учетной записи в \(AD FS\) служб федерации Active Directory — сбор учетных данных аутентификации с клиентского компьютера, на которые входит через Интернет и передать эти учетные данные на сервер федерации, который находится в корпоративной сети организации партнера по учетным записям. Учетная запись для клиентского компьютера хранится в хранилище атрибутов партнера по учетным записям.  
  
Прокси-сервер федерации также может функционировать в одной или нескольких из следующих ролей, в зависимости от того, как настроить его в соответствии с потребностями организации партнера по учетным записям:  
  
-   Ретрансляция токенов безопасности — сервер федерации выдает токен безопасности прокси-сервер федерации, который затем передает токен клиентскому компьютеру. Токен безопасности служит для предоставления доступа к клиентскому компьютеру для определенной проверяющей стороны.  
  
-   Сбор учетных данных — прокси-сервера федерации использует формы \(clientlogon.aspx\) Web входа по умолчанию клиента для сбора учетных данных через проверку подлинности на основе forms\ на основе password\. Тем не менее, вы эту форму можно настроить для использования других типов проверки подлинности, такие как проверка подлинности клиента \(SSL\) протокола SSL. Дополнительные сведения о настройке этой страницы см. в разделе Настройка входа в систему страниц и домашней области обнаружения \ ([http:///\/go.microsoft.com\/fwlink\/? LinkId\ = 104275](https://go.microsoft.com/fwlink/?LinkId=104275)\). Прокси-сервер федерации не принимает учетные данные посредством интегрированной аутентификации Windows.  
  
Итак, прокси-сервера федерации в партнера по учетным записям выступает в качестве прокси-сервера для операций входа клиентов на сервер федерации, который находится в корпоративной сети. Прокси-сервер федерации также обеспечивает распространение маркеров безопасности для Интернет-клиентов, предназначенных для проверяющих сторон.  
  
> [!CAUTION]  
> Предоставление доступа к прокси-сервера федерации в экстрасети партнера по учетным записям будет входа клиента веб-формы доступны любым пользователем, имеющим Интернет к. Это можно сделать организации уязвимой к некоторым атакам на основе password\, такие как атаки перебором по словарю или атаки методом подбора, могут привести к блокировке учетных записей пользователей, хранящихся в корпоративных \(AD DS\) доменных служб Active Directory.  
  

## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)