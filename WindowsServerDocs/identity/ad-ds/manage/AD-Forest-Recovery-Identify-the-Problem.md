---
title: Восстановление леса AD — выявление проблемы
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: 5a291f65-794e-4fc3-996e-094c5845a383
ms.technology: identity-adds
ms.openlocfilehash: 73b7ef8dc6093ae28c4b5076e7b332b704090b4f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80823997"
---
# <a name="identify-the-problem"></a>Выявление проблемы

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2
  
При возникновении симптомов сбоя в масштабе леса, например в журналах событий или других решениях для мониторинга, следует работать с служба поддержки Майкрософт, чтобы определить причину сбоя и оценить возможные способы их устранения.  

## <a name="examples-of-forest-wide-failures"></a>Примеры сбоев в масштабе леса

- Все контроллеры домена логически повреждены или физически повреждены до точки, в которой непрерывность бизнес-процессов невозможна; Например, все бизнес-приложения, зависящие от AD DS, являются нефункциональными.  
- Фальшивый администратор скомпрометирован Active Directoryной среде.  
- Злоумышленник намеренно (или администратор случайно) выполняет сценарий, который распространяет повреждение данных в пределах леса.  
- Злоумышленник намеренно (или администратор случайно) расширяет схему Active Directory с помощью вредоносных или конфликтующих изменений.  
- Злоумышленник может установить вредоносное программное обеспечение на контроллерах домена, и вам было рекомендовано служба поддержки Майкрософт восстановить лес из резервной копии.  
  
   > [!IMPORTANT]
   >  В этом документе не рассматриваются рекомендации по обеспечению безопасности для восстановления несанкционированных или скомпрометированных лесов. Как правило, для защиты среды рекомендуется использовать приемы защиты от-хэша. Дополнительные сведения см. в разделе [Устранение атак Pass-The-hash (PtH) и других методов кражи учетных данных](https://www.microsoft.com/download/details.aspx?id=36036).
  
- Ни один из контроллеров домена не может реплицироваться с партнерами по репликации.  
- Невозможно внести изменения в AD DS на любом контроллере домена.  
- Новые контроллеры домена не могут быть установлены ни в одном домене.  
  
## <a name="next-steps"></a>Следующие шаги

- [Восстановление леса AD — необходимые условия](AD-Forest-Recovery-Prerequisties.md)  
- [Восстановление леса AD — Девисинг план восстановления пользовательского леса](AD-Forest-Recovery-Devising-a-Plan.md)  
- [Восстановление леса AD. обнаружение проблемы](AD-Forest-Recovery-Identify-the-Problem.md)
- [Восстановление леса AD. Определение способа восстановления](AD-Forest-Recovery-Determine-how-to-Recover.md)
- [Восстановление леса AD — выполнение начального восстановления](AD-Forest-Recovery-Perform-initial-recovery.md)  
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)  
- [Восстановление леса AD — часто задаваемые вопросы](AD-Forest-Recovery-FAQ.md)  
- [Восстановление леса Active Directory. Восстановление одного домена в лесу с несколькими доменами](AD-Forest-Recovery-Single-Domain-in-Multidomain-Recovery.md)  
- [Восстановление леса Active Directory — восстановление леса с контроллерами домена Windows Server 2003](AD-Forest-Recovery-Windows-Server-2003.md) 
