---
ms.assetid: 80b5335b-fa02-4944-900c-5fe4f5c6111d
title: "Улучшение взаимодействия с SAML 2.0"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 4f55eaacec8ee0eb41e1980f1aa15c6256f8b979
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="improved-interoperability-with-saml-20"></a>Улучшение взаимодействия с SAML 2.0

>Область применения: Windows Server 2016

  
AD FS в Windows Server 2016 содержит дополнительные поддержку протокола SAML, включая поддержку Импорт отношений доверия на основе метаданных, содержащий несколько объектов.  Это позволяет настроить AD FS для участия в confederations, например InCommon федерации и в других реализациях соблюдения eGov стандарт 2.0.   
  
Новые возможности на основе групп проверяющей стороной и отношения доверия с поставщиком утверждений. Каждая группа является элементом EntitiesDescriptor (< md:EntitiesDescriptor >), указанном в eGov 2.0 профиль, содержащий один или несколько элементов EntityDescriptor.  Для групп действуют общие правила авторизации, а все остальные свойства можно изменить как доверия отдельные объекты.  
  
После группы доверия импортируются в AD FS, AD FS автоматическое обновление отношений доверия в группу на основе документа метаданных.  
  
Включение этих сценариев является таким простым, как с помощью нового командлеты PowerShell, добавление и удаление AdfsClaimsProviderTrustsGroup и AdfsRelyingPartyTrustsGroup объекты. Это можно сделать с помощью URL-адрес метаданных или файла, как показано в примерах ниже.  
  
Кроме того AD FS 2016 реализована поддержка параметра область, как описано в спецификации SAML основной раздел 3.4.1.2. Этот элемент позволяет проверяющей лицами, чтобы указать один или несколько поставщиков удостоверений для проверки подлинности запроса.  
  
## <a name="examples"></a>Примеры  
  
```  
Add-AdfsClaimsProviderTrustsGroup -MetadataUrl "https://www.contosoconsortium.com/metadata/metadata.xml"   
```  
  
  
  
```  
Add-AdfsClaimsProviderTrustsGroup -MetadataFile "C:\metadata.xml"   
```  
  
## <a name="references"></a>Ссылки  
  
Профиль eGov 2.0 можно найти [здесь.](https://kantarainitiative.org/confluence/download/attachments/60817482/kantara-report-egov-saml2-profile-2.0.pdf?version=1&modificationDate=1345580916000&api=v2)  
  
Можно найти в спецификации основных SAML [здесь.](https://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf)   


