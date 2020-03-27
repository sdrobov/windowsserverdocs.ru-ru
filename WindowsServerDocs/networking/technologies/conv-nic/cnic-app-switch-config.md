---
title: Конфигурация физического коммутатора для Объединенных сетевых адаптеров
description: В этом разделе приведены рекомендации по настройке физических коммутаторов.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 6d53c797-fb67-4b9e-9066-1c9a8b76d2aa
manager: dougkim
ms.author: lizross
author: eross-msft
ms.date: 09/14/2018
ms.openlocfilehash: 57fc944461254e78635913ac298bacc26a0789f2
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80309617"
---
# <a name="physical-switch-configuration-for-converged-nic"></a>Конфигурация физического коммутатора для Объединенных сетевых адаптеров

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе приведены рекомендации по настройке физических коммутаторов. 


Это только команды и их использование; необходимо определить порты, к которым подключены сетевые карты в вашей среде. 

>[!IMPORTANT]
>Убедитесь, что для виртуальной ЛС и политики без удаления задан приоритет, по которому настроен протокол SMB.

## <a name="arista-switch-dcs-7050s-64-eos-4137m"></a>Ариста Switch \(DCS\-7050s\-64, EOS\-4.13.7 M\)

1.  \(EN переходит в режим администратора, обычно запрашивает пароль\)
2.  \(конфигурации для входа в режим конфигурации\)
3.  Показать запуск \(отображает текущую выполняющуюся конфигурацию\)
4.  Найдите порты коммутатора, к которым подключены сетевые карты. В этом примере это 14/1, 15/1, 16/1, 17/1.
5.  int ETH 14/1, 15/1, 16/1, 17/1 \(войти в режим конфигурации для этих портов\)
6.  режим дкбкс IEEE
7.  приоритет — режим управления потоком в
8.  встроенная виртуальная ЛС свитчпорт для магистрали машинного кода 225
9.  свитчпортная магистральная виртуальная ЛС 100-225
10. Магистральный режим свитчпорт
11. Priority — Приоритет управления потоком 3 без удаления
12. отношение доверия с QoS COS
13. показывать запуск \(убедитесь, что конфигурация правильно настроена для портов\)
14. WR \(, чтобы сохранить параметры между перезагрузками коммутатора\)

### <a name="tips"></a>Советы.
1.  No #command # инвертирует команду
2.  Как добавить новую виртуальную ЛС: int VLAN 100 \(, если сеть хранения находится в 100 на виртуальной ЛС\)
3.  Проверка существующих виртуальных ЛС: Отображение виртуальной ЛС
4.  Для получения дополнительных сведений о настройке коммутатора Ариста выполните поиск в Интернете: Ариста EOS вручную.
5.  Используйте эту команду, чтобы проверить параметры КОМПЕНСАЦИй: отображение счетчиков "приоритет — управление потоком"

--- 

## <a name="dell-switch-s4810-ftos-99-00"></a>Dell Switch \(S4810, ФТОС 9,9 \(0,0\)\)

    
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

## <a name="cisco-switch-nexus-3132-version-602u61"></a>Коммутатор Cisco \(хранилища 3132, версия 6,0\(2\)U6\(1\)\)

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

## <a name="related-topics"></a>Связанные разделы

- [Конфигурация с согласованным СЕТЕВЫМ адаптером с одним сетевым адаптером](cnic-single.md)
- [Конфигурация сетевого адаптера Объединенных сетевых адаптеров](cnic-datacenter.md)
- [Устранение неполадок конфигураций Объединенных сетевых адаптеров](cnic-app-troubleshoot.md)

--- 