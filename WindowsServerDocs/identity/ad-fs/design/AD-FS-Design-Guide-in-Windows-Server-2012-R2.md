---
ms.assetid: a8558c9d-0606-4881-93b2-f2d2716b18e7
title: Руководство по разработке служб AD FS в Windows Server 2012 R2
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 614bc2b4571dd8a1b35c075ae1dec6934e77e148
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408163"
---
# <a name="ad-fs-design-guide-in-windows-server"></a>Руководство по проектированию AD FS в Windows Server 

Службы федерации Active Directory (AD FS) \(AD FS @ no__t-1 предоставляет упрощенную, защищенную федерацию удостоверений и единый вход в Интернет @ no__t-2on \(SSO @ no__t-4 для конечных пользователей, которым требуется доступ к приложениям в AD FS @ no__t-5secured Enterprise, в организациях-партнерах Федерации или в облаке.  
  
В Windows Server® 2012 R2 AD FS включает службу роли службы федерации, которая выступает в качестве поставщика удостоверений \(authenticates пользователей для предоставления маркеров безопасности для приложений, которые доверяют AD FS @ no__t-1 или в качестве поставщика федерации \(consumes tokens из другие поставщики удостоверений, а затем предоставляют маркеры безопасности для приложений, которые доверяют AD FS @ no__t-3.  
  
Функцию предоставления доступа к экстрасети для приложений и служб, которые защищены в Windows Server 2012 R2 с помощью AD FS, теперь выполняет новая служба роли удаленного доступа, называемая прокси-службой веб-приложения. В этом состоит отличие от предыдущих версий Windows Server, в которых эта функция находилась под управлением прокси-сервера федерации AD FS. Прокси веб-приложения — это роль сервера, предназначенная для предоставления доступа к сценарию AD FS @ no__t-0related экстрасети и другим сценариям экстрасети. Дополнительные сведения о прокси веб-приложения см. в разделе [Пошаговое руководство по прокси веб-приложения](https://technet.microsoft.com/library/dn280944.aspx).  
  
## <a name="about-this-guide"></a>Об этом руководстве  
В этом руководством содержатся рекомендации по планированию нового развертывания AD FS в зависимости от требований Организации. Это руководство предназначено для использования специалистом по инфраструктуре или системным архитектором. Он выделяет основные точки принятия решений при планировании развертывания AD FS. Прежде чем читать это руководство, вы получите хорошее представление о том, как AD FS работает на функциональном уровне. Дополнительные сведения см. в разделе [Understanding Key AD FS Concepts](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md).  
  
## <a name="in-this-guide"></a>В данном руководстве  
  
-   [Определение целей по развертыванию служб федерации Active Directory](Identify-Your-AD-FS-Deployment-Goals.md)  
  
-   [Планирование топологии развертывания для служб федерации Active Directory](Plan-Your-AD-FS-Deployment-Topology.md)  
  
-   [Требования к службам федерации Active Directory](AD-FS-Requirements.md)  
  
  
## <a name="see-also"></a>См. также  
[Разработка служб федерации Active Directory](../../ad-fs/AD-FS-Design.md)  
  

