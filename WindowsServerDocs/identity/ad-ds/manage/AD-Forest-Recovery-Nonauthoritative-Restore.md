---
title: "Восстановление леса AD — непринудительное восстановление"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/07/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: e4ce1d18-d346-492a-8bca-f85513aa3ac1
ms.technology: identity-adfs
ms.openlocfilehash: 684672491a0574b12e9b117a8e3c9c1f0936f357
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="performing-a-nonauthoritative-restore-of-active-directory-domain-services"></a>Выполнение непринудительное восстановление доменных служб Active Directory 

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2
 
 Чтобы выполнить непринудительное восстановление, выполните следующую процедуру.  
  
 В следующих процедурах используются Wbadmin.exe непринудительное восстановление из Active Directory или доменные службы Active Directory (AD DS). Если вы используете другой решение для резервного копирования или если вы планируете выполнить принудительное восстановление SYSVOL позже в процессе восстановления леса, можно выполнить принудительное восстановление SYSVOL с помощью этих альтернативные методы.  
  
-   Если вы используете службы репликации файлов (FRS) для репликации SYSVOL, выполните действия, описанные в [статья 290762](https://go.microsoft.com/fwlink/?LinkId=148443) базы знаний Майкрософт с помощью **BurFlags** раздела реестра для повторной инициализации наборов реплик службы репликации файлов, или при необходимости, статья 315457 [315457](https://support.microsoft.com/kb/315457)для повторного создания дерева SYSVOL. Чтобы определить, если репликации SYSVOL, FRS, см. [папки SYSVOL определение ли контроллера домена реплицируется с DFSR или FRS](https://msdn.microsoft.com/en-us/library/windows/desktop/cc507518.aspx#determining_whether_a_domain_controller_s_sysvol_folder_is_replicated_by_dfsr_or_frs).  
  
-   Если вы используете репликации распределенной файловой системы (DFS) для репликации SYSVOL, см. раздел [выполнения заслуживающую доверия синхронизацию SYSVOL, реплицированного DFSR](AD-Forest-Recovery-Authoritative-Recovery-SYSVOL.md).  
  
 
## <a name="performing-a-nonauthoritative-restore"></a>Выполнение непринудительное восстановление  
 Используйте следующую процедуру для выполнения непринудительное восстановление AD DS и в то же время принудительное восстановление SYSVOL с помощью wbadmin.exe на Контроллере домена под управлением Windows Server 2012, Windows Server 2008 R2 или Windows Server 2008. Резервное копирование необходимо явным образом включающими данные о состоянии системы; полного резервного копирования сервера, используемый для всего сервера восстановления не будет работать. Дополнительные сведения о создании резервной копии состояния системы см. в разделе [резервное копирование данных состояния системы](AD-Forest-Recovery-Backing-up-System-State.md).  
  
### <a name="to-perform-a-nonauthoritative-restore-of-ad-ds-and-authoritative-restore-of-sysvol-using-wbadminexe"></a>Для выполнения непринудительное восстановление Доменных службах Active Directory и SYSVOL с помощью wbadmin.exe принудительное восстановление  
  
-   Включить **- authsysvol** переключиться в команде восстановления, как показано в следующем примере:  
  
    ```  
    wbadmin start systemstaterecovery <otheroptions> -authsysvol  
    ```  
  
     Например:  
  
    ```  
    wbadmin start systemstaterecovery -version:11/20/2012-13:00 -authsysvol  
    ```  
  
 ![Восстановление](media/AD-Forest-Recovery-Nonauthoritative-Restore/nonauth.png)

## <a name="next-steps"></a>Дальнейшие действия

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
