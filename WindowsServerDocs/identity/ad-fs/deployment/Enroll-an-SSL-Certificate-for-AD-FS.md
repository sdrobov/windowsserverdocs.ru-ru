---
ms.assetid: 3095e6a7-b562-4c6a-bf29-13b32c133cac
title: Регистрация SSL-сертификата для AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 6f7af40f23c3fa3bd0a31ecb74b11013133a4b32
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855437"
---
# <a name="enroll-an-ssl-certificate-for-ad-fs"></a>Регистрация SSL-сертификата для AD FS

Для службы федерации Active Directory (AD FS) \(AD FS\) требуется сертификат для безопасного уровня сокета \(проверка подлинности SSL\) сервера на каждом сервере федерации в ферме серверов федерации. Один и тот же сертификат можно использовать на каждом сервере федерации в ферме. Необходимо наличие самого сертификата, а также его закрытого ключа. Например, если сертификат и его закрытый ключ находятся в PFX-файле, то можно импортировать этот файл непосредственно в мастер настройки служб федерации Active Directory. Сертификат SSL должен содержать следующие данные.  
  
1.  Имя субъекта и альтернативное имя субъекта должны содержать имя службы федерации, например fs.contoso.com.  
  
2.  Альтернативное имя субъекта должно содержать значение **enterpriseregistration** , за которым следует имя участника-пользователя \(UPN\) суффикса вашей организации, например **enterpriseregistration.Corp.contoso.com**.  
  
    > [!WARNING]  
    > Укажите альтернативное имя субъекта, если вы планируете включить службу регистрации устройств \(DRS\) для Workplace Join.  
  
> [!IMPORTANT]  
> Если в вашей организации используется несколько суффиксов имени участника-пользователя и вы планируете включить DRS, SSL-сертификат должен содержать запись альтернативного имени субъекта для каждого суффикса.  
  
## <a name="see-also"></a>См. также
[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Рекомендации по развертыванию AD FS Windows Server 2012 R2](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[Развертывание фермы серверов федерации](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  
  

