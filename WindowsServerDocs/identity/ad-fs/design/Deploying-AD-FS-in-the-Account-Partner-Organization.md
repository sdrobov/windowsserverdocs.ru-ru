---
ms.assetid: 8c3536b7-d091-4ee6-ad04-24713f070862
title: Развертывание служб федерации Active Directory в партнерской организации по учетным записям
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 93f61bc7fd147b2e0220178bcd163b6ca56279cf
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66191567"
---
# <a name="deploying-ad-fs-in-the-account-partner-organization"></a>Развертывание служб федерации Active Directory в партнерской организации по учетным записям

Партнера по учетным записям в службах федерации Active Directory \(AD FS\) представляет организацию, в котором физически хранятся учетные записи пользователей в поддерживаемом хранилище атрибутов отношения доверия федерации. Дополнительные сведения о какой атрибут поддерживаемых хранилищ см. в разделе [The Role of Attribute Stores](../../ad-fs/technical-reference/The-Role-of-Attribute-Stores.md).  
  
Сервер федерации в организации партнера по учетным записям проверяет подлинность локальных пользователей и создает токены безопасности, которые используются партнером по ресурсам при выполнении авторизации. Проверяющие стороны, таких как веб-сайтов и веб-служб могут затем легко регистрируются на сервере федерации и использовать выданные токены для проверки подлинности и управления доступом.  
  
В сценариях, в которых необходимо предоставить пользователям доступ к множеству федеративных приложений или служб, когда каждый приложение или служба размещается в разных организациях — сервер федерации учетных записей партнеров можно настроить таким образом, вы можете развернуть несколько проверяющих сторон.  
  
Дополнительные сведения о том, как установить и настроить организации партнера по учетным записям см. в разделе [контрольный список: Настройка партнерской организации по](../../ad-fs/deployment/Checklist--Configuring-the-Account-Partner-Organization.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Сведения о роли сервера федерации в организации партнера по учетным записям](Review-the-Role-of-the-Federation-Server-in-the-Account-Partner.md)  
  
-   [Сведения о роли прокси-сервера федерации в организации партнера по учетным записям](Review-the-Role-of-the-Federation-Server-Proxy-in-the-Account-Partner.md)  
  
-   [Подготовка клиентских компьютеров в партнере по учетным записям](Prepare-Client-Computers-in-the-Account-Partner.md)  
  
## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
