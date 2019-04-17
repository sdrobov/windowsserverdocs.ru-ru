---
ms.assetid: 20d48afc-2623-43e9-8ed9-aeb9a0505630
title: "Настройка правил утверждений"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 259e2b266b64a3b34c237cfe209a3558124c8ef2
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="configure-claim-rules"></a>Настройка правил для утверждения

>Область применения: Windows Server 2016, Windows Server 2012 R2

В модели идентификации на базе claims\ функции федерации служб Active Directory (AD FS) как служб федерации — предоставление токена, содержащего набор утверждений. Правила утверждений определяют решения относительно утверждения, которые выдает AD FS. Правила утверждений и все данные конфигурации сервера хранятся в базе данных конфигурации AD FS.  
  
AD FS делает выдачи решения на основе информации об удостоверениях, предоставляемый ей в виде утверждений и других контекстно-зависимая информация. На высоком уровне службы федерации Active Directory работает процессор правил, выполнив одно набора утверждений в качестве входных данных, выполняет число преобразований, а затем возвращает на другой набор утверждений, как выходные данные. 

Следующие разделы помогут при создании правил, которые будут обрабатывать AD FS: 
  
-   [Создание правила для пропуска или фильтрации входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)  
  
-   [Создание правила для разрешения всем пользователям](../../ad-fs/operations/Create-a-Rule-to-Permit-All-Users.md)  
  
-   [Создание правила для разрешения или запрета пользователям на основании входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки атрибутов LDAP как утверждений](../../ad-fs/operations/Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)  
  
-   [Создание правила для отправки членства в группе как утверждения](../../ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)  
  
-   [Создание правила для преобразования входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки утверждения методов проверки подлинности](../../ad-fs/operations/Create-a-Rule-to-Send-an-Authentication-Method-Claim.md)  
  
-   [Создание правила для отправки утверждений с помощью настраиваемого правила](../../ad-fs/operations/Create-a-Rule-to-Send-Claims-Using-a-Custom-rule.md)  

## <a name="see-also"></a>См. также:  
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md) 
