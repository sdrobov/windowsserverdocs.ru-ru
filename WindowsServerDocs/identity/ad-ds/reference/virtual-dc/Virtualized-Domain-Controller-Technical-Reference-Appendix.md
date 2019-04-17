---
ms.assetid: 73a4deba-7da6-4eae-8fdd-2a4d369f9cbb
title: "Приложение технического справочника контроллера домена виртуализированных"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 2e7f264a098b6f67d98c9aa47ec5794374b8920d
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="virtualized-domain-controller-technical-reference-appendix"></a>Приложение технического справочника контроллера домена виртуализированных

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Содержание раздела  
  
-   [Терминология](../../../ad-ds/reference/virtual-dc/../../../ad-ds/reference/virtual-dc/Virtualized-Domain-Controller-Technical-Reference-Appendix.md#BKMK_Terms)  
  
-   [FixVDCPermissions.ps1](../../../ad-ds/reference/virtual-dc/../../../ad-ds/reference/virtual-dc/Virtualized-Domain-Controller-Technical-Reference-Appendix.md#BKMK_FixPDCPerms)  
  
## <a name="BKMK_Terms"></a>Терминология  
  
-   **Моментальный снимок** -состояние виртуальной машины в определенный момент времени. Она зависит, в цепочке предыдущих снимков съемки, а на оборудовании, а также на платформа виртуализации.  
  
-   **Клон** — завершения и разделения копия виртуальной машины. Это зависит от виртуального оборудования (низкоуровневая оболочка).  
  
-   **Полная копия** -полный клон является независимая копия виртуальной машины, которые предоставляет ресурсы не родительской виртуальной машины после завершения операции клонирования. Текущую операцию полный клон полностью отделен от родительской виртуальной машины.  
  
-   **Разностный диск** -копия виртуальной машины, которые предоставляет виртуальные диски виртуальной машины родительского текущих способом. Обычно это экономит место на диске и позволяет нескольким виртуальным машинам использовать одну и ту же установку программного обеспечения.  
  
-   **Копирование виртуальной Машины**— системы копирование файлов всех связанных файлов и папок из виртуальной машины.  
  
-   **Копирование файлов VHD** -копия виртуальной машины виртуальный жесткий ДИСК  
  
-   **ИД создания виртуальной Машины** - 128-разрядное целое число, учитывая к виртуальной машине, низкоуровневой оболочкой. Этот идентификатор сохраняется в памяти и сброс каждый раз, когда моментального снимка. Структура использует механизм зависящего от гипервизора для предоставления доступа к ИД создания Виртуальной машины на виртуальной машине. Реализация Hyper-V предоставляет идентификатор таблицы ACPI виртуальной машины.  
  
-   **Импорт и экспорт** -функция Hyper-V, которая позволяет пользователю сохранить виртуальную машину целиком (виртуальных Машин файлы, виртуального жесткого диска и конфигурации компьютера). Затем она позволяет пользователям с помощью этого набора файлов, чтобы перевести машину обратно на том же компьютере, одной виртуальной машины (восстановление) на другом компьютере, как же виртуальной Машины (перемещения) или новой виртуальной Машины (скопировать)  
  
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
  


