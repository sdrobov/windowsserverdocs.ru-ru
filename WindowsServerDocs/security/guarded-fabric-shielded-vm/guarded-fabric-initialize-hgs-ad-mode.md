---
title: Инициализация с помощью доверенного администратора аттестации HGS
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 664404cb72981e162bca016df14847e684d987c1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821835"
---
# <a name="initialize-hgs-using-admin-trusted-attestation"></a>Инициализация с помощью доверенного администратора аттестации HGS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

>[!IMPORTANT]
>Аттестацию с доверием администратора (режим AD) является устаревшим, начиная с Windows Server 2019. Для сред, где аттестацию доверенного платформенного МОДУЛЯ не поддерживается, Настройка [размещения Аттестация ключей](guarded-fabric-initialize-hgs-key-mode.md). Аттестация ключей узла обеспечивает аналогичный уверенность в режим AD и проще в настройке. 


Эти действия зависят от ли при инициализации HGS в новом лесу или существующем лесу бастиона.

1. [Инициализировать кластер HGS в новом лесу (по умолчанию)](guarded-fabric-initialize-hgs-ad-mode-default.md)

   -Или-

   [Инициализировать кластер HGS в существующем лесу бастиона](guarded-fabric-initialize-hgs-ad-mode-bastion.md)

2. [Настроить перенаправление запросов DNS в домене fabric](guarded-fabric-configuring-fabric-dns.md)

3. [Настройте перенаправление запросов DNS и одностороннее доверие в домене HGS](guarded-fabric-configure-dns-forwarding-and-trust.md)



