---
ms.assetid: d0ba3c0d-869f-4e24-89d7-499da7576f22
title: "Сведения о роли сервера федерации в партнера по учетным записям"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 0914d32e8f24d5e7db0a25c733342c1bde3e0329
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="review-the-role-of-the-federation-server-in-the-account-partner"></a>Сведения о роли сервера федерации в партнера по учетным записям

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Сервер федерации в службах федерации Active Directory \(AD FS\) функционирует как поставщик маркера безопасности. Создает утверждения на основе учетных записей хранения, находящиеся в локальных атрибутов значения сервера федерации и упаковывает их в маркеры безопасности, чтобы пользователи легко могут получить доступ к browser\ веб-приложений \ (с помощью одного \(SSO\)\) входа в систему, которые размещаются в организации партнера по ресурсам.  
  
> [!NOTE]  
> При доступа пользователей федеративных приложений с помощью веб-браузер, сервер федерации автоматически выдает пользователям для сохранения их состояния входа в систему для этого приложения, веб browser\ файлы cookie. Эти файлы cookie содержат утверждения для пользователей. Файлы cookie включают возможности единого входа, чтобы пользователям не требуется вводить учетные данные каждый раз, что разные browser\ веб-приложения в организации партнера по ресурсам.  
  
В проекте единого входа в Интернете организации с сетью периметра, которые предоставляют пользователям Интернета доступ к приложениям необходимо установить прокси-сервера федерации в сети периметра. Федеративного Единого входа должен быть хотя бы один сервер федерации в корпоративной сети организации партнера по учетным записям и хотя бы один сервер федерации в корпоративной сети организации партнера по ресурсам.  
  
> [!NOTE]  
> Перед настройкой компьютере сервера федерации в организации партнера по учетным записям необходимо присоединить компьютер к любому домену в лесу Active Directory, где сервер федерации будет использоваться для проверки подлинности пользователей из этого леса. Дополнительные сведения см. в разделе [Checklist: Setting Up a Federation Server](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server.md).  
  
## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)