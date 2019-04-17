---
ms.assetid: 9cafa3e1-8118-4a75-a7c2-1dbe40b1a444
title: "Настройка правил утверждений"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: f9e0509e2f870fd0edc7f0c6a241d789945e7ccb
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="configure-claim-rules"></a>Настройка правил для утверждения

>Область применения: Windows Server 2016, Windows Server 2012 R2

В модели идентификации на базе claims\ функции \(AD FS\) служб федерации Active Directory как служб федерации — предоставление токена, содержащего набор утверждений. Правила утверждений определяют решения относительно утверждения, которые выдает AD FS. Правила утверждений и все данные конфигурации сервера хранятся в базе данных конфигурации AD FS.  
  
AD FS делает выдачи решения на основе информации об удостоверениях, предоставляемый ей в виде утверждений и других контекстно-зависимая информация. На высоком уровне службы федерации Active Directory работает процессор правил, выполнив одно набора утверждений в качестве входных данных, выполняет число преобразований, а затем возвращает на другой набор утверждений, как выходные данные. 

Следующие разделы помогут при создании правил, которые будут обрабатывать AD FS: 
  
-   [Создание правила для пропуска или фильтрации входящего утверждения](Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)  
  
-   [Создание правила для разрешения всем пользователям](Create-a-Rule-to-Permit-All-Users.md)  
  
-   [Создание правила для разрешения или запрета пользователям на основании входящего утверждения](Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки атрибутов LDAP как утверждений](Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)  
  
-   [Создание правила для отправки членства в группе как утверждения](Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)  
  
-   [Создание правила для преобразования входящего утверждения](Create-a-Rule-to-Transform-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки утверждения методов проверки подлинности](Create-a-Rule-to-Send-an-Authentication-Method-Claim.md) 
-   [Создание правила для отправки AD FS 1.x утверждения, совместимые](Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md) 
  
-   [Создание правила для отправки утверждений с помощью настраиваемого правила](Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule.md)  

## <a name="see-also"></a>См. также:  
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md) 
