---
ms.assetid: cea6011d-3753-4b95-aaa5-38d4e97d6e42
title: Prepare Client Computers in the Account Partner
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 0c5bdcb0a80b15a1905109229ddd20ee642a8dd7
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="prepare-client-computers-in-the-account-partner"></a>Prepare Client Computers in the Account Partner

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Самый простой способ для администратора в организации партнера по учетным записям подготовить клиентские компьютеры для доступа к приложениям \(AD FS\) федеративных служб федерации Active Directory является использование групповой политики. Групповая политика предоставляет удобный способ передачи конкретных сертификатов и параметров, необходимых для создания федерации на всех клиентских компьютеров, которые будут использоваться для доступа к федеративным приложениям.  
  
Чтобы клиентские компьютеры можно легко получить доступ к федеративным приложениям без запросов сертификатов или запросов сайта, связанных с доверенными, рекомендуется подготовить каждый клиентский компьютер перед широким развертыванием AD FS в вашей организации. Рекомендуется использовать групповую политику, чтобы автоматически.  
  
-   Настройки Internet Explorer на каждом клиентском компьютере для доверия сервера федерации учетных записей.  
  
    Дополнительные сведения см. в разделе [Настройка клиентских компьютеров на доверие серверу федерации учетной записи](../../ad-fs/deployment/Configure-Client-Computers-to-Trust-the-Account-Federation-Server.md).  
  
-   Установите соответствующую учетную запись сервера федерации, сервер федерации ресурсов и сертификатов \(SSL\) протокола SSL для веб-сервера \ (или эквивалент сертификаты, цепочка включает для доверенных root\) на каждом клиентском компьютере.  
  
    Дополнительные сведения см. в разделе [распространение сертификатов на клиентские компьютеры с помощью групповой политики](../../ad-fs/deployment/Distribute-Certificates-to-Client-Computers-by-Using-Group-Policy.md).  
  

## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
