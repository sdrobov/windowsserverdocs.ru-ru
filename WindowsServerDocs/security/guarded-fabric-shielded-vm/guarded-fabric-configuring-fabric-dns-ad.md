---
title: Настройка DNS-сервера структуры для защищенных узлов (AD)
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 074b6d09-f16e-49bf-b88a-377139d35067
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 411b845d57c36916dcbc73d51675f5d9f92bfa0e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386765"
---
# <a name="configure-the-fabric-dns-for-guarded-hosts"></a>Настройка структуры DNS для защищенных узлов

>Область применения. Windows Server 2016


>[!IMPORTANT]
>Режим AD является устаревшим, начиная с Windows Server 2019. Для сред, в которых невозможно подтвердить аттестацию доверенного платформенного модуля, настройте [аттестацию ключа узла](guarded-fabric-initialize-hgs-key-mode.md). Аттестация ключа узла обеспечивает аналогичные гарантии в режиме AD и проще в настройке. 

Администратор структуры должен настроить структуру DNS, чтобы разрешить защищенным узлам разрешать кластер HGS. [Администратор HGS](/WindowsServerDocs/virtualization/guarded-fabric-shielded-vm/guarded-fabric-setting-up-the-host-guardian-service-hgs.md)должен уже настроить кластер HGS.



[!INCLUDE [Configure fabric DNS](../../../includes/guarded-fabric-configure-fabric-dns.md)] 


## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Настройка DNS в HGS и одностороннего отношения доверия](guarded-fabric-configure-dns-forwarding-and-trust.md)
