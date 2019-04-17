---
ms.assetid: bb9b9e18-bf2f-4115-be77-9a165944db41
title: "Планирование развертывания"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 5c7cec9ad92605f3dc98f8ce8fb7853a7ae61299
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="planning-your-deployment"></a>Планирование развертывания

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

При планировании совместной работы организации cross\ \(federation\-based\), с помощью служб федерации Active Directory \(AD FS\), сначала определите, если в организации размещаться веб-ресурс, доступный другим организациям через Интернет или будет предоставляться доступ к веб-ресурсу сотрудникам в вашей организации. Это решение влияет на развертывание Служб федерации Active Directory и является определяющим в планировании инфраструктуры AD FS.  
  
> [!NOTE]  
> Убедитесь, что роль организации в соглашении о федерации должны ясно понимать все стороны.  
  
Для [Federated Web SSO Design](Federated-Web-SSO-Design.md), службы федерации Active Directory используются термины, такие как *партнера по учетным записям* \ (также называется *поставщика удостоверений* в snap\ управления AD FS-количества) и *партнера по ресурсам* \ (также называется *проверяющей стороны* в управления AD FS snap\ количества) приведены различия организации, на котором размещается учетные записи \(the account partner\) из организации, где размещены ресурсы, веб-\(the resource partner\).  
  
В [Web SSO Design](Web-SSO-Design.md), организация выступает одновременно в учетной записи партнера и ресурсов партнеров роли роли, так как она предоставляет своим пользователям доступ к приложениям.  
  
В следующих разделах показано, что некоторые из AD FS партнерские организации понятия. Они также содержат ссылки на разделы в руководстве по развертыванию AD FS, содержащие сведения об установке и настройке партнерских организаций по учетной записи и партнерских организациях по ресурсам в зависимости от целей развертывания AD FS.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Рекомендации по безопасному планированию и развертыванию AD FS](Best-Practices-for-Secure-Planning-and-Deployment-of-AD-FS.md)  
  
-   [Планирование взаимодействия с AD FS 1.x](Planning-for-Interoperability-with-AD-FS-1.x.md)  
  
-   [Использование делегирования удостоверений](When-to-Use-Identity-Delegation.md)  
  
-   [Развертывание AD FS в организации партнера по учетным записям](Deploying-AD-FS-in-the-Account-Partner-Organization-2012.md)  
  
-   [Развертывание AD FS в организации партнера по ресурсам](Deploying-AD-FS-in-the-Resource-Partner-Organization-2012.md)  
  
## <a name="see-also"></a>См. также:
[Руководство по разработке служб AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)


