---
ms.assetid: 4163cf03-3bff-426c-9844-4cc2d7897d52
title: Назначение DNS для роли владельца доменных служб Active Directory
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: dde9ed6035b30ba5b5b96b7132d25a1f8a1c0b8c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59884025"
---
# <a name="assigning-the-dns-for-ad-ds-owner-role"></a>Назначение DNS для роли владельца доменных служб Active Directory

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Владелец леса назначает доменных имен (DNS) для владельца доменных служб Active Directory (AD DS) для леса. DNS для леса AD DS владельца — это лицо (или группа людей) кто отвечает за контроль развертывания DNS для инфраструктуры AD DS и убедиться, (при необходимости) доменных имен зарегистрировано в соответствующие органы Интернет.  
  
DNS для AD DS владельца несет ответственность за DNS для разработки AD DS для леса. Если ваша организация в настоящее время работает служба DNS-сервера, конструкторе DNS для существующей службы DNS-сервер работает в DNS для AD DS владельца для делегирования DNS-имя леса корневой DNS-серверы, работающих на контроллерах домена.  
  
DNS для владельца AD DS для леса также хранит обратитесь к группе конфигурации протокола DHCP (Dynamic Host) и группу DNS-сервера организации и соответствующим планы отдельных владельцев DNS для каждого домена в лесу (если таковые имеются) эти группы. Владельца DNS для леса гарантирует, что группы DHCP и DNS участвуют в DNS для процесса разработки AD DS, чтобы каждая группа учитывает плана разработки DNS и может предоставить входные данные раньше.  
  


