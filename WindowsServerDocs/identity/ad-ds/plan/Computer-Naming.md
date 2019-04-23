---
ms.assetid: f7002265-60fa-40b8-9dd7-4bf131d9320a
title: Именование компьютеров
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: ae2483571d67b4cdb32c2a547b924b1315573da0
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842165"
---
# <a name="computer-naming"></a>Именование компьютеров

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

При присоединении компьютера под управлением операционной системы Windows 2000, Windows XP, Windows Server 2003, Windows Server 2008 или Windows Vista домена, по умолчанию компьютер назначает себе имя. Он назначает себе имя включает в себя имя узла компьютера (то есть имя компьютера в свойствах системы) и имя домена Active Directory, компьютер присоединен доменных имен (DNS) (то есть основной DNS-суффикс в свойствах системы). Объединение имени узла и DNS-имя домена, известен как полное доменное имя (FQDN). Например если компьютер с узлом имя соединения Server1 домене corp.contoso.com, полное ДОМЕННОЕ имя компьютера является server1.corp.contoso.com.  
  
Если компьютер уже имеет другое DNS-имя домена, статически введенные в зону DNS или зарегистрированы с интегрированной службы сервера DNS и динамических DHCP Host Configuration Protocol (), полное ДОМЕННОЕ имя компьютера отличается от имени, который был зарегистрирован ранее. Компьютер может ссылаться либо имя.  
  
Дополнительные сведения о соглашениях об именовании в доменных службах Active Directory (AD DS) см. соглашения об именовании в Active Directory для компьютеров, доменов, сайтов и подразделений ([https://go.microsoft.com/fwlink/?LinkID=106629](https://go.microsoft.com/fwlink/?LinkID=106629)).  
  


