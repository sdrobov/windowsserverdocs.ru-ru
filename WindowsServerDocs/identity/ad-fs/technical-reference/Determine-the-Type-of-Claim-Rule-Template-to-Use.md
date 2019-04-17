---
ms.assetid: 696a29b2-d627-4c9a-a384-9c8aaf50bd23
title: "Определение необходимого типа шаблона правил утверждений"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 129cd83be4cd8302bd170ba87aad58c50f636006
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="determine-the-type-of-claim-rule-template-to-use"></a>Определение необходимого типа шаблона правил утверждений

>Область применения: Windows Server 2016, Windows Server 2012 R2

Важной частью проектирования \(AD FS\) инфраструктуру служб федерации Active Directory Определение полного набора правил утверждений — и соответствующих утверждений шаблонов правил следует использовать для их создания — для каждого партнера, который будет участвовать в федерации с вашей организацией. Создание правила с помощью шаблонов правил для утверждений в управления AD FS оснастка.  
  
Каждый набор правил утверждений, который вы настраиваете может быть связан только с одним федеративным отношением доверия. Это означает, что нельзя создать набор правил в одном отношении доверия и использовать их для других отношений доверия в службе федерации. Вместо этого вы можно легко создать правила из утверждений шаблонов правил для, помогающих быстро создать необходимый набор утверждений, согласованных между каждым участником федерации и вашей организации.  
  
Дополнительные сведения о правилах и шаблонах правил см. в разделе [The Role of Claim Rules](The-Role-of-Claim-Rules.md).  
  
Прежде чем приступить к определению типов шаблонов правил утверждений, которые следует использовать, ответьте на следующие вопросы:  
  
-   Какие утверждения будут предоставляться вашими доверенными поставщиками утверждений?  
  
-   Каким утверждениям вы доверяете от каждого поставщика утверждений?  
  
-   Какие утверждения требуются проверяющими сторонами, доверяющими этой службе федерации?  
  
-   Какие утверждения вы готовы сообщать каждой проверяющей стороне?  
  
-   Какие пользователи должны иметь доступ к каждой проверяющей стороне?  
  
Ответы на эти вопросы будет помогут вам планировать надежную архитектуру правил для утверждений. Он также помочь в создании плавного авторизации и получить доступ к стратегии управления и повысить эффективность вашей рабочей группы развертывания во время выпуска.  
  
В следующем разделе вы узнаете о тип шаблонов правил следует выбрать для вашей среды, исходя из вашей бизнес-требований.  
  
## <a name="claim-rule-template-types"></a>Типы шаблонов правил утверждений  
В следующей таблице описаны все типы шаблонов правил утверждений, которые можно использовать для создания правил с помощью управления AD FS оснастка и введите преимущества использования одного шаблона перед другим.  
  
|Тип шаблона правила|Описание|Преимущества|Недостатки|  
|----------------------|---------------|--------------|-----------------|  
|Пропуск или Фильтрация входящего утверждения|Используется для создания правила, которое будет пропускать все значения утверждений для выбранного типа утверждения или фильтровать утверждения, основываясь на значениях утверждения, чтобы пропускались только определенные значения утверждений для выбранного типа утверждения.<br /><br />Дополнительные сведения см. в разделе [When to Use a Pass Through or Filter Claim Rule](When-to-Use-a-Pass-Through-or-Filter-Claim-Rule.md).|— Используется для выбора конкретных утверждений, которые должны быть приняты или выданы без изменений|-Утверждений, тип и значение невозможно изменить|  
|Преобразование входящего утверждения|Используется для создания правила, которое может выбрать входящее утверждение и сопоставить его с другим типом утверждения или сопоставить его значение с новым значением утверждения.<br /><br />Дополнительные сведения см. в разделе [When to Use a Transform Claim Rule](When-to-Use-a-Transform-Claim-Rule.md).|-Можно использовать для нормализации типов или значений утверждений<br />-Может заменять суффикс e\ почты входящего утверждения|-Более сложных замен строк требуется настраиваемое правило|  
|Отправка атрибутов LDAP как утверждений|Используется для создания правила, которое будет выбрать атрибуты из хранилища атрибутов LDAP для отправки в виде утверждений для проверяющей стороны.<br /><br />Дополнительные сведения см. в разделе [When to Use a Send LDAP Attributes as Claims Rule](When-to-Use-a-Send-LDAP-Attributes-as-Claims-Rule.md).|— Позволяет получать утверждения из любого хранилища атрибутов AD DS\ или AD LDS<br />-Выдаваться несколько утверждений можно с помощью одного правила|-Производительность низкая, как результат поиска учетной записи<br />-Не удается использовать настраиваемый фильтр LDAP для запроса|  
|Отправка членства в группах как утверждения|Используется для создания правила, которое может отправлять указанный тип утверждения и значение, если пользователь является членом группы безопасности Active Directory. С помощью этого правила на основе выбранной группы выбранного будет отправляться только одно утверждение.<br /><br />Дополнительные сведения см. в разделе [When to Use a Send Group Membership as Claim Rule](When-to-Use-a-Send-Group-Membership-as-a-Claim-Rule.md).|— Высокая производительность при выдаче групповых утверждений — поиск не учетной записи|-Пользователь должен быть членом локальной группы Active Directory|  
|Отправка утверждений с помощью настраиваемого правила|Используется для создания настраиваемого правила, которое предоставляет дополнительные варианты по сравнению со стандартным шаблоном правила. Выполняется запись языка правил для утверждений настраиваемые правила с помощью AD FS.<br /><br />Дополнительные сведения см. в разделе [When to Use a Custom Claim Rule](When-to-Use-a-Custom-Claim-Rule.md).|— Используется для получения утверждений из хранилища атрибутов SQL<br />— Позволяет указать настраиваемый фильтр LDAP<br />— Используется для выдачи PPID<br />-Может использоваться с настраиваемым хранилищем атрибутов<br />— Позволяет добавлять утверждения только во входной набор утверждений<br />— Используется для отправки утверждений на основе нескольких входящих утверждений|-Более сложная настройка \-дополнительное время может потребоваться, чтобы сначала изучить язык правил утверждений|  
|Разрешать или запрещать пользователям на основании входящего утверждения|Используется для создания правила, которое будет разрешать или запрещать доступ пользователей к проверяющей стороне на основе типа и значения входящего утверждения.<br /><br />Дополнительные сведения см. в разделе [When to Use an Authorization Claim Rule](When-to-Use-an-Authorization-Claim-Rule.md).|-Упрощает процесс авторизации|— Требует, чтобы только одного типа утверждения и одного значения утверждения указать<br />-Поддерживает сопоставление шаблонов для значений утверждений|  
|Разрешить всем пользователям|Используется для создания правила, которое разрешает всем пользователям доступ к проверяющей стороне.<br /><br />Дополнительные сведения см. в разделе [When to Use an Authorization Claim Rule](When-to-Use-an-Authorization-Claim-Rule.md).|-Простая настройка|-Менее безопасен, чем разрешать или запрещать пользователям на основе на основе шаблона входящего утверждения|  
  
