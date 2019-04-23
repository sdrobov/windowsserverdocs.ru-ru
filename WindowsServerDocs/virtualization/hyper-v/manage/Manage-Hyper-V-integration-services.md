---
title: Управление службами интеграции Hyper-V
description: Описывает способ включения служб integration services и отключения и установить их при необходимости
ms.technology: compute-hyper-v
author: KBDAzure
ms.author: kathydav
manager: dongill
ms.date: 12/20/2016
ms.topic: article
ms.prod: windows-server-threshold
ms.service: na
ms.assetid: 9cafd6cb-dbbe-4b91-b26c-dee1c18fd8c2
ms.openlocfilehash: b049efc61d5060791574f20fcdd8b369a26f0507
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59890255"
---
>Область применения. Windows 10, Windows Server 2016, Windows Server 2019 г.

# <a name="manage-hyper-v-integration-services"></a>Управление службами интеграции Hyper-V

Службы интеграции Hyper-V повышения производительности виртуальной машины и предоставляет удобные возможности за счет использования двусторонний обмен данными с узлом Hyper-V. Многие из этих служб используются для удобства, например копирования файлов гостевой ОС, а другие — важны для функциональных возможностей виртуальной машины, например драйверы синтетических устройств. Это набор служб и драйверов, иногда называются «компоненты интеграции». Вы можете управлять ли службы отдельных удобства работы для любой заданной виртуальной машины. Компоненты драйвера не предназначены для обслуживания вручную.

Дополнительные сведения о каждой службе интеграции см. в разделе [служб интеграции Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/reference/integration-services).

>[!IMPORTANT]
>Для работы на узле и гостевой необходимо включить каждой службы, которую вы хотите использовать. Все службы интеграции, за исключением «Интерфейс гостевой службы Hyper-V» включены по умолчанию в Windows гостевых операционных системах. Службы можно включать и выключать по отдельности. В следующих разделах показано, каким образом.

## <a name="turn-an-integration-service-on-or-off-using-hyper-v-manager"></a>Включить службу интеграции, или отключить с помощью диспетчера Hyper-V

1. В центральной области щелкните правой кнопкой мыши виртуальную машину и нажмите кнопку **параметры**.
  
2. В области слева от **параметры** окна в разделе **управления**, нажмите кнопку **служб Integration Services**.
  
В области служб Integration Services перечислены все службы интеграции, доступные на узле Hyper-V, и включил ли узел виртуальной машины, их использование.

### <a name="turn-an-integration-service-on-or-off-using-powershell"></a>Включить службу интеграции, или отключить с помощью PowerShell

