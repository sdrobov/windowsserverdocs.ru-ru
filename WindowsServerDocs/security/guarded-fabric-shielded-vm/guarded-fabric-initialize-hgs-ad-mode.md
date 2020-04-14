---
title: Инициализация HGS с помощью аттестации, доверенной администратором
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: b7c0b88071a28953ddda8abb57a805ef119511e0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856677"
---
# <a name="initialize-hgs-using-admin-trusted-attestation"></a>Инициализация HGS с помощью аттестации, доверенной администратором

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

>[!IMPORTANT]
>Служба аттестации, доверенная для администраторов (режим AD), устарела, начиная с Windows Server 2019. Для сред, в которых невозможно подтвердить аттестацию доверенного платформенного модуля, настройте [аттестацию ключа узла](guarded-fabric-initialize-hgs-key-mode.md). Аттестация ключа узла обеспечивает аналогичные гарантии в режиме AD и проще в настройке. 


Эти действия зависят от того, инициализируется ли HGS в новом или существующем лесу бастиона:

1. [Инициализация кластера HGS в новом лесу (по умолчанию)](guarded-fabric-initialize-hgs-ad-mode-default.md)

   -Или-

   [Инициализация кластера HGS в существующем лесу бастиона](guarded-fabric-initialize-hgs-ad-mode-bastion.md)

2. [Настройка пересылки DNS в домене структуры](guarded-fabric-configuring-fabric-dns.md)

3. [Настройка перенаправления DNS и одностороннего доверия в домене HGS](guarded-fabric-configure-dns-forwarding-and-trust.md)



