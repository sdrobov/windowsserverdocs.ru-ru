---
ms.assetid: 3095e6a7-b562-4c6a-bf29-13b32c133cac
title: Регистрация SSL-сертификата для AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: efa7c7aee848a5bbb68d3ce7140e135d37c2161d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408363"
---
# <a name="enroll-an-ssl-certificate-for-ad-fs"></a>Регистрация SSL-сертификата для AD FS

Службы федерации Active Directory (AD FS) \(AD FS @ no__t-1 требует сертификат для безопасного уровня сокета \(SSL @ no__t-3 для проверки подлинности сервера на каждом сервере федерации в ферме серверов федерации. Один и тот же сертификат можно использовать на каждом сервере федерации в ферме. Сертификат и его закрытый ключ должны быть доступны. Например, если сертификат и его закрытый ключ находятся в PFX-файле, то можно импортировать этот файл непосредственно в мастер настройки служб федерации Active Directory. Этот SSL-сертификат должен содержать указанные ниже данные.  
  
1.  Имя субъекта и альтернативное имя субъекта должны содержать имя службы федерации, например fs.contoso.com.  
  
2.  В качестве альтернативного имени субъекта должно быть указано значение **enterpriseregistration** , за которым следует имя участника-пользователя @no__t — 1UPN @ no__t-2 суффикса вашей организации, например **enterpriseregistration.Corp.contoso.com**.  
  
    > [!WARNING]  
    > Укажите альтернативное имя субъекта, если вы планируете включить службу регистрации устройств \(DRS @ no__t-1 для Workplace Join.  
  
> [!IMPORTANT]  
> Если в вашей организации используется несколько суффиксов имени участника-пользователя и вы планируете включить DRS, SSL-сертификат должен содержать запись альтернативного имени субъекта для каждого суффикса.  
  
## <a name="see-also"></a>См. также
[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Рекомендации по развертыванию AD FS Windows Server 2012 R2](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[Развертывание фермы серверов федерации](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  
  

