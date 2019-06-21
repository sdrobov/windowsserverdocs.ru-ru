---
title: Восстановление леса AD - непринудительное восстановление
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: e4ce1d18-d346-492a-8bca-f85513aa3ac1
ms.technology: identity-adds
ms.openlocfilehash: 65e33e6507d2affc4d07cc0780a7baf91a170a09
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280590"
---
# <a name="performing-a-nonauthoritative-restore-of-active-directory-domain-services"></a>Выполняет принудительное восстановление доменных служб Active Directory 

>Область применения. Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

Чтобы выполнить непринудительное восстановление, выполните следующую процедуру.  
  
В следующих процедурах используются Wbadmin.exe для выполнения непринудительное восстановление Active Directory или доменных служб Active Directory (AD DS). При использовании другого решения резервного копирования, или если вы собираетесь выполнить Полномочное восстановление SYSVOL позже в процессе восстановления леса, нужно выполнить Полномочное восстановление SYSVOL с помощью этих альтернативных методов.  
  
- Если вы используете службы репликации файлов (FRS) для репликации SYSVOL, выполните действия, описанные в [статьи 290762](https://go.microsoft.com/fwlink/?LinkId=148443) в базе знаний Майкрософт, с помощью **BurFlags** раздел реестра для повторной инициализации репликации FRS Задает или при необходимости статьи 315457 [315457](https://support.microsoft.com/kb/315457)для перестроения дерева SYSVOL. Чтобы определить, если SYSVOL реплицируется с FRS, см. в разделе [папки SYSVOL определение ли контроллера домена реплицируется с DFSR или FRS](https://msdn.microsoft.com/library/windows/desktop/cc507518.aspx#determining_whether_a_domain_controller_s_sysvol_folder_is_replicated_by_dfsr_or_frs).  
- Если вы используете репликации распределенной файловой системы (DFS) для репликации SYSVOL, см. в разделе [выполнения заслуживающую доверия синхронизацию SYSVOL с репликацией DFSR](AD-Forest-Recovery-Authoritative-Recovery-SYSVOL.md).  

## <a name="performing-a-nonauthoritative-restore"></a>Выполнение непринудительное восстановление

Используйте следующую процедуру для выполнения непринудительное восстановление AD DS и SYSVOL Полномочное восстановление в то же время с помощью wbadmin.exe на Контроллере домена, выполняется Windows Server 2012, Windows Server 2008 R2 или Windows Server 2008. Резервное копирование необходимо явно включить данные о состоянии системы; Архив всего сервера, используемый для восстановления всего сервера не будет работать. Дополнительные сведения о создании резервной копии состояния системы см. в разделе [резервное копирование данных состояния системы](AD-Forest-Recovery-Backing-up-System-State.md).  
  
### <a name="to-perform-a-nonauthoritative-restore-of-ad-ds-and-authoritative-restore-of-sysvol-using-wbadminexe"></a>Для выполнения непринудительное восстановление, службы AD DS и принудительное восстановление с помощью wbadmin.exe SYSVOL  
  
- Включить **- authsysvol** переключиться в команду восстановления, как показано в следующем примере:  

   ```  
   wbadmin start systemstaterecovery <otheroptions> -authsysvol  
   ```  

   Пример:  

   ```  
   wbadmin start systemstaterecovery -version:11/20/2012-13:00 -authsysvol  
   ```  
  
![Восстановление](media/AD-Forest-Recovery-Nonauthoritative-Restore/nonauth.png)

## <a name="next-steps"></a>Следующие шаги

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
