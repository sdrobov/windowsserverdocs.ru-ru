---
ms.assetid: c20231dd-2b83-4494-9385-1172272e00d6
title: Обновление имеющихся доменов и развертывание новых доменов
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: e07965b079a953d062f5bdaaca8f9f9f32500610
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59851795"
---
# <a name="determining-whether-to-upgrade-existing-domains-or-deploy-new-domains"></a>Обновление имеющихся доменов и развертывание новых доменов

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Каждый домен в проекте будет иметь новый домен или существующего обновления домена. Необходимо переместить пользователей из существующих доменов, которые не обновляются в новых доменов.  
  
Перемещение учетных записей между доменами может повлиять на конечных пользователей. Перед тем, как перенос пользователей в новый домен или при обновлении существующих доменов, оцените долгосрочного административные преимущества нового домена AD DS со стоимостью перемещение пользователей в домен.  
  
Дополнительные сведения об обновлении доменов Active Directory для Windows Server 2008, см. в разделе [обновления доменов Active Directory до Windows Server 2008 и Windows Server 2008 R2 доменов доменных Служб](https://technet.microsoft.com/library/cc731188.aspx).  
  
Дополнительные сведения о реструктуризации доменов AD DS внутри и между лесами см. в разделе Active Directory Migration Tool версии 3.1 руководство по миграции ([https://go.microsoft.com/fwlink/?LinkId=93678](https://go.microsoft.com/fwlink/?LinkId=93678)).  
  
Для рабочего листа, чтобы помочь в документировании планов для новых и обновленных доменов, загрузите Job_Aids_Designing_and_Deploying_Directory_and_Security_Services.zip из задания вспомогательные средства для Windows Server 2003 Deployment Kit ([ https://go.microsoft.com/fwlink/?LinkID=102558 ](https://go.microsoft.com/fwlink/?LinkID=102558)) и откройте «Домена планирование» (DSSLOGI_5.doc).  
  


