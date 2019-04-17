---
title: "Восстановление леса AD — заслуживающих доверия синхронизацию SYSVOL"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/07/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 38a1c543-c76d-4b8e-a06b-53742aaa172f
ms.technology: identity-adfs
ms.openlocfilehash: 5bdc619ddf9f28fb074e90dfbf22a7be076a05d9
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="ad-forest-recovery---performing-an-authoritative-synchronization-of-dfsr-replicated-sysvol"></a>Восстановление леса AD — выполнение заслуживающую доверия синхронизацию SYSVOL, реплицированного DFSR  

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

 Существуют различные способы для принудительного восстановления SYSVOL. Можно либо изменить **msDFSR параметры** атрибут или выполнить восстановление состояния системы с помощью wbadmin — authsysvol. Если у вас есть параметр для восстановления резервной копии состояния системы (то есть вы восстанавливаете AD DS на том же экземпляре оборудования и операционной системы), а затем с помощью wbadmin — authsysvol проще. Однако если необходимо выполнить восстановление компьютера, его необходимо отредактировать **msDFSR параметры** атрибута.  
  
 Выполните следующие действия для выполнения заслуживающую доверия синхронизацию SYSVOL (если они реплицируются с помощью DFSR), изменив **msDFSR параметры** атрибута. При репликации SYSVOL с помощью FRS в разделе [статья 290762](https://go.microsoft.com/fwlink/?LinkId=148443).  
  
## <a name="to-perform-an-authoritative-synchronization-of-dfsr-replicated-sysvol"></a>Для выполнения заслуживающую доверия синхронизацию SYSVOL, реплицированного DFSR  
  
1.  Откройте Active Directory-пользователи и компьютеры.  
2.  Нажмите кнопку **представление**и выберите **пользователей, контакты, группы и компьютеры как контейнеры** и **дополнительные функции**. 
![SYSVOL](media/AD-Forest-Recovery-Authoritative-Recovery-SYSVOL/sysvol1.png) 
3.  В древовидном представлении щелкните **контроллеры домена**, имя контроллера домена, можно восстановить **DFSR LocalSettings**, а затем **системный том домена**. 
![SYSVOL](media/AD-Forest-Recovery-Authoritative-Recovery-SYSVOL/sysvol2.png)  
4.  В области сведений щелкните правой кнопкой мыши **подписки SYSVOL**, нажмите кнопку **свойства**и нажмите кнопку **редактор атрибутов**.  
![SYSVOL](media/AD-Forest-Recovery-Authoritative-Recovery-SYSVOL/sysvol3.png) 
5.  Нажмите кнопку **параметры msDFSR**, нажмите кнопку **изменить**, тип **1**и нажмите кнопку **ОК**  
![SYSVOL](media/AD-Forest-Recovery-Authoritative-Recovery-SYSVOL/sysvol4.png) 
6.  Нажмите кнопку **ОК** закрыть редактор атрибутов.  
  
## <a name="next-steps"></a>Дальнейшие действия

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
