---
title: Восстановление леса AD - заслуживающие доверия синхронизацию SYSVOL
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 38a1c543-c76d-4b8e-a06b-53742aaa172f
ms.technology: identity-adds
ms.openlocfilehash: 246a2ea589ee05110362cff99d50e93a0a18c2b9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59827005"
---
# <a name="ad-forest-recovery---performing-an-authoritative-synchronization-of-dfsr-replicated-sysvol"></a>Восстановление леса AD — выполнение заслуживающую доверия синхронизацию SYSVOL с репликацией DFSR  

>Область применения. Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

Существуют разные способы выполнить Полномочное восстановление SYSVOL. Можно изменить **msDFSR-Options** атрибут или выполните восстановление состояния системы с помощью wbadmin — authsysvol. Если у вас есть параметр, чтобы восстановить резервную копию состояния системы (то есть вы восстанавливаете AD DS к тому же экземпляру оборудования и операционной системы), а затем с помощью wbadmin — authsysvol проще. Но если вам нужно выполнить восстановление исходного состояния системы, то необходимо изменить **msDFSR-Options** атрибута.  

Выполните следующие действия для выполнения заслуживающую доверия синхронизацию SYSVOL (если она реплицируется с помощью DFSR), изменив **msDFSR-Options** атрибута. При репликации SYSVOL с помощью FRS, см. в разделе [статьи 290762](https://go.microsoft.com/fwlink/?LinkId=148443).  

## <a name="to-perform-an-authoritative-synchronization-of-dfsr-replicated-sysvol"></a>Для выполнения заслуживающую доверия синхронизацию SYSVOL с репликацией DFSR  

1. Откройте оснастку "Пользователи и компьютеры Active Directory".  
2. Нажмите кнопку **представление**, а затем выберите **пользователей, контакты, группы и компьютеры как контейнеры** и **дополнительные функции**. 

   ![SYSVOL](media/AD-Forest-Recovery-Authoritative-Recovery-SYSVOL/sysvol1.png) 

3. В древовидном представлении щелкните **контроллеры домена**, имя контроллера домена, которые были восстановлены, **DFSR LocalSettings**, а затем **системный том домена**. 

   ![SYSVOL](media/AD-Forest-Recovery-Authoritative-Recovery-SYSVOL/sysvol2.png)  

4. В области сведений щелкните правой кнопкой мыши **подписки SYSVOL**, нажмите кнопку **свойства**и нажмите кнопку **редактор атрибутов**.  

   ![SYSVOL](media/AD-Forest-Recovery-Authoritative-Recovery-SYSVOL/sysvol3.png) 

5. Нажмите кнопку **msDFSR-Options**, нажмите кнопку **изменить**, тип **1**и нажмите кнопку **ОК**  

   ![SYSVOL](media/AD-Forest-Recovery-Authoritative-Recovery-SYSVOL/sysvol4.png) 

6. Нажмите кнопку **ОК** чтобы закрыть редактор атрибутов.  
  
## <a name="next-steps"></a>Следующие шаги

- [Руководство по восстановлению из леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD - процедуры](AD-Forest-Recovery-Procedures.md)