Для этого в PowerShell, используйте [Enable-VMIntegrationService](https://technet.microsoft.com/library/hh848500.aspx) и [Disable-VMIntegrationService](https://technet.microsoft.com/library/hh848488.aspx).

В следующих примерах демонстрируется включение гостевой службу копирования файлов и отключать для виртуальной машины с именем «demovm».

1. Получение списка запущенных служб integration services:
  
    ``` PowerShell
    Get-VMIntegrationService -VMName "DemoVM"
    ```
1. Результат должен выглядеть так:

    ``` PowerShell
   VMName      Name                    Enabled PrimaryStatusDescription SecondaryStatusDescription
   ------      ----                    ------- ------------------------ --------------------------
   DemoVM      Guest Service Interface False   OK
   DemoVM      Heartbeat               True    OK                       OK
   DemoVM      Key-Value Pair Exchange True    OK
   DemoVM      Shutdown                True    OK
   DemoVM      Time Synchronization    True    OK
   DemoVM      VSS                     True    OK
   ```

1. Включите интерфейс гостевой службы:

   ``` PowerShell
   Enable-VMIntegrationService -VMName "DemoVM" -Name "Guest Service Interface"
   ```

1. Убедитесь, что интерфейс гостевой службы включено:

   ```
   Get-VMIntegrationService -VMName "DemoVM" 
   ``` 

1. Отключите интерфейс гостевой службы:

    ```
    Disable-VMIntegrationService -VMName "DemoVM" -Name "Guest Service Interface"
    ```
   
## <a name="checking-the-guests-integration-services-version"></a>Проверка версии служб интеграции на виртуальной машине работает
Некоторые функции могут работать неправильно или вообще, если гостевые службы интеграции не является текущей. Чтобы получить сведения о версии для Windows, войдите в систему гостевой операционной системы, откройте командную строку и выполните следующую команду:

```
REG QUERY "HKLM\Software\Microsoft\Virtual Machine\Auto" /v IntegrationServicesVersion
```
Более ранние гостевые операционные системы не будет иметь все доступные службы. Например гостевые системы Windows Server 2008 R2 не может быть «Hyper-V интерфейс гостевой службы».

## <a name="start-and-stop-an-integration-service-from-a-windows-guest"></a>Запускать и останавливать службу интеграции из гостевой Windows
Для полной функциональности службы интеграции, его соответствующей службы должен выполняться в гостевой помимо включается на узле. Каждой службе интеграции в гостевых систем Windows, отображается как стандартную службу Windows. Приложение "службы" в панели управления или PowerShell можно использовать для остановки и запуска этих служб.

>[!IMPORTANT]
> Остановить службу интеграции может серьезно повлиять на возможность узлов управлять вашей виртуальной машиной. Работал правильно, необходимо включить на узле и гостевой каждой службы интеграции, которую вы хотите использовать.
> Рекомендуется только вы сами должны управлять служб интеграции Hyper-V, следуя инструкциям выше. Соответствующие службы в гостевой операционной системы будет остановить или запустить автоматически, при изменении его состояния в Hyper-V.
> Если запустить службу в гостевой операционной системы, но оно отключено на Hyper-V, служба будет остановлена. При остановке службы в гостевой операционной системе, которая включается в Hyper-V, Hyper-V будет со временем запустите его снова. Если отключить службу в гостевой ОС, Hyper-V будет не удается запустить его.

### <a name="use-windows-services-to-start-or-stop-an-integration-service-within-a-windows-guest"></a>Использование служб Windows, чтобы запустить или остановить службу интеграции в гостевой Windows

1. Откройте диспетчер служб, выполнив ```services.msc``` с правами администратора или дважды щелкнув значок "службы" на панели управления.

    ![Снимок экрана, показывающий области служб Windows](media/HVServices.png) 

1. Найти службы, которые начинаются с «Hyper-V». 

1. Щелкните правой кнопкой мыши службу, необходимо запустить или остановить. Щелкните нужное действие.


### <a name="use-windows-powershell-to-start-or-stop-an-integration-service-within-a-windows-guest"></a>Чтобы запустить или остановить службу интеграции в гостевой Windows с помощью Windows PowerShell

1. Чтобы получить список служб integration services, выполните следующую команду:

    ```
    Get-Service -Name vm*
    ```
1.  Выходные данные должны выглядеть примерно следующим образом:

    ```PowerShell
    Status   Name               DisplayName
    ------   ----               -----------
    Running  vmicguestinterface Hyper-V Guest Service Interface
    Running  vmicheartbeat      Hyper-V Heartbeat Service
    Running  vmickvpexchange    Hyper-V Data Exchange Service
    Running  vmicrdv            Hyper-V Remote Desktop Virtualizati...
    Running  vmicshutdown       Hyper-V Guest Shutdown Service
    Running  vmictimesync       Hyper-V Time Synchronization Service
    Stopped  vmicvmsession      Hyper-V VM Session Service
    Running  vmicvss            Hyper-V Volume Shadow Copy Requestor
    ```

1. Выполните одну [Start-Service](https://technet.microsoft.com/library/hh849825.aspx) или [Stop-Service](https://technet.microsoft.com/library/hh849790.aspx). Например чтобы отключить Windows PowerShell Direct, выполните следующую команду:

    ```
    Stop-Service -Name vmicvmsession
    ```

## <a name="start-and-stop-an-integration-service-from-a-linux-guest"></a>Запускать и останавливать службу интеграции из гостевой ОС Linux 

Службы интеграции Linux обычно предоставляются через ядро Linux. Драйвер служб интеграции Linux называется **hv_utils**.

1.  Чтобы определить **hv_utils** загружается, используйте следующую команду:

    ``` BASH
    lsmod | grep hv_utils
    ``` 
  
1. Выходные данные должны выглядеть примерно следующим образом:  
  
    ``` BASH
    Module                  Size   Used by
    hv_utils               20480   0
    hv_vmbus               61440   8 hv_balloon,hyperv_keyboard,hv_netvsc,hid_hyperv,hv_utils,hyperv_fb,hv_storvsc
    ```

1. Чтобы узнать, запускаются ли необходимые управляющие программы, используйте следующую команду.
  
    ``` BASH
    ps -ef | grep hv
    ```
  
1. Выходные данные должны выглядеть примерно следующим образом: 
  
    ```BASH
    root       236     2  0 Jul11 ?        00:00:00 [hv_vmbus_con]
    root       237     2  0 Jul11 ?        00:00:00 [hv_vmbus_ctl]
    ...
    root       252     2  0 Jul11 ?        00:00:00 [hv_vmbus_ctl]
    root      1286     1  0 Jul11 ?        00:01:11 /usr/lib/linux-tools/3.13.0-32-generic/hv_kvp_daemon
    root      9333     1  0 Oct12 ?        00:00:00 /usr/lib/linux-tools/3.13.0-32-generic/hv_kvp_daemon
    root      9365     1  0 Oct12 ?        00:00:00 /usr/lib/linux-tools/3.13.0-32-generic/hv_vss_daemon
    scooley  43774 43755  0 21:20 pts/0    00:00:00 grep --color=auto hv          
    ```

1. Чтобы отобразить все доступные управляющие программы, выполните следующую команду:

    ``` BASH
    compgen -c hv_
    ```
  
1. Выходные данные должны выглядеть примерно следующим образом:
  
    ``` BASH
    hv_vss_daemon
    hv_get_dhcp_info
    hv_get_dns_info
    hv_set_ifconfig
    hv_kvp_daemon
    hv_fcopy_daemon     
    ```
  
 Управляющие программы служб интеграции, могут быть указаны включают следующее. Если какие-либо отсутствуют, они могут не поддерживаться в вашей системе, или они не могут быть установлены. Найти сведения, см. в разделе [виртуальных машин поддерживается Linux и FreeBSD для Hyper-V в Windows](https://technet.microsoft.com/library/dn531030.aspx).  
  - **hv_vss_daemon**: Эта управляющая программа необходима для создания динамической резервных копий виртуальных машин Linux.
  - **hv_kvp_daemon**: Эта управляющая программа позволяет задавать и запрашивать пары внутренние и внешние значения ключа.
  - **hv_fcopy_daemon**: Эта управляющая программа внедряет службу копирования файлов между узлом и гостевой.  

### <a name="examples"></a>Примеры

Эти примеры показывают, остановка и запуск управляющей программы KVP, с именем `hv_kvp_daemon`.

1. Используйте идентификатор процесса \(PID\) остановить процесс управляющей программы. Чтобы найти PID, просмотрите второй столбец выходных данных, или использовать `pidof`. Управляющие программы Hyper-V запускаются как корень, поэтому необходимы разрешения корневой.

    ``` BASH
    sudo kill -15 `pidof hv_kvp_daemon`
    ```

1. Чтобы убедиться, что все `hv_kvp_daemon` процесс исчезли, выполните:

    ```
    ps -ef | hv
    ```

1. Чтобы запустить управляющую программу снова, запустите ее в качестве привилегированного пользователя:

    ``` BASH
    sudo hv_kvp_daemon
    ``` 

1. Чтобы убедиться, что `hv_kvp_daemon` процесса отображается с новым Идентификатором процесса, выполните:

    ```
    ps -ef | hv
    ```

## <a name="keep-integration-services-up-to-date"></a>Службы integration services для обновления

Мы рекомендуем поддерживать актуальность для получения максимальной производительности и новейшие возможности для виртуальных машин, службы integration services. Если они настроены на получение важных обновлений из центра обновления Windows, то это значение происходит для большинства гостевых систем Windows по умолчанию. Гостевых ОС Linux, с помощью текущего ядра будут получать последние компоненты интеграции, при обновлении ядра.

**Для виртуальных машин, работающих на узлах под управлением Windows 10:**

> [!NOTE]
> Файл образа vmguest.iso не входят в состав Hyper-V в Windows 10, так как он больше не требуется.

| Гость  | Механизм обновления | Примечания |
|:---------|:---------|:---------|
| Windows 10 | Центр обновления Windows | |
| Windows 8.1 | Центр обновления Windows | |
| Windows 8 | Центр обновления Windows | Требуется служба интеграции для обмена данными.* |
| Windows 7 | Центр обновления Windows | Требуется служба интеграции для обмена данными.* |
| Windows Vista с пакетом обновления 2 (SP2) | Центр обновления Windows | Требуется служба интеграции для обмена данными.* |
| - | | |
| Windows Server 2016 | Центр обновления Windows | |
| Windows Server Semi-Annual Channel | Центр обновления Windows | |
| Windows Server 2012 R2 | Центр обновления Windows | |
| Windows Server 2012 | Центр обновления Windows | Требуется служба интеграции для обмена данными.* |
| Windows Server 2008 R2 с пакетом обновления 1 (SP1) | Центр обновления Windows | Требуется служба интеграции для обмена данными.* |
| Windows Server 2008 с пакетом обновления 2 (SP 2) | Центр обновления Windows | Расширенная поддержка только в Windows Server 2016 ([Подробнее](https://support.microsoft.com/lifecycle?p1=12925)). |
| Windows Home Server 2011 | Центр обновления Windows | Не будет поддерживаться в Windows Server 2016 ([Подробнее](https://support.microsoft.com/lifecycle?p1=15820)). |
| Windows Small Business Server 2011 | Центр обновления Windows | Не в основной фазе поддержки ([подробности](https://support.microsoft.com/lifecycle?p1=15817)). |
| - | | |
| Гостевые ОС Linux | диспетчер пакетов | Службы интеграции Linux встроены в дистрибутив, но может существовать необязательные обновления. ******** |

\* Если служба интеграции обмена данными невозможно включить, службы интеграции для этих гостей доступны из [центра загрузки](https://support.microsoft.com/kb/3071740) как в формате CAB-файл. Инструкции по применению CAB-файлов см. в этом [блога](https://blogs.technet.com/b/virtualization/archive/2015/07/24/integration-components-available-for-virtual-machines-not-connected-to-windows-update.aspx).

**Для виртуальных машин, работающих на узлах под управлением Windows 8.1:**

| Гость  | Механизм обновления | Примечания |
|:---------|:---------|:---------|
| Windows 10 | Центр обновления Windows | |
| Windows 8.1 | Центр обновления Windows | |
| Windows 8 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows 7 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Vista с пакетом обновления 2 (SP2) | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows XP с пакетами обновления 2 и 3 (SP2, SP3) | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| - | | |
| Windows Server 2016 | Центр обновления Windows | |
| Windows Server Semi-Annual Channel | Центр обновления Windows | |
| Windows Server 2012 R2 | Центр обновления Windows | |
| Windows Server 2012 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Server 2008 R2 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Server 2008 с пакетом обновления 2 (SP 2) | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Home Server 2011 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Small Business Server 2011 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Server 2003 R2 с пакетом обновления 2 (SP2) | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Server 2003 с пакетом обновления 2 (SP2) | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| - | | |
| Гостевые ОС Linux | диспетчер пакетов | Службы интеграции Linux встроены в дистрибутив, но может существовать необязательные обновления. ** |


**Для виртуальных машин, работающих на узлах под управлением Windows 8:**

| Гость  | Механизм обновления | Примечания |
|:---------|:---------|:---------|
| Windows 8.1 | Центр обновления Windows | |
| Windows 8 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows 7 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Vista с пакетом обновления 2 (SP2) | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows XP с пакетами обновления 2 и 3 (SP2, SP3) | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| - | | |
| Windows Server 2012 R2 | Центр обновления Windows | |
| Windows Server 2012 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Server 2008 R2 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже.|
| Windows Server 2008 с пакетом обновления 2 (SP 2) | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Home Server 2011 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Small Business Server 2011 | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Server 2003 R2 с пакетом обновления 2 (SP2) | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| Windows Server 2003 с пакетом обновления 2 (SP2) | Диск со службами интеграции | См. в разделе [инструкции](#install-or-update-integration-services)ниже. |
| - | | |
| Гостевые ОС Linux | диспетчер пакетов | Службы интеграции Linux встроены в дистрибутив, но может существовать необязательные обновления. ** |

Дополнительные сведения о гостевых ОС Linux, см. в разделе [виртуальных машин поддерживается Linux и FreeBSD для Hyper-V в Windows](https://technet.microsoft.com/windows-server-docs/virtualization/hyper-v/supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows).

## <a name="install-or-update-integration-services"></a>Установка или обновление служб integration services

Для узлов более ранних, чем Windows Server 2016 и Windows 10, необходимо вручную установить или обновить службы интеграции в гостевых операционных систем. 
  
1.  Откройте диспетчер Hyper-V. Меню "Сервис" диспетчера серверов щелкните **диспетчера Hyper-V**.  
  
2.  Подключитесь к виртуальной машине. Щелкните правой кнопкой мыши виртуальную машину и нажмите кнопку **Connect**.  
  
3.  В меню "Действие" средства "Подключение к виртуальной машине" выберите команду **Вставьте установочный диск служб интеграции**. Это действие загружает установочный диск в виртуальный DVD-дисковод. В зависимости от гостевой операционной системы может потребоваться запуск установки вручную.  
  
4.  По завершении установки все службы интеграции станут доступны для использования.

Эти действия нельзя автоматизировать или выполнить в сеансе Windows PowerShell для сети виртуальных машин. Их можно применить к автономных образам VHDX; [см. в записи блога](https://blogs.technet.microsoft.com/virtualization/2013/04/18/how-to-install-integration-services-when-the-virtual-machine-is-not-running/).
