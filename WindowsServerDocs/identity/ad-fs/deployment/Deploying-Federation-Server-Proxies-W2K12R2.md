---
ms.assetid: 222e9f93-7c41-4527-8a98-8f7fbc7a58af
title: "Развертывание прокси-сервера федерации"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: dc49d8f4b656fdbb92083aa3c60bc4ce81091e9b
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="deploying-federation-server-proxies"></a>Развертывание прокси-сервера федерации

>Область применения: Windows Server 2016, Windows Server 2012 R2

В \(AD FS\) служб федерации Active Directory в Windows Server 2012 R2 роль прокси-сервера федерации выполняет новая служба роли удаленного доступа с именем прокси веб-приложения. Чтобы включить AD FS доступ из-за пределами корпоративной сети, которая является целью развертывания прокси-сервера федерации в устаревших версиях Служб федерации Active Directory, таких как AD FS 2.0 и AD FS в Windows Server 2012, можно развернуть один или несколько приложений прокси для AD FS в Windows Server 2012 R2.  
  
В контексте AD FS веб-приложения прокси работает в качестве прокси-сервера федерации AD FS. Кроме того прокси веб-приложения предоставляет функции обратного прокси-сервера для веб-приложений в корпоративной сети включить пользователей с любого устройства для доступа к ним из за пределами корпоративной сети. Дополнительные сведения о службе роли прокси веб-приложения. в разделе Обзор прокси-сервера веб-приложения.  
  
Для планирования развертывания прокси-сервера веб-приложения, можно просмотреть сведения в следующих разделах:  
  
-   [Планирование инфраструктуры прокси-сервера приложений Web (WAP)](https://technet.microsoft.com/library/dn383648.aspx)  
  
-   [Планирование сервера прокси-сервера веб-приложений](https://technet.microsoft.com/library/dn383647.aspx)  
  
Для развертывания прокси-сервера веб-приложения можно следовать процедурам в следующих разделах:  
  
-   [Настройка инфраструктуры прокси-сервера веб-приложений](https://technet.microsoft.com/library/dn383644.aspx)  
  
-   [Установка и настройка сервера прокси-сервера веб-приложений](https://technet.microsoft.com/library/dn383662.aspx)  
  
 
## <a name="see-also"></a>См. также: 

[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Руководство по развертыванию Windows Server 2012 R2 AD FS](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[Развертывание фермы серверов федерации](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  

