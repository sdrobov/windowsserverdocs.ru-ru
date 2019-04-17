---
ms.assetid: 1b21b0a9-1fe6-4fd1-8a25-92e578d774ed
title: "Развертывание прокси-сервера федерации"
description: 
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: b914141a0445febd3961b688aadc2f444b2eee7b
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="deploying-federation-server-proxies"></a>Развертывание прокси-сервера федерации

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Для развертывания прокси-серверов федерации в \(AD FS\) служб федерации Active Directory, выполните все задачи в [контрольный список: Настройка Up a Federation Server Proxy](Checklist--Setting-Up-a-Federation-Server-Proxy.md).  
  
> [!NOTE]  
> Когда вы используете этот контрольный список, мы рекомендуем сначала ознакомиться ссылки на прокси-сервера федерации, руководство по планированию [AD FS Design Guide in Windows Server 2012](https://technet.microsoft.com/library/dd807036.aspx) перед началом процедуры по настройке серверов. Следующий контрольный список содержит лучше понять процесс проектирования и развертывания для федерации прокси-серверов.  
  
## <a name="about-federation-server-proxies"></a>О прокси-серверов федерации  
Прокси-серверов федерации — это компьютеры под управлением Windows Server® 2012 и программного обеспечения AD FS, настроенных вручную выступать в роли прокси-сервера. Для предоставления промежуточной службы между Интернет-клиентом и сервером федерации, находится за брандмауэром в сети организации, можно использовать прокси-серверов федерации в организации.  
  
> [!NOTE]  
> Хотя на одном компьютере нельзя установить сервер федерации и прокси-сервера роли сервера федерации, сервер федерации может выполнять функции прокси-сервера сервера федерации. Дополнительные сведения см. в разделе [When to Create a Federation Server](https://technet.microsoft.com/library/dd807101.aspx).  
  
Во время установки программного обеспечения AD FS на компьютере Windows Server® 2012 и настроить его для работы в роли прокси-сервера, компьютер становится прокси-сервера федерации.  
  

