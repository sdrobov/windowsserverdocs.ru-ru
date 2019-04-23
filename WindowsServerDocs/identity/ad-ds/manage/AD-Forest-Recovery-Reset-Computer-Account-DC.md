---
title: Восстановление леса AD - Сброс учетной записи компьютера на контроллере домена
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 4e1a6070-df0a-4dfe-8773-899a010bfabd
ms.technology: identity-adds
ms.openlocfilehash: 388b460196888d4ca0cd12218972197afb6d49c5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59852765"
---
# <a name="ad-forest-recovery---resetting-the-computer-account-on-the-dc"></a>Восстановление леса AD - Сброс учетной записи компьютера на контроллере домена

>Область применения. Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

 Используйте следующую процедуру, чтобы сбросить пароль учетной записи компьютера контроллера домена. 
  
## <a name="to-reset-the-computer-account-password-of-the-domain-controller"></a>Чтобы сбросить пароль учетной записи компьютера контроллера домена  

1. В командной строке введите следующую команду и нажмите клавишу ВВОД:  

   ```
   netdom help resetpwd  
   ```
  
2. Используйте синтаксис, что эта команда предоставляет для с помощью средства командной строки Netdom, чтобы сбросить пароль учетной записи компьютера, например:  

   ```
   netdom resetpwd /server:domain controller name /userD:administrator /passwordd:*  
   ```  
  
    Где *имя контроллера домена* локальный контроллер домена, если выполняется восстановление. 
  
   > [!NOTE]
   > Эту команду необходимо запустить дважды.
  
## <a name="next-steps"></a>Следующие шаги

- [Руководство по восстановлению из леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD - процедуры](AD-Forest-Recovery-Procedures.md)
