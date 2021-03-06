---
title: Восстановление леса Active Directory — неполномочное восстановление
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: e4ce1d18-d346-492a-8bca-f85513aa3ac1
ms.technology: identity-adds
ms.openlocfilehash: 52c3e4fb20009a37a7f778907639390f9b00cfcb
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86960956"
---
# <a name="performing-a-nonauthoritative-restore-of-active-directory-domain-services"></a>Выполнение неполномочного восстановления служб домен Active Directory 

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

Чтобы выполнить неполномочное восстановление, выполните следующую процедуру.  
  
В следующих процедурах используется Wbadmin.exe для выполнения неполномочного восстановления Active Directory или служб домен Active Directory (AD DS). Если вы используете другое решение для резервного копирования или планируете выполнить полномочное восстановление SYSVOL позже в процессе восстановления леса, можно выполнить полномочное восстановление SYSVOL с помощью следующих альтернативных методов:  
  
- Если для репликации SYSVOL используется служба репликации файлов (FRS), выполните действия, описанные в [статье 290762](https://go.microsoft.com/fwlink/?LinkId=148443) базы знаний Майкрософт, с помощью раздела реестра **BurFlags** для повторной инициализации наборов реплик FRS или при необходимости см. статью 315457 [315457](https://support.microsoft.com/kb/315457)для перестроения дерева SYSVOL. Сведения о том, как определить, реплицируется ли SYSVOL с помощью FRS, см. в разделе [Определение репликации папки SYSVOL контроллера домена с помощью DFSR или FRS](/windows/win32/vss/backing-up-and-restoring-an-frs-replicated-sysvol-folder#determining_whether_a_domain_controller_s_sysvol_folder_is_replicated_by_dfsr_or_frs).  
- Если для репликации SYSVOL используется репликация распределенная файловая система (DFS), см. статью [выполнение полномочной синхронизации SYSVOL, реплицированной](AD-Forest-Recovery-Authoritative-Recovery-SYSVOL.md)с помощью DFSR.  

## <a name="performing-a-nonauthoritative-restore"></a>Выполнение неполномочного восстановления

Используйте следующую процедуру для выполнения неполномочного восстановления AD DS и полномочного восстановления SYSVOL одновременно с помощью wbadmin.exe на контроллере домена под управлением Windows Server 2012, Windows Server 2008 R2 или Windows Server 2008. Резервная копия должна содержать данные состояния системы явным образом. полное резервное копирование сервера, используемое для полного восстановления сервера, не будет работать. Дополнительные сведения о создании резервной копии состояния системы см. [в разделе Резервное копирование данных о состоянии системы](AD-Forest-Recovery-Backing-up-System-State.md).  
  
### <a name="to-perform-a-nonauthoritative-restore-of-ad-ds-and-authoritative-restore-of-sysvol-using-wbadminexe"></a>Чтобы выполнить неполномочное восстановление AD DS и полномочного восстановления SYSVOL с помощью wbadmin.exe  
  
- Включите параметр **-ауссисвол** в команду восстановления, как показано в следующем примере:  

   ```  
   wbadmin start systemstaterecovery <otheroptions> -authsysvol  
   ```  

   Например.  

   ```  
   wbadmin start systemstaterecovery -version:11/20/2012-13:00 -authsysvol  
   ```  
  
![Восстановить](media/AD-Forest-Recovery-Nonauthoritative-Restore/nonauth.png)

## <a name="next-steps"></a>Дальнейшие шаги

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
