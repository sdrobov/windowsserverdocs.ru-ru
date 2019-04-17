---
title: "Восстановление леса AD — Переустановка учетной записи компьютера на контроллере домена"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/07/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 4e1a6070-df0a-4dfe-8773-899a010bfabd
ms.technology: identity-adfs
ms.openlocfilehash: 588510a27f56abb4497b2f80fa0281a858a7e8eb
ms.sourcegitcommit: 84a2bdcb92ba6af45781fab9727617e50fa5e911
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2017
---
# <a name="ad-forest-recovery---resetting-the-computer-account-on-the-dc"></a>Восстановление леса AD — Переустановка учетной записи компьютера на контроллере домена 

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

 Используйте следующую процедуру для сброса пароля учетной записи компьютера контроллера домена.  
  
## <a name="to-reset-the-computer-account-password-of-the-domain-controller"></a>Чтобы сбросить пароль учетной записи компьютера контроллера домена  
  
1.  В командной строке введите следующую команду и нажмите клавишу ВВОД:  
  
    ```  
    netdom help resetpwd  
    ```  
  
2.  Используйте синтаксис, что эта команда предоставляет для с помощью программы командной строки Netdom, чтобы сбросить пароль учетной записи компьютера, например:  
  
    ```  
    netdom resetpwd /server:domain controller name /userD:administrator /passwordd:*  
    ```  
  
     Где *имя контроллера домена* локальный контроллер домена, если выполняется восстановление.  
  
    > [!NOTE]
    >  Эту команду необходимо выполнить дважды.  
  
## <a name="next-steps"></a>Дальнейшие действия

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
