---
ms.assetid: cea6011d-3753-4b95-aaa5-38d4e97d6e42
title: Подготовка клиентских компьютеров для партнеров по учетным записям
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 0c5bdcb0a80b15a1905109229ddd20ee642a8dd7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868525"
---
# <a name="prepare-client-computers-in-the-account-partner"></a>Подготовка клиентских компьютеров для партнеров по учетным записям

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Самый простой способ для администратора в учетной записи организации партнера по записям подготовить клиентские компьютеры для доступа к службам федерации Active Directory \(AD FS\) федеративных приложений является использование групповой политики. Групповая политика обеспечивает удобный способ передачи конкретных сертификатов и параметров, необходимых для создания федерации на всех клиентских компьютерах, которые будут использоваться для доступа к федеративным приложениям.  
  
Таким образом, чтобы клиентские компьютеры можно легко получить доступ к федеративным приложениям без запросов сертификатов или доверенных запросов, связанных с сайта, рекомендуется подготовить каждый клиентский компьютер перед развертыванием AD FS широко в вашей организации. Рассмотрите возможность использования групповой политики для автоматической  
  
-   Настройка Internet Explorer на каждом клиентском компьютере доверять сервер федерации учетных записей.  
  
    Дополнительные сведения см. в разделе [Configure Client Computers to Trust the Account Federation Server](../../ad-fs/deployment/Configure-Client-Computers-to-Trust-the-Account-Federation-Server.md).  
  
-   Установите соответствующую учетную запись сервера федерации, сервер федерации ресурсов и веб-сервером Secure Sockets Layer \(SSL\) сертификаты \(или эквивалент сертификаты, которые восходят по цепочке с доверенным корневым расположением\) на каждом клиентский компьютер.  
  
    Дополнительные сведения см. в разделе [распространять сертификаты для клиентских компьютеров с помощью групповой политики](../../ad-fs/deployment/Distribute-Certificates-to-Client-Computers-by-Using-Group-Policy.md).  
  

## <a name="see-also"></a>См. также
[Руководство по разработке AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
