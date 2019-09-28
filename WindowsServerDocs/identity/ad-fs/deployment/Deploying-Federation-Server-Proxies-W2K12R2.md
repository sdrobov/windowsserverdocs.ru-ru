---
ms.assetid: 222e9f93-7c41-4527-8a98-8f7fbc7a58af
title: Развертывание прокси-серверов федерации
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 34d2a15d5ad4f2563beffbce6ae5e729cf72c3ab
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359684"
---
# <a name="deploying-federation-server-proxies"></a>Развертывание прокси-серверов федерации

В службы федерации Active Directory (AD FS) \(AD FS @ no__t-1 в Windows Server 2012 R2 роль прокси-сервера федерации обрабатывается новой службой роли удаленного доступа, именуемой прокси-сервером веб приложения. Чтобы обеспечить доступность AD FS для доступа извне корпоративной сети, которая была предназначена для развертывания прокси-сервера федерации в устаревших версиях AD FS, таких как AD FS 2,0 и AD FS в Windows Server 2012, можно развернуть один или несколько прокси-приложений для D FS в Windows Server 2012 R2.  
  
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
  

