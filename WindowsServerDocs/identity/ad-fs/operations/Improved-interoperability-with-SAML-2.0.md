---
ms.assetid: 80b5335b-fa02-4944-900c-5fe4f5c6111d
title: Улучшение взаимодействия с SAML 2.0
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 3abc3f09e5ae572800e5580d14a76ada6d62e320
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816367"
---
# <a name="improved-interoperability-with-saml-20"></a>Улучшение взаимодействия с SAML 2.0



  
AD FS в Windows Server 2016 содержит дополнительную поддержку протокола SAML, включая поддержку импорта доверий на основе метаданных, содержащих несколько сущностей.  Это позволяет настроить в AD FS участие в таких конфедерациях, как InCommon Federation и другие реализации, соответствующие стандарту eGov 2.0.   
  
Новая возможность основана на группах отношений доверия с проверяющей стороной или поставщика утверждений. Каждая группа является элементом Ентитиесдескриптор (< MD: Ентитиесдескриптор >), как указано в профиле егов 2,0, содержащем один или несколько элементов EntityDescriptor.  Группы имеют общие правила авторизации, и все остальные свойства могут быть изменены как индивидуальные объекты доверия.  
  
После импорта групп доверия в AD FS AD FS автоматически обновляет отношения доверия как группу на основе документа метаданных.  
  
Чтобы включить эти сценарии, достаточно просто использовать новый командлеты PowerShell, который добавляет и удаляет объекты Адфсклаимспровидертрустсграуп и Адфсрелингпартитрустсграуп. Это можно сделать с помощью URL-адреса метаданных или файла, как показано в приведенных ниже примерах.  
  
Кроме того, AD FS 2016 поддерживает параметр области, как описано в спецификации SAML Core, раздел 3.4.1.2. Этот элемент позволяет проверяющим сторонам указывать одного или нескольких поставщиков удостоверений для запроса проверки подлинности.  
  
## <a name="examples"></a>Примеры  
  
```  
Add-AdfsClaimsProviderTrustsGroup -MetadataUrl "https://www.contosoconsortium.com/metadata/metadata.xml"   
```  
  
  
  
```  
Add-AdfsClaimsProviderTrustsGroup -MetadataFile "C:\metadata.xml"   
```  
  
## <a name="references"></a>Ссылки  
  
Профиль егов 2,0 можно найти [здесь.](https://kantarainitiative.org/confluence/download/attachments/60817482/kantara-report-egov-saml2-profile-2.0.pdf?version=1&modificationDate=1345580916000&api=v2)  
  
Спецификацию SAML Core можно найти [здесь.](https://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf)   


