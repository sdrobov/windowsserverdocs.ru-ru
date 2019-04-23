---
title: Развертывание инфраструктуры программно-конфигурируемой сети
description: В этом разделе содержит ссылки на разделы о том, как развернуть инфраструктуру Microsoft программно-определяемой сети (SDN) с помощью сценариев в Windows Server 2016.
manager: dougkim
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.service: virtual-network
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 6c665c88-df28-4150-81d4-a47e9fa5255c
ms.author: pashort
ms.date: 08/23/2018
ms.openlocfilehash: 30d5597cdeb76d636cdf5236228f035999a6bdf6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59878025"
---
# <a name="deploy-a-software-defined-network-infrastructure"></a>Развертывание инфраструктуры программно-определяемой сети

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Развертывание инфраструктуры программно определяемой сети (SDN) корпорации Майкрософт.   
  
Эти развертывания включают все технологии, необходимые для полнофункциональной инфраструктуры, включая виртуализацию сети Hyper-V (HNV), сетевые контроллеры, программные подсистемы балансировки нагрузки (SLB/MUX) и шлюзов.  
  
## <a name="set-up-sdn-infrastructure-in-the-vmm-fabric"></a>Настройка инфраструктуры SDN в структуре VMM



  
-   [Настройка инфраструктуры программно определяемой сети (SDN) в структуре VMM](https://docs.microsoft.com/system-center/vmm/deploy-sdn)  
  
    Этот метод следует используйте, если вы хотите включить System Center виртуальной машины Manger (VMM) для управления своей инфраструктуре SDN.  
 
## <a name="deploy-sdn-infrastructure-using-scripts"></a>Развертывание инфраструктуры SDN с помощью сценариев
 
-   [Развертывание инфраструктуры программно-определяемой сети с помощью сценариев](../../sdn/deploy/Deploy-a-Software-Defined-Network-infrastructure-using-scripts.md)  
  
    Этот метод следует используйте, если вы не хотите управлять своей инфраструктуре SDN с помощью VMM, или если вы настраивали другой способ управления.  


## <a name="deploy-individual-sdn-technologies-instead-of-an-entire-infrastructure"></a>Развертывания отдельных технологий SDN вместо всей инфраструктуры  
 Если вы хотите развернуть отдельные технологии SDN, а не всю инфраструктуру, см. в разделе:  
[Развертывание программного обеспечения определяемых сетевых технологий, с помощью Windows PowerShell](Deploy-Software-Defined-Network-Technologies-using-Windows-PowerShell.md).    
  




  


## <a name="related-topics"></a>См. также
- [Программно-конфигурируемой сети (SDN)](../Software-Defined-Networking--SDN-.md)  
- [Технологии SDN](../technologies/Software-Defined-Networking-Technologies.md)  
- [Планирование SDN](../plan/plan-a-software-defined-network-infrastructure.md)  
- [Управление SDN](../manage/manage-sdn.md)
- [Безопасность для SDN](../security/sdn-security-top.md)
- [Устранение неполадок SDN](../troubleshoot/Troubleshoot-Software-Defined-Networking.md)