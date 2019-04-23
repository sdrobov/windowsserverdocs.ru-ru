---
title: Конфигурация физического коммутатора для сетевых Адаптеров со схождением
description: В этом разделе мы предоставляем рекомендациям по настройке вашей физическим коммутаторам.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 6d53c797-fb67-4b9e-9066-1c9a8b76d2aa
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/14/2018
ms.openlocfilehash: e31d7b83fee84d9055d938f77b49389205786244
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59829405"
---
# <a name="physical-switch-configuration-for-converged-nic"></a>Конфигурация физического коммутатора для сетевых Адаптеров со схождением

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе мы предоставляем рекомендациям по настройке вашей физическим коммутаторам. 


Это только команды и методах их использования; необходимо определить порты, к которым подключены сетевые карты, в вашей среде. 

>[!IMPORTANT]
>Убедитесь, что виртуальной локальной сети и политики запрещенным перетаскиванием для приоритета, для которого настроен SMB.

## <a name="arista-switch-dcs-7050s-64-eos-4137m"></a>Коммутатор arista \(контроллеры домена\-7050s\-64, EOS\-4.13.7M\)

1.  EN \(перейти в режим администратора, обычно запросит пароль\)
2.  config \(переходит в режим настройки\)
3.  Показать выполнения \(показывает текущую конфигурацию\)
4.  Узнайте, порты коммутатора, к которым подключены сетевые платы. В этом примере они 14/1,15/1,16/1,17/1.
5.  int eth 14/1,15/1,16/1,17/1 \(войти в режим конфигурации для этих портов\)
6.  режим dcbx ieee
7.  режим приоритет потока управления в
8.  switchport собственного виртуальных ЛС магистрали 225
9.  switchport магистрали допускается виртуальной локальной сети 100-225
10. магистральный режим switchport
11. приоритет потока управления с приоритетом 3, запрещенным перетаскиванием
12. QoS доверять cos
13. Показать выполнения \(убедиться что конфигурация установки правильно на портах\)
14. вести жур \(чтобы сделать параметры сохраняются между перезагрузки коммутатора\)

### <a name="tips"></a>Советы:
1.  Нет command # инвертирует команды
2.  Добавление новой виртуальной локальной сети: int виртуальной локальной сети 100 \(Если сеть хранилища находится в виртуальной локальной сети 100\)
3.  Как проверить существующие виртуальные ЛС: Показать виртуальной локальной сети
4.  Дополнительные сведения о настройке коммутатора Arista поиск в Интернете: Arista EOS вручную
5.  Используйте следующую команду, чтобы проверить параметры PFC: структура счетчики приоритет потока элемента управления.

--- 

## <a name="dell-switch-s4810-ftos-99-00"></a>Коммутатор Dell \(S4810, FTOS 9.9 \(0,0\)\)

    
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
    
--- 

## <a name="cisco-switch-nexus-3132-version-602u61"></a>Коммутатора Cisco \(Nexus 3132, версия 6.0\(2\)U6\(1\)\)

### <a name="global"></a>Глобальная
    
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
    

### <a name="port-specific"></a>Конкретного порта

    
    switchport mode trunk
    switchport trunk native vlan 99
    switchport trunk allowed vlan 99,2000,2050   çuse VLANs that already exists
    spanning-tree port type edge
    flowcontrol receive on (not supported with PFC in Cisco NX-OS)
    flowcontrol send on (not supported with PFC in Cisco NX-OS)
    no shutdown
    priority-flow-control mode on
    
--- 

## <a name="related-topics"></a>См. также

- [Конфигурации сетевых Адаптеров со схождением с одним сетевым адаптером](cnic-single.md)
- [Конфигурация сетевой карты группы сетевых Адаптеров со схождением](cnic-datacenter.md)
- [Устранение неполадок со схождением конфигурации сетевых Адаптеров](cnic-app-troubleshoot.md)

--- 