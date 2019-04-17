---
title: "Использование сборщика журналов Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6985518-b42d-4cfb-9761-eaa75306b6d7
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: d003c6a45159548f7e34d86ca242f74868659d2f
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="use-the-windows-server-essentials-log-collector"></a>Использование сборщика журналов Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

При устранении проблем с компьютерами, представитель службы поддержки клиентов Майкрософт и поддержки может попросить вас собрать журналы из серверов, сети, и / или компьютеров с помощью сборщика журналов Windows Server Essentials.  
  
 Сборщик журналов копирует журналы программ, событий и прочую информацию среды в одном ZIP-файл в указанном расположении. Можно запустить сборщик журналов непосредственно с сервера или любой компьютер в сети или с помощью удаленного подключения к компьютерам.  
  
> [!NOTE]
>  -   Сборщик журналов не анализ сетевых проблем или внести изменения на любой сервер или компьютер в сети. Дополнительные сведения о способах устранения неполадок см. в справочной документации по вашему серверу.  
> -   В этом руководстве компьютеров в сети, за исключением сервера, называются сетевых компьютеров.  
> -   [Загрузить пакет установки сборщика журналов Windows Server Essentials](https://go.microsoft.com/fwlink/?LinkID=266341).  
  
 Чтобы установить и запустить сборщик журналов, выполните действия, приведенные в следующих разделах.  
  

1.  [Установка сборщика журналов](Install-the-Windows-Server-Essentials-Log-Collector.md)  
  
2.  [Запуск сборщика журналов](Run-the-Windows-Server-Essentials-Log-Collector.md)  

1.  [Установка сборщика журналов](../support/Install-the-Windows-Server-Essentials-Log-Collector.md)  
  
2.  [Запуск сборщика журналов](../support/Run-the-Windows-Server-Essentials-Log-Collector.md)  

  
## <a name="environment-information-collected"></a>Сбор сведений о среде  
 Для каждого компьютера сети или на сервере, указанном в сборщик журналов собирает следующие сведения о среде и помещает их в файл журнала коллекции.  
  
-   Версия операционной системы  
  
-   Изготовитель и описание ЦП  
  
-   Объем памяти и ее выделение  
  
-   Сетевые адаптеры, связанные с TCP/IP  
  
-   Языковой стандарт  
  
-   Процессы  
  
-   Конфигурация хранилища  
  
-   Сведения о файле узла  
  
-   Журналы событий, включая приложения, System, Windows Server и Media Center  
  
-   Сообщения диспетчера управления службами  
  
-   События перезагрузки и центра обновления Windows  
  
-   Системные ошибки и ошибки приложений  
  
## <a name="services-information-collected"></a>Собираемые сведения о службах  
  
### <a name="server-services"></a>Службы сервера  
  
-   Windows Server служба архивации клиентских компьютеров  
  
-   Windows Server клиентского компьютера поставщик службы резервного копирования  
  
-   Поставщик устройств Windows Server  
  
-   Управление доменными именами Windows Server  
  
-   Реестр поставщика службы Windows Server  
  
-   Поставщик параметров Windows Server  
  
-   Служба UPnP-устройств Windows Server  
  
-   Поставщик средств администрирования Windows Server веб-сайт удаленного доступа  
  
-   Служба работоспособности Windows Server  
  
-   Служба хранилища Windows Server  
  
-   Служба SQM Windows Server  
  
### <a name="network-computer-services"></a>Службы сетевой компьютер  
  
-   Windows Server клиентского компьютера поставщик службы резервного копирования  
  
-   Служба работоспособности Windows Server  
  
-   Реестр поставщика службы Windows Server  
  
-   Служба SQM Windows Server  
  
## <a name="logs-and-registry-information-collected"></a>Журналы и сбор сведений о реестре  
 Для каждого компьютера сети или сервера, указанного сборщик журналов собирает сведения журналов и реестра от сервера и компьютеров сети следующим образом.  
  
### <a name="server-logs-and-registry-information"></a>Журналы сервера и данных реестра  
  
-   Журналы серверного продукта из \Microsoft\Windows Server\Logs < ProgramData\ >  
  
-   Запланированные задачи  
  
-   Журналы API установки  
  
-   Журналы центра обновления Windows  
  
-   Файл оповещений о работоспособности  
  
-   Файл сведений об устройствах  
  
-   Файл журнала архивации сервера  
  
-   Файл журнала panther  
  
-   Службы  
  
-   Разделы реестра из  
  
    -   \\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\  
  
    -   \\\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DevicesProviderSvc  
  
    -   \\\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DomainManagerProviderSvc  
  
### <a name="network-computer-logs-and-registry-information"></a>Журналы компьютеров сети и данные реестра  
  
-   Журналы компьютеров сети продукта в < ProgramData\ > \Microsoft\Windows Server\Logs  
  
-   Файл оповещений о работоспособности в \Microsoft\Windows Server\Data < ProgramData\ >  
  
-   Журналы центра обновления Windows  
  
-   Журналы API установки  
  
-   Сведения о запланированных задачах  
  
-   Разделы реестра из \\\HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows Server\  
  
## <a name="logs-for-computers-that-do-not-run-a-version-of-the-windows-operating-system"></a>Журналы компьютеров, работающих не под управлением версии операционной системы Windows  
 Сборщик журналов не собирает файлы журналов с компьютеров, работающих не под управлением версии операционной системы Windows. Для компьютеров, отличных от Windows вручную скопируйте следующие файлы журнала, в то же расположение, где хранятся файлы сборщика журналов.  
  
-   Вышеперечисленные  
  
-   Server.log библиотеки или журналы и Windows  
  
-   Library/Logs/CrashReporter/LaunchPad-< nnn\ > (скопируйте все файлы LaunchPad-< nnn\ > .crash)  
  
-   Library/Logs/DiagnosticReports/LaunchPad-< nnn\ > (скопируйте все файлы LaunchPad-< nnn\ > .crash)  
  
## <a name="see-also"></a>См. также:  
  

-   [Устранение неполадок сборщика журналов](Troubleshoot-Windows-Server-Essentials-Log-Collector-Errors.md)

-   [Устранение неполадок сборщика журналов](../support/Troubleshoot-Windows-Server-Essentials-Log-Collector-Errors.md)

