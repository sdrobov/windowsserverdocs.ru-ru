---
ms.assetid: 4163cf03-3bff-426c-9844-4cc2d7897d52
title: "Назначение DNS для роли владельца доменных служб Active Directory"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: e393cbf32aa5a13ff22044eabb8c575508baaf79
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="assigning-the-dns-for-ad-ds-owner-role"></a>Назначение DNS для роли владельца доменных служб Active Directory

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Владелец леса назначает доменных имен (DNS) для владельца доменных служб Active Directory (AD DS) для леса. DNS для леса AD DS владельца является пользователь (или группа людей) кто отвечает за надзора за все развертывание DNS для инфраструктуры AD DS и убедитесь, что (при необходимости) доменные имена зарегистрированных в соответствующие органы Интернета.  
  
DNS-сервер для AD DS владельца отвечает за DNS для проектирования Доменных службах Active Directory для леса. Если ваша организация в настоящее время работает служба DNS-сервера, конструктор существующая служба DNS-сервер DNS работает с DNS для владельца Доменных службах Active Directory для делегирования DNS-имя леса корневой DNS-серверы, на контроллерах домена.  
  
В DNS для леса AD DS владельцем также поддерживает контакт с протокол динамической настройки узла (DHCP) и группа DNS организации и координирует планы отдельных владельцев DNS для каждого домена в лесу (при наличии) этих групп. Владелец DNS для леса гарантирует участвующих группы DHCP- и DNS-сервера в DNS для процесса разработки AD DS, чтобы каждая группа знает плана разработки DNS и раньше предоставить входные данные.  
  


