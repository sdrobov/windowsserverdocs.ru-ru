---
title: Восстановление леса AD - аннулирования пул относительных ИДЕНТИФИКАТОРОВ
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 2f5f84df-bd85-4ca4-bdd3-835bd1d45c11
ms.technology: identity-adds
ms.openlocfilehash: 46115991e48da301a8a739009bac27415ebe73df
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842515"
---
# <a name="ad-forest-recovery---invalidating-the-current-rid-pool"></a>Восстановление леса AD - аннулирования текущий пул относительных ИДЕНТИФИКАТОРОВ  

>Область применения. Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

Используйте следующую процедуру, чтобы Windows PowerShell нам сделать недействительным текущий пул относительных ИДЕНТИФИКАТОРОВ на контроллере домена. Windows PowerShell включено по умолчанию на Windows Server 2012 и Windows Server 2008 R2, но не Windows Server 2008 где он должен быть установлен с помощью **добавить компоненты**. Это может быть [загрузки](https://www.microsoft.com/download/details.aspx?id=20020) под управлением Windows Server 2003.  

Чтобы проверить команда выполнена успешно, проверьте событие с кодом 16654 (источник — Directory-Services-SAM) в системном журнале в средстве просмотра событий в Windows Server 2012. Это событие не входите в более ранних версиях Windows.  
  
> [!NOTE]
> После вы недействительным пул относительных ИДЕНТИФИКАТОРОВ, вы получите ошибку при попытке сначала создать субъект безопасности (пользователя, компьютера или группы). Попытка создания объекта активирует запрос нового пула относительных ИДЕНТИФИКАТОРОВ. Повторите попытку операции завершается успешно, поскольку будет выделен нового пула относительных ИДЕНТИФИКАТОРОВ.  
  
## <a name="to-invalidate-the-current-rid-pool"></a>Чтобы сделать недействительным текущий пул относительных ИДЕНТИФИКАТОРОВ  
  
- Откройте сеанс Windows PowerShell с повышенными привилегиями, выполните следующую команду и нажмите клавишу ВВОД:  

   ```powershell
   $Domain = New-Object System.DirectoryServices.DirectoryEntry  
   $DomainSid = $Domain.objectSid  
   $RootDSE = New-Object System.DirectoryServices.DirectoryEntry("LDAP://RootDSE")  
   $RootDSE.UsePropertyCache = $false  
   $RootDSE.Put("invalidateRidPool", $DomainSid.Value)  
   $RootDSE.SetInfo()  
   ```  

## <a name="next-steps"></a>Следующие шаги

- [Руководство по восстановлению из леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD - процедуры](AD-Forest-Recovery-Procedures.md)
