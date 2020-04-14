---
ms.assetid: 222e9f93-7c41-4527-8a98-8f7fbc7a58af
title: Развертывание прокси-серверов федерации
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 04837c8b38f1f6cdf048f7d8744d9cd0f61ebb0d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855457"
---
# <a name="deploying-federation-server-proxies"></a>Развертывание прокси-серверов федерации

В службы федерации Active Directory (AD FS) \(AD FS\) в Windows Server 2012 R2 роль прокси-сервера федерации обрабатывается новой службой роли удаленного доступа, именуемой прокси-сервером веб приложения. Чтобы обеспечить доступность AD FS для доступа извне корпоративной сети, которая была предназначена для развертывания прокси-сервера федерации в устаревших версиях AD FS, таких как AD FS 2,0 и AD FS в Windows Server 2012, можно развернуть один или несколько прокси веб-приложений для AD FS в Windows Server 2012 R2.  
  
В контексте AD FS прокси веб-приложения функционирует в качестве прокси-сервера AD FS Федерации. Кроме того, прокси-сервер веб-приложения предоставляет функции обратного прокси-сервера для веб-приложений в корпоративной сети, что делает их доступными для пользователей с любых устройств из-за пределов корпоративной сети. Дополнительные сведения о службе роли прокси веб-приложения см. в разделе "Обзор прокси-сервера веб-приложения".  
  
При планировании развертывания прокси-сервера веб-приложения можно использовать сведения из следующих разделов.  
  
-   [Планирование инфраструктуры прокси веб-приложений (WAP)](https://technet.microsoft.com/library/dn383648.aspx)  
  
-   [Планирование сервера прокси веб-приложения](https://technet.microsoft.com/library/dn383647.aspx)  
  
При развертывании прокси-сервера веб-приложения можно следовать процедурам в следующих разделах.  
  
-   [Настройка инфраструктуры прокси веб-приложения](https://technet.microsoft.com/library/dn383644.aspx)  
  
-   [Установка и настройка сервера прокси веб-приложения](https://technet.microsoft.com/library/dn383662.aspx)  
  
 
## <a name="see-also"></a>См. также 

[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Рекомендации по развертыванию AD FS Windows Server 2012 R2](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[Развертывание фермы серверов федерации](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  

