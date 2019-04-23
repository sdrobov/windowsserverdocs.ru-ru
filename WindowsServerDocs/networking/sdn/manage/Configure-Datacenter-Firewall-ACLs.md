---
title: Настройка списка управления доступом для брандмауэра центра обработки данных
description: Можно применить определенные списки управления доступом к сетевым интерфейсам.  Если списки также устанавливаются на виртуальной подсети, к которой подключен сетевой интерфейс, как применяются списки управления доступом, но сетевой интерфейс списки управления доступом имеет приоритет над виртуальной подсети списки управления доступом.
manager: dougkim
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 25f18927-a63e-44f3-b02a-81ed51933187
ms.author: pashort
author: shortpatti
ms.date: 08/23/2018
ms.openlocfilehash: 77a7706e39da265eedd65342a0ccf2174ab050ea
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59853405"
---
# <a name="configure-datacenter-firewall-access-control-lists-acls"></a>Настройка брандмауэра центра обработки данных, списки управления доступом (ACL)

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

После создания списка ACL и назначен виртуальной подсети, может потребоваться переопределить это значение по умолчанию список управления Доступом в виртуальной подсети с определенного ACL для отдельного сетевого интерфейса.  В этом случае применяемыми определенные списки управления доступом к сетевых интерфейсов, подключенных к виртуальным ЛС, а не виртуальной сети. Если у вас есть списков управления доступом виртуальной подсети, подключенной к сетевому интерфейсу, оба списки управления доступом применяются и устанавливает приоритеты для сетевого интерфейса ACL выше ACL виртуальной подсети.

>[!IMPORTANT]
>Если вы не создан список управления Доступом и назначен виртуальной сети, см. в разделе [используйте списки управления доступом (ACL) для управления центра обработки данных сети трафик проходит](Use-Access-Control-Lists--ACLs--to-Manage-Datacenter-Network-Traffic-Flow.md) для создания списка ACL и назначить его виртуальной подсети.  

В этом разделе мы покажем, как добавить список управления Доступом к сетевому интерфейсу. Мы также покажем, как удалить ACL из сетевого интерфейса с помощью Windows PowerShell и REST API сетевого контроллера.

- [Пример: Добавление списка ACL к сетевому интерфейсу](#example-add-an-acl-to-a-network-interface)
- [Пример: Удалить ACL из сетевого интерфейса с помощью Windows Powershell и REST API сетевого контроллера](#example-remove-an-acl-from-a-network-interface-by-using-windows-powershell-and-the-network-controller-rest-api)


## <a name="example-add-an-acl-to-a-network-interface"></a>Пример. Добавление списка ACL к сетевому интерфейсу
В этом примере мы демонстрируется добавление списка ACL к виртуальной сети. 

>[!TIP]
>Это также можно добавить список управления Доступом, в то же время, создайте сетевой интерфейс.

1. Получите или создайте сетевой интерфейс, к которому добавляется ACL.
 
   ```PowerShell
   $nic = get-networkcontrollernetworkinterface -ConnectionUri $uri -ResourceId "MyVM_Ethernet1"
   ```
 
2. Получите или создайте ACL, вы добавите к сетевому интерфейсу.
 
   ```PowerShell
   $acl = get-networkcontrolleraccesscontrollist -ConnectionUri $uri -resourceid "AllowAllACL"
   ```
 
3. Назначение списка управления Доступом к свойству AccessControlList сетевого интерфейса
 
   ```PowerShell
    $nic.properties.ipconfigurations[0].properties.AccessControlList = $acl
   ```
 
4. Добавьте сетевой интерфейс в сетевой контроллер
 
   ```
   new-networkcontrollernetworkinterface -ConnectionUri $uri -Properties $nic.properties -ResourceId $nic.resourceid
   ```
 
## <a name="example-remove-an-acl-from-a-network-interface-by-using-windows-powershell-and-the-network-controller-rest-api"></a>Пример. Удалить ACL из сетевого интерфейса с помощью Windows Powershell и REST API сетевого контроллера
В этом примере мы покажем, как удалить список управления Доступом. Удаление ACL применяется набор правил по умолчанию сетевому интерфейсу. Набор правил по умолчанию разрешает весь исходящий трафик, но блокирует весь входящий трафик.

>[!NOTE]
>Если вы хотите разрешить весь входящий трафик, необходимо выполнить предыдущий [пример](#example-add-an-acl-to-a-network-interface) добавляемый ACL, который разрешает весь входящий трафик и весь исходящий трафик.


1. Получение списка ACL для сетевого интерфейса, из которого будут удалены.<br>
   ```PowerShell
   $nic = get-networkcontrollernetworkinterface -ConnectionUri $uri -ResourceId "MyVM_Ethernet1"
   ```
 
2. Назначьте $NULL свойству AccessControlList IP-конфигурации.<br>
   ```PowerShell
   $nic.properties.ipconfigurations[0].properties.AccessControlList = $null
   ```
 
3. Добавьте объект сетевого интерфейса на сетевом контроллере.<br>
   ```PowerShell
   new-networkcontrollernetworkinterface -ConnectionUri $uri -Properties $nic.properties -ResourceId $nic.resourceid
   ```
