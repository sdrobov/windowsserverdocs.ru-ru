---
title: Инициализация HGS с помощью аттестации, доверенной администратором
ms.custom: na
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 491754e8bcaad4524084604b78c7c6ed0fdee295
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402357"
---
# <a name="initialize-hgs-using-admin-trusted-attestation"></a>Инициализация HGS с помощью аттестации, доверенной администратором

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

>[!IMPORTANT]
>Служба аттестации, доверенная для администраторов (режим AD), устарела, начиная с Windows Server 2019. Для сред, в которых невозможно подтвердить аттестацию доверенного платформенного модуля, настройте [аттестацию ключа узла](guarded-fabric-initialize-hgs-key-mode.md). Аттестация ключа узла обеспечивает аналогичные гарантии в режиме AD и проще в настройке. 


Эти действия зависят от того, инициализируется ли HGS в новом или существующем лесу бастиона:

1. [Инициализация кластера HGS в новом лесу (по умолчанию)](guarded-fabric-initialize-hgs-ad-mode-default.md)

   -Или-

   [Инициализация кластера HGS в существующем лесу бастиона](guarded-fabric-initialize-hgs-ad-mode-bastion.md)

2. [Настройка пересылки DNS в домене структуры](guarded-fabric-configuring-fabric-dns.md)

3. [Настройка перенаправления DNS и одностороннего доверия в домене HGS](guarded-fabric-configure-dns-forwarding-and-trust.md)



