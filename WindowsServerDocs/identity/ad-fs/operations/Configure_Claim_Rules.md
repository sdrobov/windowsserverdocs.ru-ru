---
ms.assetid: 20d48afc-2623-43e9-8ed9-aeb9a0505630
title: Настройка правил утверждений
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: e7eedd907c07c2aaef1670c5db3a6892ca3e650d
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189626"
---
# <a name="configure-claim-rules"></a>Настройка правил для утверждения

В утверждениях\-удостоверений на основе модели, функция федерации служб Active Directory (AD FS) как службы федерации — выпустить маркер, содержащий набор утверждений. Правила утверждений управляют решения относительно утверждений, выдаваемых AD FS. Правила утверждений и все данные конфигурации сервера хранятся в базе данных конфигурации AD FS.  
  
AD FS делает выдачи решения, которые основаны на удостоверениях, который предоставляется в форме утверждений и других контекстных сведений. На высоком уровне AD FS работает как обработчик правил, выполнив одно набор утверждений в качестве входных данных, выполняет ряд преобразований и возвращает другой набор утверждений как выходные данные. 

Следующие разделы будут полезны для создания правил, которые будут обрабатывать AD FS: 
  
-   [Создайте правило, чтобы пропуск или Фильтрация входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)  
  
-   [Создание правила для разрешения всем пользователям](../../ad-fs/operations/Create-a-Rule-to-Permit-All-Users.md)  
  
-   [Создание правила для разрешения или запрета пользователям на основе входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки атрибутов LDAP как утверждений](../../ad-fs/operations/Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)  
  
-   [Создание правила для отправки членства в группе в качестве утверждения](../../ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)  
  
-   [Создание правила для преобразования входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки утверждения методов аутентификации](../../ad-fs/operations/Create-a-Rule-to-Send-an-Authentication-Method-Claim.md)  
  
-   [Создание правила для отправки утверждений с помощью настраиваемого правила](../../ad-fs/operations/Create-a-Rule-to-Send-Claims-Using-a-Custom-rule.md)  

## <a name="see-also"></a>См. также  
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md) 
