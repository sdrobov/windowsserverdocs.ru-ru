---
title: Восстановление леса AD - разработки Рекламу леса плана восстановления
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 17381f30-55f2-4e00-977a-b701675fa4ff
ms.technology: identity-adds
ms.openlocfilehash: edfc874fe030c6394bc8bda95c49e61951e78f43
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59881785"
---
# <a name="ad-forest-recovery---devising-an-ad-forest-recovery-plan"></a>Восстановление леса AD - разработки Рекламу леса плана восстановления

>Область применения. Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

В зависимости от вашей среды и бизнес-требований может или не может потребоваться выполнить все действия, описанные в этом руководстве для выполнения восстановления успешно леса. Учитывая, что в этом руководстве используется только как шаблон для восстановления леса, крайне важно разработать план восстановления Выборочная лес, который подходит для вашей среды и потребностям вашего бизнеса.  
  
Например в план восстановления леса должен быть карту подробная топология ваших лесов. Карты должны содержать всю информацию о контроллеров домена, например их имена, их ролей и состояние резервного копирования и отношения доверия между ними. Это средство, которое можно использовать для создания карты топологии, см. в разделе [Microsoft Active Directory топологии Diagrammer](https://www.microsoft.com/download/details.aspx?id=13380).  
  
Вы должны практике плана восстановления леса по крайней мере один раз в год. Кроме того рекомендуется для выполнения детализации восстановления леса, когда происходят изменения членства в группе "Администраторы предприятия" или "Администраторы домена". Это гарантирует, что ваш ИТ-персонал сведения полностью понимает плана восстановления леса.

## <a name="next-steps"></a>Следующие шаги

- [Восстановление леса AD — предварительные требования](AD-Forest-Recovery-Prerequisties.md)  
- [Восстановление леса AD — составить план восстановления пользовательских леса](AD-Forest-Recovery-Devising-a-Plan.md)  
- [Восстановление леса AD — определить проблему](AD-Forest-Recovery-Identify-the-Problem.md)
- [Восстановление леса AD — определить способ восстановления](AD-Forest-Recovery-Determine-how-to-Recover.md)
- [Восстановление леса AD - начального восстановления](AD-Forest-Recovery-Perform-initial-recovery.md)  
- [Восстановление леса AD - процедуры](AD-Forest-Recovery-Procedures.md)  
- [Восстановление леса AD — часто задаваемые вопросы](AD-Forest-Recovery-FAQ.md)  
- [Восстановление леса AD — восстановление одного домена в лесу Multidomain](AD-Forest-Recovery-Single-Domain-in-Multidomain-Recovery.md)  
- [Восстановление леса AD - восстановление леса с контроллерами домена Windows Server 2003](AD-Forest-Recovery-Windows-Server-2003.md)
