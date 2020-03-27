---
title: Устранение неполадок брандмауэра в Windows Server Essentials
description: Описание использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 51d94b67-8b9b-4159-80dd-f652d73a43cb
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 15a2361284d041898d9ad7240643fdb55aa5b866
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80318588"
---
# <a name="troubleshoot-your-firewall-in-windows-server-essentials"></a>Устранение неполадок брандмауэра в Windows Server Essentials
 
>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
  
 При возникновении проблем с удаленным доступом запустите мастер исправления повсеместного доступа.  
  
### <a name="to-run-the-repair-anywhere-access-wizard"></a>Запуск мастера исправления повсеместного доступа  
  
1. Откройте Панель администрирования.  
  
2. Нажмите кнопку **Параметры**, затем откройте вкладку **Повсеместный доступ** и щелкните **Исправить**.  
  
3. Следуйте инструкциям мастера исправления повсеместного доступа.  
  
   Если вы применяете расширенную настройку сети или используете брандмауэр другого разработчика, может потребоваться открыть дополнительные порты брандмауэра. Описанные в следующей таблице порты зарегистрированы в Internet Assigned Numbers Authority (IANA).  
  
|Номер порта|Описание|  
|-----------------|-----------------|  
|65500|Веб-служба сертификатов|  
|65510 и 65515|Веб-сайт развертывания клиентских компьютеров|  
|65520|Веб-служба для клиентских компьютеров Mac|  
|65532|Платформа поставщика для связи с сервером замыканием на себя|  
|6602|Платформа поставщика для обмена данными между сервером и клиентскими компьютерами|  
  
## <a name="see-also"></a>См. также:  
  
-   [Использовать удаленный Веб-доступ](../use/Use-Remote-Web-Access-in-Windows-Server-Essentials.md)  
  
-   [Управление удаленными Веб-доступ](../manage/Manage-Remote-Web-Access-in-Windows-Server-Essentials.md)  
  
-   [Управление повсеместным доступом](../manage/Manage-Anywhere-Access-in-Windows-Server-Essentials.md)  
  
-   [Управление Windows Server Essentials](../manage/Manage-Windows-Server-Essentials.md)  
  

-   [Поддержка Windows Server Essentials](Support-Windows-Server-Essentials.md)

-   [Поддержка Windows Server Essentials](../support/Support-Windows-Server-Essentials.md)

