---
title: Устранение неполадок схождение выполнено конфигурации сетевого Адаптера
description: Этот раздел является частью схождение выполнено NIC конфигурации руководство для Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 0bc6746f-2adb-43d8-a503-52f473833164
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 373ecd9b9fff62aaabd8caa176ff091ec98ad81c
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="troubleshooting-converged-nic-configurations"></a>Устранение неполадок схождение выполнено конфигурации сетевого Адаптера

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Следующий сценарий можно использовать для проверки правильности конфигурации RDMA на узле Hyper-V.

- [Загрузите .ps1 Test-Rdma сценария](https://github.com/Microsoft/SDN/blob/master/Diagnostics/Test-Rdma.ps1)

Можно также использовать следующие команды Windows PowerShell для устранения неполадок и проверьте конфигурацию на схождением сетевых адаптерах.

## <a name="get-netadapterrdma"></a>Get-NetAdapterRdma

Чтобы проверить конфигурацию сетевого адаптера RDMA, воспользуйтесь следующей командой Windows PowerShell на сервере Hyper-V.

    
    Get-NetAdapterRdma | fl *
    

Чтобы определить и устранить проблемы, после выполнения этой команды на узле Hyper-V можно использовать следующие ожидается и неожиданные результаты.

### <a name="get-netadapterrdma-expected-results"></a>Get-NetAdapterRdma ожидаемых результатов

Сетевой адаптер узла и физический сетевой Адаптер Показать возможности RDMA отличное от нуля.

![Результаты ожидается в Windows PowerShell](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-01.jpg)

### <a name="get-netadapterrdma-unexpected-results"></a>Get-NetAdapterRdma неожиданные результаты

Выполните следующие действия, если получать неожиданные результаты при запуске **Get-NetAdapterRdma** команды.

1. Убедитесь, что драйвер мини-порта Mlnx и драйверы шины Mlnx последней. Для Mellanox использовать по крайней мере удалите 42. 
2. Убедитесь, что драйверы мини-порта и шины Mlnx соответствуют путем проверки версии драйвер через диспетчер устройств. Драйвер шины можно найти в системные устройства. Имя должно начинаться с Mellanox Connect-X 3 PRO VPI, как показано на следующем снимке экрана из свойств сетевого адаптера.

![Свойств сетевого адаптера](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-02.jpg)

4. Убедитесь, что сеть Direct (RDMA) включено на физический сетевой Адаптер и сетевой адаптер узла.
5. Убедитесь, что виртуальный коммутатор создается прямо физический адаптер, проверив его возможности RDMA.
6. Проверьте журнал системных трассировка и фильтрации по источнику «Hyper-V-VmSwitch».

## <a name="get-smbclientnetworkinterface"></a>Получить SmbClientNetworkInterface

Как дополнительный шаг, чтобы проверить конфигурацию RDMA воспользуйтесь следующей командой Windows PowerShell на сервере Hyper-V.


    Get SmbClientNetworkInterface

### <a name="get-smbclientnetworkinterface-expected-results"></a>Получить результаты SmbClientNetworkInterface ожидаемого

С точки зрения SMB также поддерживают RDMA должно быть сетевой адаптер узла.

![Свойств сетевого адаптера](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-03.jpg)


### <a name="get-smbclientnetworkinterface-unexpected-results"></a>Получить SmbClientNetworkInterface неожиданные результаты

1. Убедитесь, что драйвер мини-порта Mlnx и драйверы шины Mlnx последней. Для Mellanox использовать по крайней мере удалите 42. 
2. Убедитесь, что драйверы мини-порта и шины Mlnx соответствуют путем проверки версии драйвер через диспетчер устройств. Драйвер шины можно найти в системные устройства. Имя должно начинаться с Mellanox Connect-X 3 PRO VPI, как показано на следующем снимке экрана из свойств сетевого адаптера.
3. Убедитесь, что сеть Direct (RDMA) включено на физический сетевой Адаптер и сетевой адаптер узла.
4. Убедитесь, что виртуальный коммутатор Hyper-V создается прямо физический адаптер, проверив его возможности RDMA.
5. Проверьте журналы Трассировка «Клиента SMB» **служб и приложений | Майкрософт | Windows**.

## <a name="get-netadapterqos"></a>Get-NetAdapterQos

Сетевой адаптер качество \(QoS\) конфигурации службы можно просмотреть, выполнив следующую команду Windows PowerShell.

    Get-NetAdapterQos

### <a name="get-netadapterqos-expected-results"></a>Get-NetAdapterQos ожидаемых результатов

Приоритеты и классы трафика должны отображаться в соответствии с первый шаг настройки, выполненные с помощью этого руководства.

![Качество классов и службы приоритетов](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-04.jpg)

### <a name="get-netadapterqos-unexpected-results"></a>Get-NetAdapterQos неожиданные результаты

В случае непредвиденных результатов выполните следующие действия.

1. Убедитесь, что физический сетевой адаптер поддерживает \(DCB\) мост для центра обработки данных и качество обслуживания
2. Убедитесь, что драйверы сетевого адаптера в актуальном состоянии.


## <a name="get-smbmultichannelconnection"></a>Get-SmbMultiChannelConnection

Можно использовать следующую команду Windows PowerShell для проверки поддержкой RDMA\ удаленный узел IP-адрес.

    Get-SmbMultiChannelConnection


### <a name="get-smbmultichannelconnection-expected-results"></a>Get-SmbMultiChannelConnection ожидаемых результатов

Удаленный узел IP-адрес отображается как RDMA поддержкой.

![RDMA поддержкой удаленному узлу IP-адрес](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-05.jpg)

### <a name="get-smbmultichannelconnection-unexpected-results"></a>Get-SmbMultiChannelConnection неожиданные результаты

В случае непредвиденных результатов выполните следующие действия.

1. Убедитесь, что ping работает обоими способами.
2. Убедитесь, что брандмауэр не блокирует инициации подключения SMB. В частности необходимо включите правило брандмауэра для порта SMB Direct 5445 для iWARP и 445 для ROCE.

## <a name="get-smbclientnetworkinterface"></a>Get-SmbClientNetworkInterface

Можно использовать следующую команду, чтобы убедиться, что виртуальный сетевой Адаптер, включен для RDMA считается поддержкой RDMA\ по SMB.

    Get-SmbClientNetworkInterface


### <a name="get-smbclientnetworkinterface-expected-results"></a>Get-SmbClientNetworkInterface ожидаемых результатов

Виртуальный сетевой Адаптер, который был включен для RDMA, должны быть видны как поддерживают RDMA SMB.

![SMB сообщает, что сетевые адаптеры поддерживают RDMA](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-06.jpg)

### <a name="get-smbclientnetworkinterface-unexpected-results"></a>Get-SmbClientNetworkInterface неожиданные результаты

В случае непредвиденных результатов выполните следующие действия.

1. Убедитесь, что ping работает обоими способами.
2. Убедитесь, что брандмауэр не блокирует инициации подключения SMB.

## <a name="vstat-mellanox-specific"></a>vstat \(Mellanox specific\)

Если вы используете сетевые адаптеры Mellanox, можно использовать **vstat** команду, чтобы проверить RDMA по Конвергентной сети Ethernet \(RoCE\) версии на узлах Hyper-V.

### <a name="vstat-expected-results"></a>Ожидается vstat результатов

Версия RoCE на обоих узлах должны быть одинаковыми. Это хороший способ проверки правильности последние версии встроенного по на обоих узлах.

![Примеры результатов проверки версии RoCE](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-07.jpg)

### <a name="vstat-unexpected-results"></a>vstat неожиданные результаты

В случае непредвиденных результатов выполните следующие действия.

1. Установить правильную версию RoCE, с помощью Set-MlnxDriverCoreSetting
2. Установите последние версии встроенного по с Mellanox веб-сайта.


## <a name="perfmon-counters"></a>Счетчики системного монитора

Вы можете просмотреть счетчики системного монитора, чтобы проверить активность RDMA конфигурации.

![Примеры результат монитора производительности](../../media/Converged-NIC/CNIC-Troubleshooting/cnic-tshoot-08.jpg)

## <a name="all-topics-in-this-guide"></a>Все разделы в этом руководстве

Это руководство содержит следующие разделы.

- [Настройка объединенных сетевых Адаптеров с одним сетевым адаптером](cnic-single.md)
- [Настройка сетевой КАРТЫ группы схождением сетевых Адаптеров](cnic-datacenter.md)
- [Физический переключатель конфигурации для сетевого Адаптера схождением](cnic-app-switch-config.md)
- [Устранение неполадок схождение выполнено конфигурации сетевого Адаптера](cnic-app-troubleshoot.md)
