---
ms.assetid: 4b71b212-7e5b-4fad-81ee-75b3d1f27869
title: "Поддержка привязки альтернативного имени узла для проверки подлинности сертификата в AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 553ff059693c7b0c0e6f0364d82c1adbca661097
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="ad-fs-support-for-alternate-hostname-binding-for-certificate-authentication"></a>Поддержка привязки альтернативного имени узла для проверки подлинности сертификата в AD FS

>Область применения: Windows Server 2016

На многих сетей политики локального брандмауэра не может разрешить трафик через нестандартным портам, например 49443. Это стало ошибку при попытке выполнения проверки подлинности сертификата в AD FS перед AD FS в Windows Server 2016. Это, поскольку не могут иметь различные привязки для проверки подлинности устройства и проверки подлинности сертификата пользователя на одном узле. Порт по умолчанию 443 привязана получать сертификаты на устройство и не могут быть изменены для поддержки нескольких привязки в тот же канал. Результаты были что проверки подлинности смарт-карт не будет работать, и пользователи не понятия что случилось, так как не удалось найти действительно что случилось.  
  
С помощью AD FS в Windows Server 2016 это можно сделать.
  
В AD FS в Windows Server 2016 это изменилось. Теперь мы поддерживаем два режима, первый использует один и тот же узел (т. е. adfs.contoso.com) с помощью различных портов (443, 49443). Второй при использовании разных узлах (adfs.contoso.com и certauth.adfs.contoso.com) один и тот же порт (443). Эта процедура потребует SSL-сертификат для поддержки «certauth < имя службы федерации Active Directory службы >». как альтернативное имя субъекта. Это можно сделать во время создания фермы или более поздней версии с помощью PowerShell.  
  
## <a name="how-to-configure-alternate-host-name-binding-for-certificate-authentication"></a>Настройка привязки имя альтернативного узла для проверки подлинности сертификата  
Существует два способа, можно добавить привязку имя альтернативного узла для проверки подлинности сертификата. Первый — при настройке новой ферме AD FS с AD FS в Windows Server 2016, если сертификат содержит альтернативное имя субъекта (SAN), автоматически будет настройка для второй метод, упомянутых выше. То есть он будет автоматически установки двух разных узлах (sts.contoso.com и certauth.sts.contoso.com с тот же порт. Если сертификат не содержит SAN, вы увидите предупреждение о том, что альтернативные имена субъекта сертификата не поддерживает certauth.*. См. ниже снимки экрана. Первый показана установка где сертификат был SAN, а во втором примере показана сертификат, который не был.  
  
![привязки альтернативного имени узла](media/AD-FS-support-for-alternate-hostname-binding-for-certificate-authentication/ADFS_CA_1.png)  
  
![привязки альтернативного имени узла](media/AD-FS-support-for-alternate-hostname-binding-for-certificate-authentication/ADFS_CA_2.png)  
  
Аналогичным образом, после развертывания AD FS в Windows Server 2016 можно использовать командлет PowerShell: Set-AdfsAlternateTlsClientBinding.
  
```powershell
Set-AdfsAlternateTlsClientBinding -Member DC1.contoso.com -Thumbprint '<thumbprint of cert>'
```

При появлении соответствующего запроса нажмите кнопку "Да, чтобы подтвердить".  И, должен быть.

![привязки альтернативного имени узла](media/AD-FS-support-for-alternate-hostname-binding-for-certificate-authentication/ADFS_CA_3.png)

## <a name="additional-references"></a>Дополнительные ссылки

* [Управление SSL-сертификатов в AD FS и WAP в Windows Server 2016](../operations/Manage-SSL-Certificates-AD-FS-WAP-2016.md)
