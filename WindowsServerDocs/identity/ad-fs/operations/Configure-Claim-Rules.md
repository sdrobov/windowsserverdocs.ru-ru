---
ms.assetid: 9cafa3e1-8118-4a75-a7c2-1dbe40b1a444
title: Настройка правил утверждений
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: d0dd8528e5fbd6829b313a3e6bc47f5a17f6a12f
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66189724"
---
# <a name="configure-claim-rules"></a>Настройка правил для утверждения

В утверждениях\-удостоверений на основе модели, функция служб федерации Active Directory \(AD FS\) как федерации служб является выпустить маркер, содержащий набор утверждений. Правила утверждений управляют решения относительно утверждений, выдаваемых AD FS. Правила утверждений и все данные конфигурации сервера хранятся в базе данных конфигурации AD FS.  
  
AD FS делает выдачи решения, которые основаны на удостоверениях, который предоставляется в форме утверждений и других контекстных сведений. На высоком уровне AD FS работает как обработчик правил, выполнив одно набор утверждений в качестве входных данных, выполняет ряд преобразований и возвращает другой набор утверждений как выходные данные. 

Следующие разделы будут полезны для создания правил, которые будут обрабатывать AD FS: 
  
-   [Создайте правило, чтобы пропуск или Фильтрация входящего утверждения](Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)  
  
-   [Создание правила для разрешения всем пользователям](Create-a-Rule-to-Permit-All-Users.md)  
  
-   [Создание правила для разрешения или запрета пользователям на основе входящего утверждения](Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки атрибутов LDAP как утверждений](Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)  
  
-   [Создание правила для отправки членства в группе в качестве утверждения](Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)  
  
-   [Создание правила для преобразования входящего утверждения](Create-a-Rule-to-Transform-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки утверждения методов аутентификации](Create-a-Rule-to-Send-an-Authentication-Method-Claim.md) 
-   [Создание правила для отправки AD FS 1.x утверждения, совместимые](Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md) 
  
-   [Создание правила для отправки утверждений с помощью настраиваемого правила](Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule.md)  

## <a name="see-also"></a>См. также  
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md) 
