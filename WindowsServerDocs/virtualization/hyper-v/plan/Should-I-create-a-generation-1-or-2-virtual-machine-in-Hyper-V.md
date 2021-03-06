---
title: Следует ли создать виртуальную машину поколения 1 или 2 в Hyper-V?
description: Предоставляет такие рекомендации, как поддерживаемые методы загрузки и другие различия в функциях, позволяющие выбрать, какое поколение соответствует вашим потребностям.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.topic: article
ms.assetid: 02e31413-6140-4723-a8d6-46c7f667792d
author: kbdazure
ms.author: kathydav
ms.date: 12/05/2016
ms.openlocfilehash: 0e8b8dbaa937229b5a87560f3993bb07d7cd7ff8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860777"
---
# <a name="should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v"></a>Следует ли создать виртуальную машину поколения 1 или 2 в Hyper-V?

>Область применения: Windows 10, Windows Server 2016, Microsoft Hyper-V Server 2016, Windows Server 2019, Microsoft Hyper-V Server 2019

> [!NOTE]
> Если вы планируете загружать виртуальные машины Windows из локальной среды в Microsoft Azure, виртуальные машины поколения 1 и поколения 2 в формате VHD-файла и поддерживаются диски фиксированного размера. Дополнительные сведения о возможностях поколения 2, поддерживаемых в Azure, см. в статье [виртуальные машины поколения 2 в Azure](https://docs.microsoft.com/azure/virtual-machines/windows/generation-2) . Дополнительные сведения о загрузке VHD или VHDX в формате Windows см. в статье [Подготовка VHD или VHDX Windows к отправке в Azure](https://docs.microsoft.com/azure/virtual-machines/windows/prepare-for-upload-vhd-image).

Ваш выбор для создания виртуальной машины поколения 1 или поколения 2 зависит от того, какую операционную систему на виртуальной машине вы хотите установить, и метод загрузки, который вы хотите использовать для развертывания виртуальной машины. Рекомендуется создать виртуальную машину версии 2, чтобы воспользоваться преимуществами таких функций, как безопасная загрузка, за исключением случаев, когда выполняется одно из следующих условий.  

- Виртуальный жесткий диск, с которого требуется выполнить загрузку, не [совместим с UEFI](https://technet.microsoft.com/library/hh824898.aspx).  
- Поколение 2 не поддерживает операционную систему, которую нужно запустить на виртуальной машине.  
- Поколение 2 не поддерживает метод загрузки, который вы хотите использовать.  

Дополнительные сведения о возможностях виртуальных машин версии 2 см. в статье [Совместимость компонентов Hyper-V по поколениям и гостевым системам](../Hyper-V-feature-compatibility-by-generation-and-guest.md).

Невозможно изменить поколение виртуальной машины после ее создания. Поэтому рекомендуется ознакомиться с рекомендациями, а также выбрать операционную систему, метод загрузки и функции, которые необходимо использовать перед тем, как выбрать поколение.  

## <a name="which-guest-operating-systems-are-supported"></a>Какие гостевые операционные системы поддерживаются?

Виртуальные машины поколения 1 поддерживают большинство гостевых операционных систем. Виртуальные машины поколения 2 поддерживают большинство 64-разрядных версий Windows и более текущих версий операционных систем Linux и FreeBSD. Используйте следующие разделы, чтобы узнать, какое поколение виртуальной машины поддерживает операционную систему на виртуальной машине, которую вы хотите установить.  

- [Поддержка гостевых операционных систем Windows](#windows-guest-operating-system-support)  

- [Поддержка гостевых операционных систем CentOS и Red Hat Enterprise Linux](#centos-and-red-hat-enterprise-linux-guest-operating-system-support)  

- [Поддержка гостевой операционной системы Debian](#debian-guest-operating-system-support)  

- [Поддержка гостевой операционной системы FreeBSD](#freebsd-guest-operating-system-support)  

- [Поддержка Oracle Linux гостевой операционной системы](#oracle-linux-guest-operating-system-support)  

- [Поддержка гостевой операционной системы SUSE](#suse-guest-operating-system-support)  

- [Поддержка гостевой операционной системы Ubuntu](#ubuntu-guest-operating-system-support)  

### <a name="windows-guest-operating-system-support"></a>Поддержка гостевых операционных систем Windows

В следующей таблице показано, какие 64-разрядные версии Windows можно использовать в качестве гостевой операционной системы для виртуальных машин поколения 1 и 2.  

|64-разрядные версии Windows|Поколение 1|Поколение 2|  
|-------------------------------|----------------|----------------|  
| Windows Server 2019 |&#10004;|&#10004;|  
| Windows Server 2016 |&#10004;|&#10004;|  
| Windows Server 2012 R2 |&#10004;|&#10004;|  
| Windows Server 2012 |&#10004;|&#10004;|  
|Windows Server 2008 R2|&#10004;| &#10006;|  
|Windows Server 2008|&#10004;| &#10006;|  
|Windows 10|&#10004;|&#10004;|  
|Windows 8.1|&#10004;|&#10004;|  
|Windows 8|&#10004;|&#10004;|  
|Windows 7|&#10004;| &#10006;|

В следующей таблице показано, какие 32-разрядные версии Windows можно использовать в качестве гостевой операционной системы для виртуальных машин поколения 1 и 2.

|32-разрядные версии Windows|Поколение 1|Поколение 2|  
|-------------------------------|----------------|----------------|  
|Windows 10|&#10004;| &#10006;|  
|Windows 8.1|&#10004;| &#10006;|  
|Windows 8|&#10004;| &#10006;|  
|Windows 7|&#10004;| &#10006;|  

### <a name="centos-and-red-hat-enterprise-linux-guest-operating-system-support"></a>Поддержка гостевых операционных систем CentOS и Red Hat Enterprise Linux

В следующей таблице показано, какие версии Red Hat Enterprise Linux \(RHEL\) и CentOS можно использовать в качестве операционной системы на виртуальной машине поколения 1 и 2.

|Версии операционной системы|Поколение 1|Поколение 2|  
|-----------------------------|----------------|----------------|  
|Серия RHEL/CentOS 7. x|&#10004;|&#10004;|  
|Серия RHEL/CentOS 6. x|&#10004;|&#10004;<br />**Примечание.** Поддерживается только в Windows Server 2016 и более поздних версиях.|  
|Серия RHEL/CentOS 5. x|&#10004;| &#10006;|  

Дополнительные сведения см. [в статье CentOS and Red Hat Enterprise Linux Virtual Machines in Hyper-V](../Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md).  

### <a name="debian-guest-operating-system-support"></a>Поддержка гостевой операционной системы Debian  

В следующей таблице показано, какие версии Debian можно использовать в качестве гостевой операционной системы для виртуальных машин поколения 1 и 2.

|Версии операционной системы|Поколение 1|Поколение 2|  
|-----------------------------|----------------|----------------|  
|Серия Debian 7. x|&#10004;| &#10006;|  
|Серия Debian 8. x|&#10004;|&#10004;|  

Дополнительные сведения см. [в статье Debian Virtual Machines on Hyper-V](../Supported-Debian-virtual-machines-on-Hyper-V.md).  

### <a name="freebsd-guest-operating-system-support"></a>Поддержка гостевой операционной системы FreeBSD

В следующей таблице показано, какие версии FreeBSD можно использовать в качестве гостевой операционной системы для виртуальных машин поколения 1 и 2.  

|Версии операционной системы|Поколение 1|Поколение 2|  
|-----------------------------|----------------|----------------|  
|FreeBSD 10 и 10,1|&#10004;| &#10006;|  
|FreeBSD 9,1 и 9,3|&#10004;| &#10006;|  
|FreeBSD 8,4|&#10004;| &#10006;|  

Дополнительные сведения см. [в статье виртуальные машины FreeBSD в Hyper-V](../Supported-FreeBSD-virtual-machines-on-Hyper-V.md).  

### <a name="oracle-linux-guest-operating-system-support"></a>Поддержка Oracle Linux гостевой операционной системы  

В следующей таблице показаны версии серии ядра, совместимые с Red Hat, которые можно использовать в качестве гостевой операционной системы для виртуальных машин поколения 1 и 2.  

|Версии серии ядра, совместимые с Red Hat|Поколение 1|Поколение 2|  
|---------------------------------------------|----------------|----------------|  
|Серия Oracle Linux 7. x|&#10004;|&#10004;|
|Серия Oracle Linux 6. x|&#10004;| &#10006;|  

В следующей таблице показано, какие версии неповрежденного корпоративного ядра можно использовать в качестве гостевой операционной системы для виртуальных машин поколения 1 и 2.

|Неповрежденные версии ядра Enterprise (UEK)|Поколение 1|Поколение 2|  
|--------------------------------------------------|----------------|----------------|  
|Oracle Linux UEK R3 QU3|&#10004;| &#10006;|  
|Oracle Linux UEK R3 QU2|&#10004;| &#10006;|  
|Oracle Linux UEK R3 QU1|&#10004;| &#10006;|  

Дополнительные сведения см. [в статье Oracle Linux виртуальные машины в Hyper-V](../Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md).  

### <a name="suse-guest-operating-system-support"></a>Поддержка гостевой операционной системы SUSE

В следующей таблице показано, какие версии SUSE можно использовать в качестве гостевой операционной системы для виртуальных машин поколения 1 и 2.

|Версии операционной системы|Поколение 1|Поколение 2|  
|-----------------------------|----------------|----------------|  
|Серия SUSE Linux Enterprise Server 12|&#10004;|&#10004;|  
|Серия SUSE Linux Enterprise Server 11|&#10004;| &#10006;|  
|Open SUSE 12,3|&#10004;| &#10006;|  

Дополнительные сведения см. в статье о [виртуальных машинах SUSE в Hyper-V](../Supported-SUSE-virtual-machines-on-Hyper-V.md).  

### <a name="ubuntu-guest-operating-system-support"></a>Поддержка гостевой операционной системы Ubuntu

В следующей таблице показано, какие версии Ubuntu можно использовать в качестве гостевой операционной системы для виртуальных машин поколения 1 и 2.

|Версии операционной системы|Поколение 1|Поколение 2|  
|-----------------------------|----------------|----------------|  
|Ubuntu 14,04 и более поздние версии|&#10004;|&#10004;|  
|Ubuntu 12.04|&#10004;| &#10006;|  

Дополнительные сведения см. в статье о [виртуальных машинах Ubuntu в Hyper-V](../Supported-Ubuntu-virtual-machines-on-Hyper-V.md).  

## <a name="how-can-i-boot-the-virtual-machine"></a>Как можно загрузить виртуальную машину?

В следующей таблице показано, какие методы загрузки поддерживаются виртуальными машинами версии 1 и поколения 2.  

|Метод загрузки|Поколение 1|Поколение 2|  
|---------------|----------------|----------------|  
|PXE-загрузка с помощью стандартного сетевого адаптера;| &#10006;|&#10004;|  
|Загрузка PXE с помощью устаревшего сетевого адаптера|&#10004;| &#10006;|  
|Загрузка с виртуального жесткого диска SCSI (. VHDX) или виртуальный DVD-диск (. ISO| &#10006;|&#10004;|  
|Загрузка из виртуального жесткого диска контроллера IDE (. VHD) или виртуальный DVD-диск (. ISO|&#10004;| &#10006;|  
|Загрузка с дискеты (. VFD|&#10004;| &#10006;|  

## <a name="what-are-the-advantages-of-using-generation-2-virtual-machines"></a>Каковы преимущества использования виртуальных машин версии 2?

Ниже приведены некоторые преимущества, получаемые при использовании виртуальной машины поколения 2.  
- **Безопасная загрузка** Это функция, которая проверяет, подписан ли загрузчик доверенным центром сертификации в базе данных UEFI, чтобы предотвратить запуск неавторизованного встроенного по, операционных систем или драйверов UEFI во время загрузки. В виртуальных машинах поколения 2 безопасная загрузка включена по умолчанию. Если необходимо запустить операционную систему на виртуальной машине, которая не поддерживается безопасной загрузкой, ее можно отключить после создания виртуальной машины.  Дополнительные сведения см. в статье [Безопасная загрузка](https://technet.microsoft.com/library/dn486875.aspx).  

    Для защиты виртуальных машин Linux с поколением 2 необходимо выбрать шаблон безопасной загрузки ЦС UEFI при создании виртуальной машины.  

- **Больший загрузочный том** Максимальный загрузочный том для виртуальных машин поколения 2 составляет 64 ТБ. Это максимальный размер диска, поддерживаемый. Формате. Для виртуальных машин поколения 1 максимальный загрузочный том составляет 2 ТБ для. VHDX и 2040GB для. VHD. Дополнительные сведения см. в статье [Обзор формата виртуального жесткого диска Hyper-V](https://technet.microsoft.com/library/hh831446.aspx).  

  Кроме того, вы можете увидеть небольшое повышение загрузки виртуальной машины и время установки с помощью виртуальных машин версии 2.

## <a name="whats-the-difference-in-device-support"></a>В чем разница в поддержке устройств?

В следующей таблице сравниваются устройства, доступные для виртуальных машин поколения 1 и 2.  

|Устройство поколения 1|Замена в поколении 2|Усовершенствования в поколении 2|  
|-----------------------|----------------------------|-----------------------------|  
|Контроллер интерфейса IDE|Виртуальный SCSI-контроллер|Загрузка из файла .VHDX (максимальный размер 64 ТБ, возможность оперативного изменения размера)|  
|Дисковод IDE|Виртуальный дисковод SCSI|Поддержка до 64 DVD-устройств SCSI на SCSI-контроллер.|  
|Традиционная BIOS|Встроенное ПО UEFI|Безопасная загрузка|  
|Традиционный сетевой адаптер|Синтетический сетевой адаптер|Сетевая загрузка по протоколам IPv4 и IPv6|  
|Контроллер гибких дисков и DMA|Контроллер гибких дисков не поддерживается|Н/Д|  
|Универсальный асинхронный приемопередатчик (UART) для COM-портов|Дополнительный UART для отладки|Более быстрый и надежный|  
|Контроллер клавиатуры i8042|Программный ввод|Использует меньше ресурсов, так как нет эмуляции. Также уменьшает уязвимость гостевой операционной системы|  
|Клавиатура PS/2|Программная клавиатура|Использует меньше ресурсов, так как нет эмуляции. Также уменьшает уязвимость гостевой операционной системы|  
|Мышь PS/2|Программная мышь|Использует меньше ресурсов, так как нет эмуляции. Также уменьшает уязвимость гостевой операционной системы|  
|S3-видео|Программное видео|Использует меньше ресурсов, так как нет эмуляции. Также уменьшает уязвимость гостевой операционной системы|  
|Шина PCI|Больше не требуется|Н/Д|  
|Программируемый контроллер прерываний (PIC)|Больше не требуется|Н/Д|  
|Программируемый интервальный таймер (PIT)|Больше не требуется|Н/Д|  
|Устройство Super I/O|Больше не требуется|Н/Д|  

## <a name="more-about-generation-2-virtual-machines"></a>Дополнительные сведения о виртуальных машинах поколения 2

Ниже приведены некоторые дополнительные советы по использованию виртуальных машин версии 2.

### <a name="attach-or-add-a-dvd-drive"></a>Подключение или добавление DVD-дисковода

- Невозможно подключить физический компакт-диск или DVD-дисковод к виртуальной машине поколения 2. Виртуальный DVD-дисковод в виртуальных машинах поколения 2 поддерживает только файлы ISO-образов. Для создания ISO-файла образа среды Windows можно использовать средство командной строки Oscdimg. Дополнительные сведения см. в разделе [Параметры командной строки Oscdimg](https://msdn.microsoft.com/library/hh824847.aspx).
- При создании новой виртуальной машины с помощью командлета Windows PowerShell New-VM у виртуальной машины поколения 2 нет DVD-дисковода. Вы можете добавить DVD-дисковод во время работы виртуальной машины.

### <a name="use-uefi-firmware"></a>Использовать встроенное по UEFI

- На физическом узле Hyper-V не требуется безопасная загрузка или встроенное по UEFI. Hyper-V предоставляет виртуальным машинам виртуальные микропрограммы, не зависящие от того, что находится на узле Hyper-V.
- Встроенное по UEFI на виртуальной машине поколения 2 не поддерживает режим настройки для безопасной загрузки.
- Мы не поддерживаем Запуск оболочки UEFI или других приложений UEFI на виртуальной машине поколения 2. Использование оболочки UEFI или приложений UEFI других разработчиков технически возможно, если они компилируются непосредственно в источниках. Если эти приложения не имеют соответствующей цифровой подписи, необходимо отключить безопасную загрузку виртуальной машины.

### <a name="work-with-vhdx-files"></a>Работа с VHDX-файлами

- Вы можете изменить размер VHDX-файла, содержащего загрузочный том для виртуальной машины поколения 2, во время работы виртуальной машины.
- Мы не поддерживаем или не рекомендуем создать VHDX-файл, который будет загрузочным для виртуальных машин поколения 1 и 2.  
- Поколение виртуальной машины — это свойство виртуальной машины, а не виртуального жесткого диска. Поэтому не удается определить, был ли VHDX-файл создан виртуальной машиной поколения 1 или поколения 2.  
- VHDX-файл, созданный с помощью виртуальной машины версии 2, можно подключить к контроллеру IDE или SCSI-контроллеру виртуальной машины поколения 1. Однако если это загрузочный VHDX-файл, виртуальная машина поколения 1 не загрузится.

### <a name="use-ipv6-instead-of-ipv4"></a>Использовать IPv6 вместо IPv4

По умолчанию виртуальные машины поколения 2 используют протокол IPv4. Чтобы использовать IPv6, выполните командлет [Set-вмфирмваре](https://technet.microsoft.com/library/dn464287.aspx) Windows PowerShell. Например, следующая команда задает предпочтительный протокол для IPv6 для виртуальной машины с именем TestVM:  

```powershell
Set-VMFirmware -VMName TestVM -IPProtocolPreference IPv6  
```  

## <a name="add-a-com-port-for-kernel-debugging"></a>Добавление COM-порта для отладки ядра

COM-порты недоступны на виртуальных машинах поколения 2, пока они не будут добавлены. Это можно сделать с помощью Windows PowerShell или инструментарий управления Windows (WMI) (WMI). Ниже показано, как это сделать с помощью Windows PowerShell.

Чтобы добавить COM-порт, выполните следующие действия.  

1. Отключите безопасную загрузку. Отладка ядра не совместима с безопасной загрузкой. Убедитесь, что виртуальная машина находится в отключенном состоянии, а затем используйте командлет [Set-вмфирмваре](https://technet.microsoft.com/library/dn464287.aspx) . Например, следующая команда отключает безопасную загрузку виртуальной машины TestVM:  

    ```powershell  
    Set-VMFirmware -Vmname TestVM -EnableSecureBoot Off  
    ```  

2. Добавьте COM-порт. Для этого используйте командлет [Set-вмкомпорт](https://technet.microsoft.com/library/hh848616.aspx) . Например, следующая команда настраивает первый COM-порт на виртуальной машине TestVM для подключения к именованному каналу Тестпипе на локальном компьютере:  

    ```powershell
    Set-VMComPort -VMName TestVM 1 \\.\pipe\TestPipe  
    ```  

> [!NOTE]  
> Настроенные COM-порты не указаны в параметрах виртуальной машины в диспетчере Hyper-V.

## <a name="see-also"></a>См. также  

- [Supported Linux and FreeBSD virtual machines for Hyper-V on Windows](../Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md) (Поддерживаемые виртуальные машины Linux и FreeBSD для Hyper-V в Windos).
- [Use local resources on Hyper-V virtual machine with VMConnect](../learn-more/Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md) (Использование локальных ресурсов на виртуальной машине с VMConnect)
- [Планирование масштабируемости Hyper-V в Windows Server 2016](Plan-for-Hyper-V-scalability-in-Windows-Server-2016.md)
