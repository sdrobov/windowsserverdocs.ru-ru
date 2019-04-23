---
ms.assetid: 73a4deba-7da6-4eae-8fdd-2a4d369f9cbb
title: Приложение технического справочника по виртуализированным контроллерам домена
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 9e3a5cc2c71455bb040f1311bdbfed1ac7e213fb
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59832235"
---
# <a name="virtualized-domain-controller-technical-reference-appendix"></a>Приложение технического справочника по виртуализированным контроллерам домена

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Содержание раздела  
  
-   [Терминология](../../../ad-ds/reference/virtual-dc/../../../ad-ds/reference/virtual-dc/Virtualized-Domain-Controller-Technical-Reference-Appendix.md#BKMK_Terms)  
  
-   [FixVDCPermissions.ps1](../../../ad-ds/reference/virtual-dc/../../../ad-ds/reference/virtual-dc/Virtualized-Domain-Controller-Technical-Reference-Appendix.md#BKMK_FixPDCPerms)  
  
## <a name="BKMK_Terms"></a>Терминология  
  
-   **Моментальный снимок** -состояние виртуальной машины в определенной точке во времени. Он зависит, в цепочке предыдущих моментальных снимков, а на оборудовании и на платформе виртуализации.  
  
-   **Клон** — завершить и отдельные копии виртуальной машины. Это зависит от виртуального оборудования (гипервизор).  
  
-   **Полный клон** -полный клон — независимая копия виртуальной машины, нет ресурсов с родительской виртуальной машины после операции клонирования. Текущую операцию полного клона полностью отделен от родительской виртуальной машины.  
  
-   **Разностный диск** -копию виртуальной машины, виртуальные диски с родительской виртуальной машины в текущей форме. Обычно это экономит место на диске и позволяет нескольким виртуальным машинам использовать одну и ту же установку программного обеспечения.  
  
-   **Копирование виртуальной Машины**— файл копии системы все связанные файлы и папки виртуальной машины.  
  
-   **Копирование файлов виртуального жесткого диска** -копию виртуального жесткого диска виртуальной машины  
  
-   **ИД создания виртуальной Машины** — 128-разрядное целое число, присвоенное виртуальной машине низкоуровневой оболочкой. Этот идентификатор сохраняется в памяти и сбросить каждый раз при применении моментального снимка. Предоставляет ИД создания виртуальной Машины в виртуальной машине используются механизм независимой от низкоуровневой оболочки. Реализация Hyper-V предоставляет идентификатор в таблице ACPI виртуальной машины.  
  
-   **Импорт и экспорт** -функция Hyper-V, которая позволяет пользователю сохранить всей виртуальной машины (виртуальной Машины файлы виртуального жесткого диска и конфигурации компьютера). Затем она позволяет пользователям с помощью этого набора файлов для перевода компьютера на одном компьютере с той же виртуальной Машине (восстановление), на другом компьютере как той же виртуальной Машине (перемещение) или новую виртуальную Машину (копия)  
  
## <a name="BKMK_FixPDCPerms"></a>FixVDCPermissions.ps1  
  
```  
# Unsigned script, requires use of set-executionpolicy remotesigned -force  
# You must run the Windows PowerShell console as an elevated administrator  
  
# Load Active Directory Windows PowerShell Module and switch to AD DS drive  
import-module activedirectory  
cd ad:  
  
## Get Domain NC  
$domainNC = get-addomain  
  
## Get groups and obtain their SIDs   
$dcgroup = get-adgroup "Cloneable Domain Controllers"  
  
$sid1 = (get-adgroup $dcgroup).sid  
  
## Get the DACL of the domain  
$acl = get-acl $domainNC  
  
## The following object specific ACE grants extended right 'Allow a DC to create a clone of itself' for the CDC group to the Domain NC  
## 3e0f7e18-2c7a-4c10-ba82-4d926db99a3e is the schemaIDGuid for 'DS-Clone-Domain-Controller"  
  
$objectguid = new-object Guid 3e0f7e18-2c7a-4c10-ba82-4d926db99a3e  
$ace1 = new-object System.DirectoryServices.ActiveDirectoryAccessRule $sid1,"ExtendedRight","Allow",$objectguid  
  
## Add the ACE in the ACL and set the ACL on the object   
  
$acl.AddAccessRule($ace1)  
set-acl -aclobject $acl $domainNC  
write-host "Done writing new VDC permissions."  
cd c:   
```  
  


