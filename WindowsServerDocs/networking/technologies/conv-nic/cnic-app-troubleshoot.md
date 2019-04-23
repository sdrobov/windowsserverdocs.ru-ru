---
title: Устранение неполадок со схождением конфигурации сетевых Адаптеров
description: Этот раздел является частью со схождением NIC конфигурации руководство для Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 0bc6746f-2adb-43d8-a503-52f473833164
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 3004ff9d6fe874410c24d174755a6d26f99f8f2a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59876485"
---
# <a name="troubleshooting-converged-nic-configurations"></a>Устранение неполадок со схождением конфигурации сетевых Адаптеров

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Следующий скрипт можно использовать для проверки правильности конфигурации RDMA на узле Hyper-V.

- [Загрузить скрипт теста Rdma.ps1](https://github.com/Microsoft/SDN/blob/master/Diagnostics/Test-Rdma.ps1)

Можно также использовать следующие команды Windows PowerShell для устранения неполадок и проверьте конфигурацию объединенных физических сетевых контроллеров.

## <a name="get-netadapterrdma"></a>Get-NetAdapterRdma

Чтобы проверить конфигурацию сетевого адаптера RDMA, выполните следующую команду Windows PowerShell на сервере Hyper-V.

    
    Get-NetAdapterRdma | fl *
    

Можно использовать следующие ожидается и непредвиденные результаты для выявления и устранения проблем, после выполнения этой команды на узле Hyper-V.

### <a name="get-netadapterrdma-expected-results"></a>Get-NetAdapterRdma ожидалось результатов

Виртуальный сетевой адаптер узла и физический сетевой Адаптер продемонстрировать возможности RDMA на ненулевое значение.

![Windows PowerShell ожидалось результатов](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-01.jpg)

### <a name="get-netadapterrdma-unexpected-results"></a>Get-NetAdapterRdma непредвиденные результаты

Выполните следующие действия, если можно получить неожиданные результаты при выполнении **Get NetAdapterRdma** команды.

1. Убедитесь, что минипорта Mlnx и драйверы шины Mlnx последней. Для Mellanox используйте по крайней мере drop 42. 
2. Проверьте соответствие драйверы минипорта и шины Mlnx по драйвера версии через диспетчер устройств. Драйвер шины можно найти в системные устройства. Имя должно начинаться с Mellanox Connect-X 3 PRO VPI, как показано на следующем снимке экрана из свойств сетевого адаптера.

![Свойства сетевого адаптера](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-02.jpg)

4. Убедитесь, что сети Direct (RDMA) с включенной физический сетевой Адаптер и виртуальную сетевую карту узла.
5. Убедитесь, что виртуальный коммутатор создается прямо физический адаптер, проверив его возможности RDMA.
6. Проверьте журнал системы EventViewer и фильтр по источнику «Hyper-V-VmSwitch».

--- 

## <a name="get-smbclientnetworkinterface"></a>Get-SmbClientNetworkInterface

Как дополнительный шаг, чтобы проверить конфигурацию RDMA выполните следующую команду Windows PowerShell на сервере Hyper-V.


    Get-SmbClientNetworkInterface

### <a name="get-smbclientnetworkinterface-expected-results"></a>Get-SmbClientNetworkInterface ожидалось результатов

Виртуальный сетевой адаптер узла с точки зрения протокола SMB, а также должно быть с поддержкой RDMA.

![Свойства сетевого адаптера](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-03.jpg)


### <a name="get-smbclientnetworkinterface-unexpected-results"></a>Get-SmbClientNetworkInterface непредвиденные результаты

1. Убедитесь, что минипорта Mlnx и драйверы шины Mlnx последней. Для Mellanox используйте по крайней мере drop 42. 
2. Проверьте соответствие драйверы минипорта и шины Mlnx по драйвера версии через диспетчер устройств. Драйвер шины можно найти в системные устройства. Имя должно начинаться с Mellanox Connect-X 3 PRO VPI, как показано на следующем снимке экрана из свойств сетевого адаптера.
3. Убедитесь, что сети Direct (RDMA) с включенной физический сетевой Адаптер и виртуальную сетевую карту узла.
4. Убедитесь, что виртуальный коммутатор Hyper-V создается прямо физический адаптер, проверив его возможности RDMA.
5. Проверьте журналы EventViewer для «SMB-клиент» **служб и приложений | Microsoft | Windows**.

--- 

## <a name="get-netadapterqos"></a>Get-NetAdapterQos

Можно просмотреть качества обслуживания сети адаптера \(QoS\) конфигурации, выполнив следующую команду Windows PowerShell.

    Get-NetAdapterQos

### <a name="get-netadapterqos-expected-results"></a>Get-NetAdapterQos ожидалось результатов

Приоритеты и классы трафика должен отображаться в соответствии с первым шагом настройки, выполненные с помощью этого руководства.

![Качество службы приоритеты и классы](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-04.jpg)

### <a name="get-netadapterqos-unexpected-results"></a>Get-NetAdapterQos непредвиденные результаты

Непредвиденные результаты, выполните следующие действия.

1. Убедитесь, что физический сетевой адаптер поддерживает мост для центра обработки данных \(DCB\) и качество обслуживания
2. Убедитесь, что драйверы сетевого адаптера в актуальном состоянии.

--- 

## <a name="get-smbmultichannelconnection"></a>Get-SmbMultiChannelConnection

Можно использовать следующую команду Windows PowerShell, чтобы убедиться, что IP-адрес удаленного узла RDMA\-поддержкой.

    Get-SmbMultiChannelConnection


### <a name="get-smbmultichannelconnection-expected-results"></a>Get-SmbMultiChannelConnection ожидалось результатов

IP-адрес удаленного узла отображается как RDMA поддержкой.

![IP-адрес удаленного узла с поддержкой RDMA](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-05.jpg)

### <a name="get-smbmultichannelconnection-unexpected-results"></a>Get-SmbMultiChannelConnection непредвиденные результаты

Непредвиденные результаты, выполните следующие действия.

1. Убедитесь, что проверка связи работает в обоих направлениях.
2. Убедитесь, что брандмауэр не блокирует инициации подключения SMB. В частности необходимо включите правило брандмауэра для порта SMB Direct 5445 для iWARP и 445 для ROCE.

--- 

## <a name="get-smbclientnetworkinterface"></a>Get-SmbClientNetworkInterface

Можно использовать следующую команду, чтобы убедиться, что виртуальный сетевой Адаптер вы включили для RDMA, которая считается RDMA\-поддержкой по SMB.

    Get-SmbClientNetworkInterface


### <a name="get-smbclientnetworkinterface-expected-results"></a>Get-SmbClientNetworkInterface ожидалось результатов

Виртуальный сетевой Адаптер, в котором была включена RDMA необходимо рассматривать как с поддержкой RDMA в протоколе SMB.

![SMB сообщает, что сетевые адаптеры с поддержкой RDMA](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-06.jpg)

### <a name="get-smbclientnetworkinterface-unexpected-results"></a>Get-SmbClientNetworkInterface непредвиденные результаты

Непредвиденные результаты, выполните следующие действия.

1. Убедитесь, что проверка связи работает в обоих направлениях.
2. Убедитесь, что брандмауэр не блокирует инициации подключения SMB.

--- 

## <a name="vstat-mellanox-specific"></a>vstat \(конкретных Mellanox\)

Если вы используете сетевые адаптеры Mellanox, можно использовать **vstat** команду, чтобы проверить RDMA over Converged Ethernet \(RoCE\) версии на узлах Hyper-V.

### <a name="vstat-expected-results"></a>Ожидается vstat результатов

Версия RoCE на обоих узлах должны совпадать. Это хороший способ проверить, имеет последнюю версию встроенного по на обоих узлах.

![Примеры результат проверки версии RoCE](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-07.jpg)

### <a name="vstat-unexpected-results"></a>vstat непредвиденные результаты

Непредвиденные результаты, выполните следующие действия.

1. Задайте правильную версию RoCE, с помощью набора MlnxDriverCoreSetting
2. Установите последние версии встроенного по с веб-сайта Mellanox.

--- 

## <a name="perfmon-counters"></a>Счетчики системного монитора

Вы можете просмотреть счетчики в системном мониторе, чтобы проверить его действия RDMA конфигурации.

![Примеры результат монитора производительности](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-08.jpg)

--- 

## <a name="related-topics"></a>См. также

- [Конфигурации сетевых Адаптеров со схождением с одним сетевым адаптером](cnic-single.md)
- [Конфигурация сетевой карты группы сетевых Адаптеров со схождением](cnic-datacenter.md)
- [Конфигурация физического коммутатора для сетевых Адаптеров со схождением](cnic-app-switch-config.md)

---
