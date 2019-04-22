---
ms.assetid: 9aaca9c5-ce44-495c-aad6-61aede87a83f
title: Развертывание служб федерации Active Directory в партнерской организации по учетным записям
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 3a668659f375f7fe96d676e7018e9e9315e35be5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814445"
---
# <a name="deploying-ad-fs-in-the-account-partner-organization"></a>Развертывание служб федерации Active Directory в партнерской организации по учетным записям

>Область применения. Windows Server 2012

Партнера по учетным записям в службах федерации Active Directory \(AD FS\) представляет организацию, в котором физически хранятся учетные записи пользователей в поддерживаемом хранилище атрибутов отношения доверия федерации. Дополнительные сведения о какой атрибут поддерживаемых хранилищ см. в разделе [The Role of Attribute Stores](../../ad-fs/technical-reference/The-Role-of-Attribute-Stores.md).  
  
Сервер федерации в организации партнера по учетным записям проверяет подлинность локальных пользователей и создает токены безопасности, которые используются партнером по ресурсам при выполнении авторизации. Проверяющие стороны, таких как веб-сайтов и веб-служб могут затем легко регистрируются на сервере федерации и использовать выданные токены для проверки подлинности и управления доступом.  
  
В сценариях, в которых необходимо предоставить пользователям доступ к множеству федеративных приложений или служб, когда каждый приложение или служба размещается в разных организациях — сервер федерации учетных записей партнеров можно настроить таким образом, вы можете развернуть несколько проверяющих сторон.  
  
Дополнительные сведения о том, как установить и настроить организации партнера по учетным записям см. в разделе [контрольный список: Настройка партнерской организации по](../../ad-fs/deployment/Checklist--Configuring-the-Account-Partner-Organization.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Сведения о роли сервера федерации в партнере по учетным записям](Review-the-Role-of-the-Federation-Server-in-the-Account-Partner.md)  
  
-   [Review the Role of the Federation Server Proxy in the Account Partner](Review-the-Role-of-the-Federation-Server-Proxy-in-the-Account-Partner.md)  
  
-   [Подготовка клиентских компьютеров в партнере по учетным записям](Prepare-Client-Computers-in-the-Account-Partner.md)  
  
## <a name="see-also"></a>См. также
[Руководство по разработке AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
