---
ms.assetid: 4b71b212-7e5b-4fad-81ee-75b3d1f27869
title: Поддержка привязки альтернативного имени узла для проверки подлинности сертификата в AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 553ff059693c7b0c0e6f0364d82c1adbca661097
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59887255"
---
# <a name="ad-fs-support-for-alternate-hostname-binding-for-certificate-authentication"></a>Поддержка привязки альтернативного имени узла для проверки подлинности сертификата в AD FS

>Область применения. Windows Server 2016

В многих сетях политиках локального брандмауэра не может разрешить трафик через нестандартные порты, такие как 49443. Это стало проблема при попытке выполнить аутентификацию на основе сертификата AD FS до AD FS в Windows Server 2016. Это обусловлено различных привязок для проверки подлинности устройств и проверка подлинности сертификата пользователя не может использоваться на одном узле. Порт по умолчанию 443 привязана получать сертификаты на устройстве и не могут быть изменены для поддержки нескольких привязки в тот же канал. Результаты были, что смарт-карты не будет работать и пользователи знают о того, что произошло, так как нет никаких признаков того, что в действительности произошло.  
  
С AD FS в Windows Server 2016 это можно сделать.
  
В AD FS в Windows Server 2016 ситуация изменилась. Теперь мы поддерживаем два режима, первый использует один и тот же узел (т. е. adfs.contoso.com) с различными портами (443, 49443). Второй разных узлах (adfs.contoso.com и certauth.adfs.contoso.com) использовать один и тот же порт (443). Для этого потребуется сертификат SSL для поддержки «certauth < adfs-service-name >». как альтернативное имя субъекта. Это можно сделать во время создания фермы или более поздней версии с помощью PowerShell.  
  
## <a name="how-to-configure-alternate-host-name-binding-for-certificate-authentication"></a>Как настроить привязки имени узла альтернативный для проверки подлинности сертификата  
Существует два способа, можно добавить привязку названия альтернативный сервер для проверки подлинности сертификата. Первый — при настройке новой фермы AD FS с AD FS для Windows Server 2016, если сертификат содержит альтернативное имя субъекта (SAN), то он автоматически будет настроена для использования второй метод, упомянутых выше. То есть он автоматически настраивает двух разных узлах (sts.contoso.com и certauth.sts.contoso.com с тот же порт. Если сертификат не содержит по сети SAN, вы увидите предупреждение, информирующее о том, что альтернативные имена субъектов сертификатов не поддерживает certauth.*. См. в разделе снимке экрана ниже. На первом показана установка где сертификата есть сеть хранения данных, а во втором показан сертификат, этого не сделали.  
  
![привязки альтернативного имени узла](media/AD-FS-support-for-alternate-hostname-binding-for-certificate-authentication/ADFS_CA_1.png)  
  
![привязки альтернативного имени узла](media/AD-FS-support-for-alternate-hostname-binding-for-certificate-authentication/ADFS_CA_2.png)  
  
Аналогичным образом после развертывания AD FS в Windows Server 2016 можно использовать командлет PowerShell: Set-AdfsAlternateTlsClientBinding.
  
```powershell
Set-AdfsAlternateTlsClientBinding -Member DC1.contoso.com -Thumbprint '<thumbprint of cert>'
```

Когда появится запрос, нажмите кнопку Да для подтверждения.  И это должно быть.

![привязки альтернативного имени узла](media/AD-FS-support-for-alternate-hostname-binding-for-certificate-authentication/ADFS_CA_3.png)

## <a name="additional-references"></a>Дополнительная справка

* [Управление SSL-сертификатов в AD FS и WAP в Windows Server 2016](../operations/Manage-SSL-Certificates-AD-FS-WAP-2016.md)
