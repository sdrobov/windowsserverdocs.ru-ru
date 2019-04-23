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
ms.openlocfilehash: 259e2b266b64a3b34c237cfe209a3558124c8ef2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59871635"
---
# <a name="configure-claim-rules"></a>Настройка правил для утверждения

>Область применения. Windows Server 2016, Windows Server 2012 R2

В утверждениях\-удостоверений на основе модели, функция федерации служб Active Directory (AD FS) как службы федерации — выпустить маркер, содержащий набор утверждений. Правила утверждений управляют решения относительно утверждений, выдаваемых AD FS. Правила утверждений и все данные конфигурации сервера хранятся в базе данных конфигурации AD FS.  
  
AD FS делает выдачи решения, которые основаны на удостоверениях, который предоставляется в форме утверждений и других контекстных сведений. На высоком уровне AD FS работает как обработчик правил, выполнив одно набор утверждений в качестве входных данных, выполняет ряд преобразований и возвращает другой набор утверждений как выходные данные. 

Следующие разделы будут полезны для создания правил, которые будут обрабатывать AD FS: 
  
-   [Создайте правило, чтобы пропуск или Фильтрация входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)  
  
-   [Создайте правило, чтобы разрешить всем пользователям](../../ad-fs/operations/Create-a-Rule-to-Permit-All-Users.md)  
  
-   [Создайте правило, чтобы разрешать или запрещать пользователям на основании входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки атрибутов LDAP как утверждений](../../ad-fs/operations/Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)  
  
-   [Создайте правило, чтобы отправлять членство в группе как утверждение](../../ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)  
  
-   [Создание правила для преобразования входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки утверждение для метода проверки подлинности](../../ad-fs/operations/Create-a-Rule-to-Send-an-Authentication-Method-Claim.md)  
  
-   [Создание правила для отправки утверждений с помощью настраиваемого правила](../../ad-fs/operations/Create-a-Rule-to-Send-Claims-Using-a-Custom-rule.md)  

## <a name="see-also"></a>См. также  
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md) 
