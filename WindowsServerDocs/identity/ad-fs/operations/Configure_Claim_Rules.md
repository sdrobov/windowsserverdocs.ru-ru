---
ms.assetid: 20d48afc-2623-43e9-8ed9-aeb9a0505630
title: Настройка правил утверждений
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: b46e228f202eeae7f8cbcf4c1a6851686f905e48
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407631"
---
# <a name="configure-claim-rules"></a>Настройка правил для утверждения

В модели идентификации Claims @ no__t-0based функция службы федерации Active Directory (AD FS) (AD FS) в качестве служб федерации выдает маркер, содержащий набор утверждений. Правила утверждений управляют решениями относительно утверждений, которые AD FS проблемы. Правила утверждений и все данные конфигурации сервера хранятся в базе данных конфигурации AD FS.  
  
AD FS принимает решения на выдачу на основе сведений об удостоверениях, предоставленных ему в виде утверждений и других контекстных сведений. На высоком уровне AD FS работает как обработчик правил, используя один набор заявок в качестве входных данных, выполняет ряд преобразований, а затем возвращает другой набор заявок в качестве выходных данных. 

Следующие разделы помогут вам создать правила, которые AD FS будет обрабатывать: 
  
-   [Создание правила для передачи или фильтрации входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)  
  
-   [Создание правила для разрешения всем пользователям](../../ad-fs/operations/Create-a-Rule-to-Permit-All-Users.md)  
  
-   [Создание правила для разрешения или запрета пользователям на основе входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки атрибутов LDAP в качестве утверждений](../../ad-fs/operations/Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)  
  
-   [Создание правила для отправки членства в группе в качестве утверждения](../../ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)  
  
-   [Создание правила для преобразования входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки утверждения методов аутентификации](../../ad-fs/operations/Create-a-Rule-to-Send-an-Authentication-Method-Claim.md)  
  
-   [Создание правила для отправки утверждений с помощью настраиваемого правила](../../ad-fs/operations/Create-a-Rule-to-Send-Claims-Using-a-Custom-rule.md)  

## <a name="see-also"></a>См. также  
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md) 
