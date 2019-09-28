---
title: Конфигурация физического коммутатора для Объединенных сетевых адаптеров
description: В этом разделе приведены рекомендации по настройке физических коммутаторов.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 6d53c797-fb67-4b9e-9066-1c9a8b76d2aa
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/14/2018
ms.openlocfilehash: d10e8ca6e4689b89a8b9532f77613f17280282b1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71355483"
---
# <a name="physical-switch-configuration-for-converged-nic"></a>Конфигурация физического коммутатора для Объединенных сетевых адаптеров

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе приведены рекомендации по настройке физических коммутаторов. 


Это только команды и их использование; необходимо определить порты, к которым подключены сетевые карты в вашей среде. 

>[!IMPORTANT]
>Убедитесь, что для виртуальной ЛС и политики без удаления задан приоритет, по которому настроен протокол SMB.

## <a name="arista-switch-dcs-7050s-64-eos-4137m"></a>Ариста Switch \(dcs @ no__t-17050s @ no__t-264, EOS @ no__t-34.13.7 M @ no__t-4

1.  EN \(go в режим администратора, обычно запрашивает пароль @ no__t-1
2.  config @no__t 0to вход в режим конфигурации @ no__t-1
3.  показывать выполнение @no__t — 0shows Текущая выполняемая конфигурация @ no__t-1
4.  Найдите порты коммутатора, к которым подключены сетевые карты. В этом примере это 14/1, 15/1, 16/1, 17/1.
5.  int ETH 14/1, 15/1, 16/1, 17/1 \(enter в режим конфигурации для этих портов @ no__t-1
6.  режим дкбкс IEEE
7.  приоритет — режим управления потоком в
8.  встроенная виртуальная ЛС свитчпорт для магистрали машинного кода 225
9.  свитчпортная магистральная виртуальная ЛС 100-225
10. Магистральный режим свитчпорт
11. Priority — Приоритет управления потоком 3 без удаления
12. отношение доверия с QoS COS
13. показывать Run @no__t — 0verify, что конфигурация правильно настроена на портах @ no__t-1
14. WR @no__t — 0to, чтобы параметры сохранялись при перезагрузке коммутатора @ no__t-1

### <a name="tips"></a>Предпринять
1.  No #command # инвертирует команду
2.  Как добавить новую виртуальную ЛС: int VLAN 100 \(If сеть хранения данных находится в виртуальной ЛС 100 @ no__t-1
3.  Проверка существующих виртуальных ЛС: Отображение виртуальной ЛС
4.  Дополнительные сведения о настройке коммутатора Ариста см. в Интернете: Руководство по Ариста EOS
5.  Используйте эту команду, чтобы проверить параметры КОМПЕНСАЦИй: отображение счетчиков "приоритет — управление потоком"

--- 

## <a name="dell-switch-s4810-ftos-99-00"></a>Коммутатор Dell Switch \(S4810, ФТОС 9,9 \(0.0 @ no__t-2 @ no__t-3

    
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

## <a name="cisco-switch-nexus-3132-version-602u61"></a>Коммутатор Cisco \(Nexus 3132, версия 6.0 @ no__t-12 @ no__t-2U6 @ no__t-31 @ no__t-4 @ no__t-5

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
    

### <a name="port-specific"></a>Для конкретного порта

    
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

- [Конфигурация с согласованным СЕТЕВЫМ адаптером с одним сетевым адаптером](cnic-single.md)
- [Конфигурация сетевого адаптера Объединенных сетевых адаптеров](cnic-datacenter.md)
- [Устранение неполадок конфигураций Объединенных сетевых адаптеров](cnic-app-troubleshoot.md)

--- 