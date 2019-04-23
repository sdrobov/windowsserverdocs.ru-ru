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
ms.openlocfilehash: f9e0509e2f870fd0edc7f0c6a241d789945e7ccb
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59829415"
---
# <a name="configure-claim-rules"></a>Настройка правил для утверждения

>Область применения. Windows Server 2016, Windows Server 2012 R2

В утверждениях\-удостоверений на основе модели, функция служб федерации Active Directory \(AD FS\) как федерации служб является выпустить маркер, содержащий набор утверждений. Правила утверждений управляют решения относительно утверждений, выдаваемых AD FS. Правила утверждений и все данные конфигурации сервера хранятся в базе данных конфигурации AD FS.  
  
AD FS делает выдачи решения, которые основаны на удостоверениях, который предоставляется в форме утверждений и других контекстных сведений. На высоком уровне AD FS работает как обработчик правил, выполнив одно набор утверждений в качестве входных данных, выполняет ряд преобразований и возвращает другой набор утверждений как выходные данные. 

Следующие разделы будут полезны для создания правил, которые будут обрабатывать AD FS: 
  
-   [Создайте правило, чтобы пропуск или Фильтрация входящего утверждения](Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)  
  
-   [Создайте правило, чтобы разрешить всем пользователям](Create-a-Rule-to-Permit-All-Users.md)  
  
-   [Создайте правило, чтобы разрешать или запрещать пользователям на основании входящего утверждения](Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки атрибутов LDAP как утверждений](Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)  
  
-   [Создайте правило, чтобы отправлять членство в группе как утверждение](Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)  
  
-   [Создание правила для преобразования входящего утверждения](Create-a-Rule-to-Transform-an-Incoming-Claim.md)  
  
-   [Создание правила для отправки утверждение для метода проверки подлинности](Create-a-Rule-to-Send-an-Authentication-Method-Claim.md) 
-   [Создание правила для отправки AD FS 1.x утверждения, совместимые](Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md) 
  
-   [Создание правила для отправки утверждений с помощью настраиваемого правила](Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule.md)  

## <a name="see-also"></a>См. также  
[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md) 
