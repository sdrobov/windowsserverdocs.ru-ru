---
ms.assetid: 3095e6a7-b562-4c6a-bf29-13b32c133cac
title: "Регистрация SSL-сертификата для AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 12f544ad0d037c4ae7a9789238186b7ded311bdf
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="enroll-an-ssl-certificate-for-ad-fs"></a>Регистрация SSL-сертификата для AD FS

>Область применения: Windows Server 2016, Windows Server 2012 R2

Active Directory службы федерации \(AD FS\) требуется сертификат для проверки подлинности сервера \(SSL\) протокола SSL для каждого сервера федерации в ферме серверов федерации. Можно использовать тот же сертификат для каждого сервера федерации в ферме. Необходимо иметь сертификат и его закрытый ключ. Например если у вас есть сертификат и его закрытый ключ в PFX-файл, можно импортировать файл непосредственно в мастер настройки служб Active Directory федерации. Этот SSL-сертификат должен содержать следующее:  
  
1.  Имя субъекта и альтернативного имени субъекта должно содержать имя службы федерации, например fs.contoso.com.  
  
2.  Альтернативное имя субъекта должно содержать значение **enterpriseregistration**, является за которым следует суффикс имени участника-пользователя \(UPN\) для организации, например, **enterpriseregistration.corp.contoso.com**.  
  
    > [!WARNING]  
    > Укажите альтернативное имя субъекта, если вы планируете включить \(DRS\) службы регистрации устройств для присоединения к рабочему месту.  
  
> [!IMPORTANT]  
> Если вы планируете включить DRS вашей организации используется несколько суффиксов имени участника-пользователя, SSL-сертификат должен содержать запись альтернативного имени субъекта для каждого суффикса.  
  
## <a name="see-also"></a>См. также:
[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Руководство по развертыванию Windows Server 2012 R2 AD FS](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[Развертывание фермы серверов федерации](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  
  

