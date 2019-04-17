---
ms.assetid: f7002265-60fa-40b8-9dd7-4bf131d9320a
title: "Именование компьютеров"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: d0dbe2da76a1cf3d1a4dd74183b5dd7106ef17b9
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="computer-naming"></a>Именование компьютеров

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

При присоединении компьютера под управлением операционной системы Windows 2000, Windows XP, Windows Server 2003, Windows Server 2008 или Windows Vista домена по умолчанию компьютер назначает себе имя. Он назначает себе имя включает имя узла компьютера (то есть, имя компьютера в свойствах системы) и имя системы доменных имен (DNS) в домен Active Directory, что компьютер присоединен (то есть, основной DNS-суффикс в свойствах системы). Объединение имени узла и DNS-имя домена, называется полное доменное имя (FQDN). Например если компьютер с именем узла Server1 присоединения к домену corp.contoso.com полное ДОМЕННОЕ имя компьютера — server1.corp.contoso.com.  
  
Если на компьютере уже установлено другое имя домена DNS, статически был введен в зону DNS или зарегистрированный службой интегрированная служба сервера DNS и динамических DHCP Host Configuration Protocol (), полное доменное имя компьютера, отличается от имени, которое ранее было зарегистрировано. Компьютер можно ссылаться по либо имя.  
  
Дополнительные сведения о контекстах именования в доменных службах Active Directory (AD DS) см. в разделе соглашения о наименовании в Active Directory для компьютеров, доменов, узлов и подразделений ([https://go.microsoft.com/fwlink/?LinkID=106629](https://go.microsoft.com/fwlink/?LinkID=106629)).  
  


