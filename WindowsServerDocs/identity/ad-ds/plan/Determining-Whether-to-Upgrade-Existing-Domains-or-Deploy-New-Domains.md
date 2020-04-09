---
ms.assetid: c20231dd-2b83-4494-9385-1172272e00d6
title: Обновление имеющихся доменов и развертывание новых доменов
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 1e058240bc971d949de279407701e57cd021712c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80822606"
---
# <a name="determining-whether-to-upgrade-existing-domains-or-deploy-new-domains"></a>Обновление имеющихся доменов и развертывание новых доменов

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Каждый домен в вашем проекте будет либо новым доменом, либо существующим обновленным доменом. Пользователи из существующих доменов, которые не обновляются, должны быть перемещены в новые домены.  
  
Перемещение учетных записей между доменами может повлиять на конечных пользователей. Прежде чем принять решение о том, следует ли переместить пользователей в новый домен или обновить существующие домены, оцените долгосрочные преимущества администрирования нового домена AD DS в отношении стоимости перемещения пользователей в домен.  
  
Дополнительные сведения об обновлении доменов Active Directory до Windows Server 2008 см. в разделе [обновление доменов Active Directory до Windows server 2008 и Windows server 2008 R2 AD DS Domains](https://technet.microsoft.com/library/cc731188.aspx).  
  
Дополнительные сведения о реструктуризации AD DS доменов в лесах и между лесами см. в разделе Средство миграции Active Directory версии 3,1 ([https://go.microsoft.com/fwlink/?LinkId=93678](https://go.microsoft.com/fwlink/?LinkId=93678)).  
  
Чтобы помочь вам в документировании планов для новых и обновленных доменов, скачайте Job_Aids_Designing_and_Deploying_Directory_and_Security_Services. zip из вспомогательных средств для пакета развертывания Windows Server 2003 ([https://go.microsoft.com/fwlink/?LinkID=102558](https://go.microsoft.com/fwlink/?LinkID=102558)) и откройте "Планирование домена" (DSSLOGI_5. doc).  
  


