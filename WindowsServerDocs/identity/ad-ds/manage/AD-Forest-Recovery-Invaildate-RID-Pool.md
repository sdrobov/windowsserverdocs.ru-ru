---
title: "Восстановление леса AD — прекращение действия пула RID"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/07/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 2f5f84df-bd85-4ca4-bdd3-835bd1d45c11
ms.technology: identity-adfs
ms.openlocfilehash: cb024356ae5f872e93448d73ea54b271fe3fae4d
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="ad-forest-recovery---invalidating-the-current-rid-pool"></a>Восстановление леса AD - за которого недействительным текущий пул относительных ИДЕНТИФИКАТОРОВ  

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

 Используйте следующую процедуру, чтобы Windows PowerShell нам сделать недействительным текущий пул относительных ИДЕНТИФИКАТОРОВ на контроллере домена. Windows PowerShell включено по умолчанию в Windows Server 2012 и Windows Server 2008 R2, но не Windows Server 2008 которых должен устанавливаться с помощью **добавить компоненты**. Это может быть [загрузки](https://www.microsoft.com/download/details.aspx?id=20020) для запуска в Windows Server 2003.  
  
 Чтобы убедитесь, что команда выполнена успешно, проверьте наличие события с кодом 16654 (источник — Directory-Services-SAM) в системном журнале в средстве просмотра событий в Windows Server 2012. Это событие не входите в более ранних версиях Windows.  
  
> [!NOTE]
>  После недействительным пул относительных ИДЕНТИФИКАТОРОВ, вы получите сообщение об ошибке при первой попытке создать субъект безопасности (пользователя, компьютера или группы). Попытка создания объекта запускает запрос нового пула относительных ИДЕНТИФИКАТОРОВ. Повтор операции завершается успешно, так как будут распределяться нового пула относительных ИДЕНТИФИКАТОРОВ.  
  
## <a name="to-invalidate-the-current-rid-pool"></a>Чтобы сделать недействительным текущий пул относительных ИДЕНТИФИКАТОРОВ  
  
1.  Откройте сеанс Windows PowerShell с повышенными привилегиями, выполните следующую команду и нажмите клавишу ВВОД:  
  
    ```  
    $Domain = New-Object System.DirectoryServices.DirectoryEntry  
    $DomainSid = $Domain.objectSid  
    $RootDSE = New-Object System.DirectoryServices.DirectoryEntry("LDAP://RootDSE")  
    $RootDSE.UsePropertyCache = $false  
    $RootDSE.Put("invalidateRidPool", $DomainSid.Value)  
    $RootDSE.SetInfo()  
    ```  
  
## <a name="next-steps"></a>Дальнейшие действия

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
