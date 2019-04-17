---
title: "Устранение неполадок повсеместного доступа в Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68f2b05c-09eb-4cba-8db4-a91353b513c6
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: a14dbaed8c36f52814ba8080262ef60c399931dc
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="troubleshoot-anywhere-access-in-windows-server-essentials"></a>Устранение неполадок повсеместного доступа в Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

В этом разделе приведены общие инструкции по использованию мастера исправления повсеместного доступа в Windows Server Essentials для устранения неполадок, которые позволяют пользователям сети получить доступ к ресурсам сервера. Повсеместный доступ функции удаленного веб-доступа, виртуальной частной сети (VPN) и DirectAccess позволяют пользователям сети получать доступ к ресурсам сервера из любого места с подключением к Интернету, в любое время, с любого устройства.  
  
 Мастер исправления повсеместного доступа пытается определить и устранить неполадки с маршрутизатором, именем домена или брандмауэром, которые не позволяют пользователям сети получить удаленный доступ к ресурсам сервера.  
  
> [!NOTE]
>  Последние сведения об устранении неполадок от сообщества пользователей Windows Server Essentials, мы рекомендуем посетить [форуме Windows Server Essentials](https://social.technet.microsoft.com/Forums/winserveressentials/threads). Форум Windows Server Essentials — отлично подходят для поиска справки или задать вопрос.  
  
### <a name="to-repair-anywhere-access"></a>Исправление повсеместного доступа  
  
1.  Войдите на сервер и откройте панель мониторинга.  
  
2.  Нажмите кнопку **параметры**, а затем нажмите кнопку **повсеместного доступа** вкладку.  
  
3.  Нажмите кнопку **восстановления**. Запускается мастер исправления повсеместного доступа.  
  
4.  Нажмите кнопку **Далее**. Мастер анализирует работу повсеместного доступа, находит проблему и пытается устранить проблему.  
  
5.  Если вы получаете оповещение, по завершении работы мастера, нажмите кнопку **повторить** чтобы попытаться устранить проблему еще раз. Если вы продолжите получать предупреждение, проверьте предупреждения Дополнительные сведения о проблеме и действия по устранению неполадок.  
  
### <a name="to-get-more-information-about-an-alert"></a>Чтобы получить дополнительные сведения об оповещении  
  
1.  В правом верхнем углу панели мониторинга щелкните любой значок ошибки или предупреждения, чтобы открыть средство просмотра оповещений.  
  
2.  В средстве просмотра оповещений выберите ошибку или оповещение для просмотра дополнительных сведений.  
  
## <a name="additional-troubleshooting-for-anywhere-access"></a>Дополнительные возможности устранения неполадок повсеместного доступа  
 Если мастеру исправления повсеместного доступа не удается восстановить Повсеместный доступ, проверьте следующие ресурсы по устранению неполадок для проблем, связанных с удаленного веб-доступа, VPN и DirectAccess:  
  

-   [Устранение неполадок подключения удаленного веб-доступа](Troubleshoot-Remote-Web-Access-connectivity-in-Windows-Server-Essentials.md)  
  
-   [Устранение неполадок брандмауэра](Troubleshoot-your-firewall-in-Windows-Server-Essentials.md)  

-   [Устранение неполадок подключения удаленного веб-доступа](../support/Troubleshoot-Remote-Web-Access-connectivity-in-Windows-Server-Essentials.md)  
  
-   [Устранение неполадок брандмауэра](../support/Troubleshoot-your-firewall-in-Windows-Server-Essentials.md)  

  
-   Проверьте [форуме Windows Server Essentials](https://social.technet.microsoft.com/Forums/winserveressentials/threads) последних неполадках, собранную сообществом Windows Server Essentials.
