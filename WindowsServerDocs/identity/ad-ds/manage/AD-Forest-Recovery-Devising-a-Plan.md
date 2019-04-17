---
title: "Восстановление леса AD — разработки AD леса план восстановления"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/07/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 17381f30-55f2-4e00-977a-b701675fa4ff
ms.technology: identity-adfs
ms.openlocfilehash: 6754509ccac352895b9370e63adf1b69548953bf
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
>
# <a name="ad-forest-recovery---devising-an-ad-forest-recovery-plan"></a>Восстановление леса AD — разработки AD леса план восстановления

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

В зависимости от вашей среды и бизнес-требований может и не может потребоваться выполнить все действия, описанные в данном руководстве, для выполнения восстановления успешно леса. Учитывая, что данное руководство служит только шаблон для восстановления леса, крайне важно, что можно разработать план восстановления пользовательских леса, который соответствует вашей среде, а также соответствует потребностям вашей организации.  
  
 Например в ваш план восстановления леса, должен иметь карты подробные топологии вашей лесов. Сопоставления должны содержать всю информацию о контроллеров домена, такие как их имена, их ролей и состояния резервного копирования и отношения доверия между ними. Средство, которое можно использовать для создания карты топологии, в разделе [Microsoft Active Directory топологии Diagrammer](https://www.microsoft.com/download/details.aspx?id=13380).  
  
 Следует Контрольное плана восстановления леса по крайней мере раз в год. Кроме того рекомендуется выполнить переход восстановления леса, при изменении членства в группе "Администраторы предприятия" или "Администраторы домена". Это гарантирует, что ИТ-персонал сведения полностью понимает план восстановления леса.

## <a name="next-steps"></a>Дальнейшие действия
-   [Восстановление леса AD - предварительные требования](AD-Forest-Recovery-Prerequisties.md)  
-   [Восстановление леса AD — разработки план восстановления пользовательских леса](AD-Forest-Recovery-Devising-a-Plan.md)  
- [Восстановление леса AD — выявление проблемы](AD-Forest-Recovery-Identify-the-Problem.md)
-   [Восстановление леса AD — определить, как восстановить](AD-Forest-Recovery-Determine-how-to-Recover.md)
-   [Восстановление леса AD — выполнения начальной восстановления](AD-Forest-Recovery-Perform-initial-recovery.md)  
-   [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)  
-   [Восстановление леса AD — вопросы и ответы](AD-Forest-Recovery-FAQ.md)  
-   [Восстановление леса AD — восстановление одного домена в лесу Multidomain](AD-Forest-Recovery-Single-Domain-in-Multidomain-Recovery.md)  
-   [Восстановление леса AD — восстановление леса с контроллеров домена Windows Server 2003](AD-Forest-Recovery-Windows-Server-2003.md) 
