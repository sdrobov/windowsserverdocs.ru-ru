---
title: Что такое Server Core?
description: Дополнительные сведения о варианте установки Server Core в Windows Server
ms.prod: windows-server
ms.mktglfcycl: manage
ms.sitesec: library
author: lizap
ms.localizationpriority: medium
ms.date: 02/20/2018
ms.openlocfilehash: 17bca691fef0ed9478c8ddb49e0511b0a16ac7b7
ms.sourcegitcommit: 75e87fef264e30af3dfeb57923d5d82b0c51de5d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85279619"
---
# <a name="what-is-the-server-core-installation-option-in-windows-server"></a>Что такое вариант установки Server Core в Windows Server?

> Область применения: Windows Server 2019, Windows Server 2016 и Windows Server (половина ежегодного канала)

Параметр Server Core — это минимальный вариант установки, доступный при развертывании выпуска Standard или Datacenter Edition Windows Server. Server Core включает большинство ролей сервера, но не все. Серверные ядра имеют меньше места на диске и, следовательно, менее подвержены атакам из-за меньшей базы кода.

## <a name="server-core-vs-server-with-desktop-experience"></a>Сервер (ядро) vs сервер с возможностями рабочего стола

При установке Windows Server устанавливаются только те роли сервера, которые были выбраны. Это позволяет сократить общий объем Windows Server. Однако при установке параметра «сервер с возможностями рабочего стола» устанавливается множество служб и других компонентов, которые часто не требуются для конкретного сценария использования.

Дело в том, где приводятся основные серверные компоненты: Установка Server Core исключает все службы и другие функции, которые не являются обязательными для поддержки некоторых часто используемых ролей сервера. Например, серверу Hyper-V не нужен графический интерфейс пользователя (GUI), так как вы можете управлять практически всеми аспектами Hyper-V из командной строки с помощью Windows PowerShell или с помощью диспетчера Hyper-V.

## <a name="the-server-core-difference---core-capabilities-without-the-frills"></a>Отличия ядра сервера от основных возможностей без простое

После завершения установки Server Core в системе и входа в систему в первый раз вы сможете немного неожиданно. Основное различие между вариантами установки «сервер с возможностями рабочего стола» и «ядро сервера» состоит в том, что Server Core не включает следующие пакеты оболочки GUI:

- Microsoft-Windows-Server-Shell-Package
- Microsoft-Windows-Server-GUI-руководства-Package
- Microsoft-Windows-Server-ГИП-RSAT-Package
- Microsoft-Windows-Кортана-PAL-Настольный-пакет

Иными словами, в архитектуре Server Core **нет рабочего стола** . При поддержке функций, необходимых для поддержки традиционных бизнес-приложений и рабочих нагрузок на основе ролей, серверное ядро не имеет традиционного интерфейса рабочего стола. Вместо этого серверное ядро предназначено для удаленного управления с помощью командной строки, PowerShell или средства графического пользовательского интерфейса (например, [RSAT](../../remote/remote-server-administration-tools.md) или [центра администрирования Windows](../../manage/windows-admin-center/overview.md)).

В дополнение к отсутствию пользовательского интерфейса ядро сервера также отличается от сервера с возможностями рабочего стола следующим образом.

- Server Core не имеет специальных средств
- Отсутствует OOBE (встроенное взаимодействие) для настройки ядра сервера
- Отсутствует поддержка звука

В следующей таблице показано, какие приложения доступны *локально* на сервере Server Core VS Server с возможностями рабочего стола. **Важно**. в большинстве случаев приложения, перечисленные ниже, могут быть запущены удаленно с клиентского компьютера Windows и использованы для управления установкой Server Core.

> [!NOTE]
> Этот список предназначен для краткого справочника — он не должен быть полным списком.


| Приложение                        | Основные серверные компоненты     | Сервер с возможностями рабочего стола |
|------------------------------------|-----------------|--------------------------------|
| С помощью командной строки                     | доступен       | доступен                      |
| Windows PowerShell или Microsoft .NET | доступен       | доступен                      |
| Perfmon.exe                        | недоступно   | доступен                      |
| WinDbg (графический пользовательский интерфейс)                       | Поддерживается       | Поддерживается                      |
| Resmon.exe                         | недоступно   | доступен                      |
| Regedit                            | доступен       | доступен                      |
| Fsutil.exe                         | доступен       | доступен                      |
| Disksnapshot.exe                   | недоступно   | доступен                      |
| Diskpart.exe                       | доступен       | доступен                      |
| Diskmgmt. msc                       | недоступно   | доступен                      |
| Devmgmt. msc                        | недоступно   | доступен                      |
| Диспетчер серверов                     | недоступно   | доступен                      |
| Mmc.exe                            | недоступно   | доступен                      |
| Файл eventvwr                           | недоступно   | доступен                      |
| Wevtutil (запросы событий)           | доступен       | доступен                      |
| Services.msc                       | недоступно   | доступен                      |
| Панель управления                      | недоступно   | доступен                      |
| Центр обновления Windows (графический пользовательский интерфейс)               | недоступно   | доступен                      |
| Проводник                   | недоступно   | доступен                      |
| Панель задач                            | недоступно   | доступен                      |
| Уведомления на панели задач              | недоступно   | доступен                      |
| Панели Диспетчер задач                            | доступен       | доступен                      |
| Internet Explorer или пограничная          | недоступно   | доступен                      |
| Встроенная система справки               | недоступно   | доступен                      |
| Оболочка Windows 10                   | недоступно   | доступен                      |
| Проигрыватель Windows Media               | недоступно   | доступен                      |
| PowerShell                         | доступен       | доступен                      |
| Интегрированная среда сценариев PowerShell                     | недоступно   | доступен                      |
| Редактор IME для PowerShell                     | доступен       | доступен                      |
| Mstsc.exe                          | недоступно   | доступен                      |
| Службы удаленных рабочих столов            | доступен       | доступен                      |
| В диспетчере Hyper-V                    | недоступно   | доступен                      |
| WordPad\*                          | недоступно   | доступен                      |


Дополнительные сведения *о том, что входит* в ядро сервера, см. [в разделе роли, службы ролей и функции, включенные в Windows Server-Server Core](server-core-roles-and-services.md). Дополнительные сведения о том, что *не* включено в Server Core, см. [в разделе роли, службы ролей и компоненты, не включенные в Server Core](server-core-removed-roles.md) .

\*Для чтения. Файлы RTF, локально хранящиеся на SKU Server Core, пользователи могут копировать файлы на другой компьютер Windows, где находится WordPad.

## <a name="get-started-using-server-core"></a>Приступая к работе с Server Core

Используйте следующие сведения для установки, настройки и управления вариантом установки основных серверных компонентов Windows Server.

Установка основных серверных компонентов:
- [Роли, службы ролей и компоненты, входящие в Server Core](server-core-roles-and-services.md)
- [Роли, службы ролей и компоненты, отсутствующие в Server Core](server-core-removed-roles.md)
- [Установка варианта установки Server Core](../../get-started/getting-started-with-server-core.md)
- [Настройка ядра сервера с помощью средства SConfig](../../get-started/sconfig-on-ws2016.md)

Использование Server Core:
- [Основные задачи администрирования Server Core с помощью Windows PowerShell или командной строки](server-core-administer.md)
- [Управление основными серверными компонентами](server-core-manage.md)
- [Обновление основных серверных компонентов](server-core-servicing.md)
- [Настройка файлов дампа памяти](server-core-memory-dump.md)
