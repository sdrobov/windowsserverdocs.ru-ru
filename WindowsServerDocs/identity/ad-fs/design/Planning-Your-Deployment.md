---
ms.assetid: bb9b9e18-bf2f-4115-be77-9a165944db41
title: Планирование развертывания
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 607dc34c8f44d8d96a8dc0c9d1ed004edc799167
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407998"
---
# <a name="planning-your-deployment"></a>Планирование развертывания

При планировании совместной работы @ no__t-0organizational \(federation @ no__t-2based @ no__t-3 с помощью службы федерации Active Directory (AD FS) \(AD FS @ no__t-5, сначала определите, будет ли ваша организация размещать веб-ресурс для доступа другим Организации через Интернет или, если вы будете предоставлять доступ к веб-ресурсу для сотрудников Организации. Это определение влияет на развертывание AD FS и является фундаментальным в планировании инфраструктуры AD FS.  
  
> [!NOTE]  
> Все стороны должны ясно понимать роль организации в соглашении о федерации.  
  
Для [проектирования федеративного единого входа в интернете](Federated-Web-SSO-Design.md)AD FS использует такие термины, как *партнер по учетным записям* \(also, который называется *поставщиком удостоверений* в AD FS управления, оснастка @ no__t-4in @ no__t-5 и *партнер по ресурсам* \(also, называемый  *Проверяющая сторона* в AD FS Management Snap @ no__t-9in @ no__t-10, чтобы отличать организацию, в которой размещены учетные записи, с партнером по учетным записям 1-12, из Организации, в которой размещены ресурсы Web @ no__t-13based 4the Resource партнер @ no__t-15.  
  
В [Web SSO Design](Web-SSO-Design.md)организация выступает одновременно в роли партнера по учетным записям и в роли партнера по ресурсам, так как она предоставляет своим пользователям доступ к приложениям.  
  
В следующих разделах объясняются некоторые основные понятия AD FS партнерской организации. Они также содержат ссылки на разделы руководства по развертыванию AD FS, содержащие сведения о настройке и настройке организаций партнеров по учетным записям и организациях партнеров по ресурсам на основе целей развертывания AD FS.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Рекомендации по безопасному планированию и развертыванию AD FS](Best-Practices-for-Secure-Planning-and-Deployment-of-AD-FS.md)  
  
-   [Планирование взаимодействия с AD FS 1.x](Planning-for-Interoperability-with-AD-FS-1.x.md)  
  
-   [Когда следует использовать делегирование удостоверений](When-to-Use-Identity-Delegation.md)  
  
-   [Развертывание служб федерации Active Directory в организации партнера по учетным записям](Deploying-AD-FS-in-the-Account-Partner-Organization-2012.md)  
  
-   [Развертывание служб федерации Active Directory в организации партнера по ресурсам](Deploying-AD-FS-in-the-Resource-Partner-Organization-2012.md)  
  
## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)


