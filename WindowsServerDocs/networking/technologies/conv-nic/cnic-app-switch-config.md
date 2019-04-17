---
title: Физический переключатель конфигурации для сетевого Адаптера схождением
description: Этот раздел является частью схождение выполнено NIC конфигурации руководство для Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 6d53c797-fb67-4b9e-9066-1c9a8b76d2aa
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 98a2e249aea38bd4d07dc1bcbc9b1ca98b98b6d6
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="physical-switch-configuration-for-converged-nic"></a>Физический переключатель конфигурации для сетевого Адаптера схождением

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Можно использовать приведенные ниже рекомендации по настройке вашей физические коммутаторы.

Это только команды и их использования; порты, к которым подключены сетевые адаптеры, необходимо определить в вашей среде. 

>[!IMPORTANT]
>Убедитесь, что виртуальной локальной сети и политики запрета перетаскивания для приоритет над тем, какие настройки SMB.

## <a name="arista-switch-dcs-7050s-64-eos-4137m"></a>Коммутатор arista \ (dcs\-7050s\-64, EOS\-4.13.7M\)

1.  en \ (перехода в режим администратора, обычно запрашивает password\)
2.  конфигурации \ (для заключения mode\ конфигурации)
3.  Показать выполнения \ (показана текущей работающей конфигурации)
4.  Узнайте, порты коммутатора, к которым подключены на сетевых адаптерах, чтобы. В этом примере это 14 и 1,15 или 1,16 или 1,17 и 1.
5.  Подразделение int 14 и 1,15/1,16/1,17/1 \ (перейдет в режим конфигурации для этих ports\)
6.  режим dcbx ieee
7.  элемент управления приоритетом потока режима на
8.  switchport магистрали встроенную виртуальную ЛС 225
9.  допустимое switchport магистрали виртуальной ЛС 100-225
10. магистральный режим switchport
11. Нет раскрывающийся элемент управления приоритетом потока приоритет 3
12. QoS доверия cos
13. Показать выполнения \ (убедиться, что конфигурация настроена правильно на ports\)
14. wr \ (чтобы параметры сохраняется для разных reboot\ коммутатора)

### <a name="tips"></a>Советы по.
1.  Не command # инвертирует команду
2.  Добавление новых виртуальных локальных СЕТЕЙ: int vlan 100 \ (если сети хранения данных является 100\ виртуальной локальной сети)
3.  Проверка существующих виртуальных локальных сетей: Показать виртуальной ЛС
4.  Дополнительные сведения о настройке коммутатора Arista поиск в Интернете: Arista электрической ПЕРЕГРУЗКИ вручную
5.  Эта команда используется для проверки параметров PFC: отображать сведения счетчики элемент управления приоритетом потока

## <a name="dell-switch-s4810-ftos-99-00"></a>Коммутатор Dell \ (S4810, \(0.0\)\) FTOS 9,9

    
    !
    dcb enable
    ! put pfc control on qos class 3
    configure
    dcb-map dcb-smb
    priority group 0 bandwidth 90 pfc on
    priority group 1 bandwidth 10 pfc off
    priority-pgid 1 1 1 0 1 1 1 1
    exit
    ! apply map to ports 0-31
    configure
    interface range ten 0/0-31
    dcb-map dcb-smb
    exit
    

## <a name="cisco-switch-nexus-3132-version-602u61"></a>Коммутатор Cisco \ (Nexus 3132, версия 6.0\(2\)U6\(1\)\)

### <a name="global"></a>Глобальные
    
    class-map type qos match-all RDMA
    match cos 3
    class-map type queuing RDMA
    match qos-group 3
    policy-map type qos QOS_MARKING
    class RDMA
    set qos-group 3
    class class-default
    policy-map type queuing QOS_QUEUEING
    class type queuing RDMA
    bandwidth percent 50
    class type queuing class-default
    bandwidth percent 50
    class-map type network-qos RDMA
    match qos-group 3
    policy-map type network-qos QOS_NETWORK
    class type network-qos RDMA
    mtu 2240
    pause no-drop
    class type network-qos class-default
    mtu 9216
    system qos
    service-policy type qos input QOS_MARKING
    service-policy type queuing output QOS_QUEUEING
    service-policy type network-qos QOS_NETWORK
    

### <a name="port-specific"></a>Определенного порта

    
    switchport mode trunk
    switchport trunk native vlan 99
    switchport trunk allowed vlan 99,2000,2050   çuse VLANs that already exists
    spanning-tree port type edge
    flowcontrol receive on (not supported with PFC in Cisco NX-OS)
    flowcontrol send on (not supported with PFC in Cisco NX-OS)
    no shutdown
    priority-flow-control mode on
    

## <a name="all-topics-in-this-guide"></a>Все разделы в этом руководстве

Это руководство содержит следующие разделы.

- [Настройка объединенных сетевых Адаптеров с одним сетевым адаптером](cnic-single.md)
- [Настройка сетевой КАРТЫ группы схождением сетевых Адаптеров](cnic-datacenter.md)
- [Физический переключатель конфигурации для сетевого Адаптера схождением](cnic-app-switch-config.md)
- [Устранение неполадок схождение выполнено конфигурации сетевого Адаптера](cnic-app-troubleshoot.md)
