---
ms.assetid: c32606b4-2ee2-4df3-a704-8ac6723e188f
title: DNS и доменные службы Active Directory
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/08/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 82c96ac3f146510c5590aabea75a60ca0f5f90cc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402689"
---
# <a name="dns-and-ad-ds"></a>DNS и доменные службы Active Directory

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Службы домен Active Directory Services (AD DS) используют службы разрешения имен системы доменных имен (DNS), чтобы клиенты могли искать контроллеры домена и контроллеры домена, на которых размещается служба каталогов, для взаимодействия друг с другом.  
  
AD DS позволяет легко интегрировать пространство имен Active Directory в существующее пространство имен DNS. Такие функции, как интегрированные с Active Directory зоны DNS, упрощают развертывание DNS, устраняя необходимость в настройке дополнительных зон, а затем настраивают зонные передачи.  
  
Сведения о том, как DNS поддерживает AD DS, см. в разделе [поддержка DNS для Active Directory технического справочника](https://go.microsoft.com/fwlink/?LinkID=48147).  
  
> [!NOTE]  
> При реализации несвязанного пространства имен, в котором доменное имя AD DS отличается от основного DNS-суффикса, который используется клиентами, AD DS интеграция с DNS является более сложной. Дополнительные сведения см. в разделе несвязанное [пространство имен](../../ad-ds/plan/../../ad-ds/plan/Disjoint-Namespace.md).  
  
## <a name="in-this-section"></a>В этом разделе  
  
- [Расположение контроллера домена](../../ad-ds/plan/Domain-Controller-Location.md)  
- [Зоны DNS, интегрированные с Active Directory](../../ad-ds/plan/Active-Directory-Integrated-DNS-Zones.md)  
- [Именование компьютеров](../../ad-ds/plan/Computer-Naming.md)  
- [Несвязанное пространство имен](../../ad-ds/plan/../../ad-ds/plan/Disjoint-Namespace.md)  
