---
ms.assetid: 4163cf03-3bff-426c-9844-4cc2d7897d52
title: Назначение DNS для роли владельца доменных служб Active Directory
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 1b42c60374162b6482b18df2555997e80463d6d9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71390847"
---
# <a name="assigning-the-dns-for-ad-ds-owner-role"></a>Назначение DNS для роли владельца доменных служб Active Directory

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Владелец леса назначает для леса службу доменных имен (DNS) для владельца домен Active Directory Services (AD DS). DNS-сервер для AD DS владельца леса — это человек (или группа людей), ответственный за наблюдение за развертыванием инфраструктуры DNS для AD DS, а также обеспечение регистрации доменных имен в соответствующих Интернет-центрах.  
  
Владелец DNS для AD DS отвечает за создание DNS для AD DS для леса. Если в вашей организации в настоящее время работает служба DNS-сервера, конструктор DNS для существующей службы DNS-сервера работает с DNS-сервером для владельца AD DS, чтобы делегировать корневое DNS-имя леса DNS-серверам, работающим на контроллерах домена.  
  
DNS-владелец для AD DS для леса также хранит контакт с группой DHCP и группой DNS организации и координирует планы отдельных владельцев DNS каждого домена в лесу (если таковые имеются) с этими группами. Владелец DNS для леса гарантирует, что DHCP-и DNS-группы будут задействованы в службе DNS для AD DS процесс проектирования, чтобы каждая группа знала о плане проектирования DNS и преддавала возможность ввода данных в начале.  
  


