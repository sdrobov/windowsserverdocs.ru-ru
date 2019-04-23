---
title: Настройте структуру DNS для защищенных узлов (AD)
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 074b6d09-f16e-49bf-b88a-377139d35067
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 8a2ddc0f2ab495b2500d4bfe48f3ee83c333c769
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842755"
---
# <a name="configure-the-fabric-dns-for-guarded-hosts"></a>Настройте структуру DNS для защищенных узлов

>Область применения. Windows Server 2016


>[!IMPORTANT]
>Режим AD является устаревшим, начиная с Windows Server 2019. Для сред, где аттестацию доверенного платформенного МОДУЛЯ не поддерживается, Настройка [размещения Аттестация ключей](guarded-fabric-initialize-hgs-key-mode.md). Аттестация ключей узла обеспечивает аналогичный уверенность в режим AD и проще в настройке. 

Администратор структуры необходимо для настройки структуры, который принимает DNS, чтобы разрешить защищенные узлы разрешить кластер HGS. Кластер HGS уже должен быть [, HGS администратор настроил](/WindowsServerDocs/virtualization/guarded-fabric-shielded-vm/guarded-fabric-setting-up-the-host-guardian-service-hgs.md).



[!INCLUDE [Configure fabric DNS](../../../includes/guarded-fabric-configure-fabric-dns.md)] 


## <a name="next-step"></a>Дальнейшие действия

>[!div class="nextstepaction"]
[Настройка HGS DNS и одностороннее отношение доверия](guarded-fabric-configure-dns-forwarding-and-trust.md)
