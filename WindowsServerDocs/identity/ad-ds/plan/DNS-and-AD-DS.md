---
ms.assetid: c32606b4-2ee2-4df3-a704-8ac6723e188f
title: DNS и доменные службы Active Directory
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/08/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: f6d75a78119d76a0f8380967292b1d0abc720597
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813145"
---
# <a name="dns-and-ad-ds"></a>DNS и доменные службы Active Directory

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Доменных служб Active Directory (AD DS) использует службы разрешения имен доменных имен (DNS) чтобы клиенты могли находить контроллеры домена и контроллеров домена, на которых размещены службы каталогов для взаимодействия друг с другом.  
  
AD DS обеспечивает простую интеграцию пространства имен Active Directory в существующее пространство имен DNS. Функции например зон DNS, интегрированный с Active Directory упрощают процесс развертывания, устраняя необходимость в настройке дополнительные зоны DNS, а затем настройте передачи зоны.  
  
Сведения о поддержке DNS AD DS, см. в разделе [поддержка DNS в техническом справочнике по Active Directory](https://go.microsoft.com/fwlink/?LinkID=48147).  
  
> [!NOTE]  
> Если вы реализуете несвязанное пространство имен, в котором имя домена AD DS, отличается от основной DNS-суффикс, используемого клиентами, интеграция с доменными Службами AD с помощью DNS является более сложным. Дополнительные сведения см. в разделе [несвязанное пространство имен](../../ad-ds/plan/../../ad-ds/plan/Disjoint-Namespace.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
- [Расположение контроллера домена](../../ad-ds/plan/Domain-Controller-Location.md)  
- [Active Directory интегрированной зоны DNS](../../ad-ds/plan/Active-Directory-Integrated-DNS-Zones.md)  
- [Присвоение имен компьютерам](../../ad-ds/plan/Computer-Naming.md)  
- [Несвязанное пространство имен](../../ad-ds/plan/../../ad-ds/plan/Disjoint-Namespace.md)  
