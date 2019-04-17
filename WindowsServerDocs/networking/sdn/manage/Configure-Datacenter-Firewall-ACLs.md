---
title: Настройте брандмауэр центра обработки данных списки управления доступом (ACL)
description: Этот раздел является частью программного обеспечения определены сетевые руководство о том, как управление рабочими нагрузками клиента и виртуальные сети в Windows Server 2016.
manager: brianlic
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
ms.openlocfilehash: d5f7c4baad24a720e073857cb6c835167e5b419b
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="configure-datacenter-firewall-access-control-lists-acls"></a>Настройте брандмауэр центра обработки данных списки управления доступом (ACL)

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Сетевые интерфейсы можно применить определенные списки управления доступом.  Если списки управления доступом также задаются в виртуальной подсети, к которой подключен сетевой интерфейс, как применяются списки управления доступом, но сетевой интерфейс ACL приоритет над виртуальной подсети списки управления доступом.

Этот раздел содержит следующие разделы.

- [Пример: Добавление списка ACL для сетевого интерфейса](#bkmk_addacl)
- [Пример: Удаление ACL из сетевого интерфейса с помощью Windows Powershell и API-Интерфейс REST сетевого контроллера](#bkmk_removeacl)

##<a name="bkmk_addacl"></a>Пример: Добавление списка ACL для сетевого интерфейса

В разделе [используйте списки управления доступом (ACL) для управления центра обработки данных сетевого трафика потока](Use-Access-Control-Lists--ACLs--to-Manage-Datacenter-Network-Traffic-Flow.md) вы узнали, как создать список управления Доступом и назначить виртуальной подсети.  Однако в некоторых случаях может потребоваться переопределить что по умолчанию ACL в подсети virtaul с определенного ACL для отдельных сетевых интерфейса.  Вам также потребуется для применения ACL сетевых интерфейсов, подключенных к виртуальным ЛС вместо виртуальных сетей.

В этом примере демонстрируется добавление списка ACL для виртуальной сети. 

>[!NOTE]
>Можно также добавить ACL в то же время, необходимо создать сетевой интерфейс.

###<a name="step-1-get-or-create-the-network-interface-to-which-you-will-add-the-acl"></a>Шаг 1: Получите или создайте сетевого интерфейса, для которого необходимо добавить ACL

    $nic = get-networkcontrollernetworkinterface -ConnectionUri $uri -ResourceId "MyVM_Ethernet1"

###<a name="step-2-get-or-create-the-acl-you-will-add-to-the-network-interface"></a>Шаг 2: Получение или создать список управления Доступом, который будет добавлен к сетевому интерфейсу
Следующий пример команды можно использовать для получения или создания ACL. 

    $acl = get-networkcontrolleraccesscontrollist -ConnectionUri $uri -resourceid "AllowAllACL"

###<a name="step-3-assign-the-acl-to-the-accesscontrollist-property-of-the-network-interface"></a>Шаг 3: Назначьте ACL свойству AccessControlList сетевого интерфейса
Следующий пример команды можно использовать, чтобы присвоить свойство AccessControlList ACL.

    $nic.properties.ipconfigurations[0].properties.AccessControlList = $acl

###<a name="step-4-add-the-network-interface-in-network-controller"></a>Шаг 4: Добавление сетевого интерфейса в сетевого контроллера
Следующий пример команды можно использовать для добавления в сетевой контроллер сетевого интерфейса.

    new-networkcontrollernetworkinterface -ConnectionUri $uri -Properties $nic.properties -ResourceId $nic.resourceid


##<a name="bkmk_removeacl"></a>Пример: Удаление ACL из сетевого интерфейса с помощью Windows Powershell и API-Интерфейс REST сетевого контроллера
Этот пример можно использовать, если вы хотите удалить ACL. При удалении ACL набор правил по умолчанию применяются к сетевому интерфейсу.

Набор правил по умолчанию разрешает весь исходящий трафик, но блокирует весь входящий трафик.

>[!NOTE]
>Если вы хотите разрешить входящий трафик, необходимо выполнить предыдущем примере для добавления ACL, который позволяет весь входящий и исходящий все трафик.

###<a name="step-1-get-the-network-interface-from-which-you-will-remove-the-acl"></a>Шаг 1: Получение сетевого интерфейса, с которого будут удалены ACL
Следующий пример команды можно использовать для получения сетевого интерфейса.

    $nic = get-networkcontrollernetworkinterface -ConnectionUri $uri -ResourceId "MyVM_Ethernet1"

###<a name="step-2-assign-null-to-the-accesscontrollist-property-of-the-ipconfiguration"></a>Шаг 2: Присвоение $NULL к свойству AccessControlList ipConfiguration
Следующий пример команды можно использовать, чтобы присвоить свойство AccessControlList $NULL.

    $nic.properties.ipconfigurations[0].properties.AccessControlList = $null

###<a name="step-3-add-the-network-interface-object-in-network-controller"></a>Шаг 3: Добавление объект сетевого интерфейса в сетевого контроллера
Следующий пример команды можно использовать для добавления в сетевой контроллер объект сетевого интерфейса

    new-networkcontrollernetworkinterface -ConnectionUri $uri -Properties $nic.properties -ResourceId $nic.resourceid

