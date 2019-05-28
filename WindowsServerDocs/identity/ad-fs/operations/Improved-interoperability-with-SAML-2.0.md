---
ms.assetid: 80b5335b-fa02-4944-900c-5fe4f5c6111d
title: Улучшение взаимодействия с SAML 2.0
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 4148614ba35ce29f567edb08b94e115d3f9152e9
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189102"
---
# <a name="improved-interoperability-with-saml-20"></a>Улучшение взаимодействия с SAML 2.0



  
AD FS в Windows Server 2016 содержит дополнительную поддержку протокола SAML, включая поддержку для импорта отношения доверия на основе метаданных, который содержит несколько сущностей.  Это позволяет настроить AD FS для участия в confederations, такие как InCommon федерации и другими реализациями, удовлетворяющие eGov 2.0 standard.   
  
Новая возможность основаны на группах проверяющая сторона или отношения доверия с поставщиком утверждений. Каждая группа представляет элемент EntitiesDescriptor (< md:EntitiesDescriptor >), как указано в eGov 2.0 профиль, содержащий один или несколько элементов EntityDescriptor.  Группы имеют общие правила авторизации, а все остальные свойства можно изменить как объекты отдельных доверия.  
  
После импорта группы доверия в AD FS, AD FS автоматически обновляет отношений доверия как группу на основе документа метаданных.  
  
Включение этих сценариев является достаточно просто использовать новые командлеты PowerShell, добавление и удаление AdfsClaimsProviderTrustsGroup и AdfsRelyingPartyTrustsGroup объекты. Это можно сделать с помощью URL-адрес метаданных или файл, как показано в приведенных ниже примерах.  
  
Кроме того AD FS 2016 реализована поддержка области параметра, как описано в разделе 3.4.1.2 спецификации SAML Core. Этот элемент позволяет проверяющей стороной лицами для указания одного или нескольких поставщиков удостоверений для проверки подлинности запроса.  
  
## <a name="examples"></a>Примеры  
  
```  
Add-AdfsClaimsProviderTrustsGroup -MetadataUrl "https://www.contosoconsortium.com/metadata/metadata.xml"   
```  
  
  
  
```  
Add-AdfsClaimsProviderTrustsGroup -MetadataFile "C:\metadata.xml"   
```  
  
## <a name="references"></a>Ссылок  
  
Можно найти в профиле eGov 2.0 [здесь.](https://kantarainitiative.org/confluence/download/attachments/60817482/kantara-report-egov-saml2-profile-2.0.pdf?version=1&modificationDate=1345580916000&api=v2)  
  
Можно найти в спецификации SAML Core [здесь.](https://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf)   


