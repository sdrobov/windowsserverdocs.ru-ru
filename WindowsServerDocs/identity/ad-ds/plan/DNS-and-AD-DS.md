---
ms.assetid: c32606b4-2ee2-4df3-a704-8ac6723e188f
title: "DNS-сервера и Доменных службах Active Directory"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 8e7ee494c157396a7d58e9fd1b4b80060c4d99fc
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="dns-and-ad-ds"></a>DNS-сервера и Доменных службах Active Directory

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Доменных служб Active Directory (AD DS) использует службы разрешения имен доменных имен (DNS) для того чтобы клиенты могли находить контроллеры домена и контроллеров домена только для этого узла службы каталогов для обмена данными друг с другом.  
  
AD DS позволяет легко интеграции имен Active Directory в существующее пространство имен DNS. Возможности таких, как зоны DNS, интегрированные с Active Directory упрощает развертывание, устраняя необходимость настраивать дополнительные зоны DNS, а затем настройте передачи зоны.  
  
Сведения о поддержке DNS-сервера AD DS см. поддержка DNS Технический справочник по Active Directory ([https://go.microsoft.com/fwlink/?LinkID=48147](https://go.microsoft.com/fwlink/?LinkID=48147)).  
  
> [!NOTE]  
> Если вы реализуете несвязанного пространства имен, в котором имя домена AD DS, отличается от основной DNS-суффикс, используемый клиентами, интеграция Доменных службах Active Directory с DNS-сервера является более сложным. Дополнительные сведения см. в разделе [несвязанное пространство имен](../../ad-ds/plan/../../ad-ds/plan/Disjoint-Namespace.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Расположение контроллера домена](../../ad-ds/plan/Domain-Controller-Location.md)  
  
-   [Интегрированная Directory зоны DNS, Active](../../ad-ds/plan/Active-Directory-Integrated-DNS-Zones.md)  
  
-   [Именование компьютеров](../../ad-ds/plan/Computer-Naming.md)  
  
-   [Несвязанное пространство имен.](../../ad-ds/plan/../../ad-ds/plan/Disjoint-Namespace.md)  
  


