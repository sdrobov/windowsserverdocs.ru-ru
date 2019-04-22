---
title: Ролей, служб ролей и компонентов не в Windows Server - основных серверных компонентов
description: Дополнительные сведения о ролях и компонентах, не включена в вариант установки Server Core для Windows Server.
ms.prod: windows-server-threshold
ms.mktglfcycl: manage
ms.sitesec: library
author: lizap
ms.localizationpriority: medium
ms.date: 02/23/2018
ms.openlocfilehash: 308bc8a5d25e2ec67438f0ee03cbfce6f7411ca2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825535"
---
# <a name="roles-role-services-and-features-not-in-windows-server---server-core"></a>Ролей, служб ролей и компонентов не в Windows Server - основных серверных компонентов

> Относится к: Windows Server (полугодовой канал) и Windows Server 2016

Следующие роли, службы ролей и компоненты были удалены из с вариантом установки основных серверных компонентов Windows Server. Используйте эти сведения помогут понять, если параметр Server Core работает для вашей среды.

> [!NOTE]
> Также можно просмотреть список ролей, служб ролей и функций, [включаются в Server Core](server-core-roles-and-services.md). Это очень большой список, для получения наилучших результатов выполните поиск этого списка для конкретных ролей и компонентов, вас интересует.

## <a name="roles-not-in-server-core"></a>Роли не в основных серверных компонентов

- Факс
- MultiPointServerRole
- NPAS
- СЛУЖБЫ РАЗВЕРТЫВАНИЯ WINDOWS

## <a name="role-services-not-in-server-core"></a>Службы ролей не в основных серверных компонентов
Обратите внимание, что для некоторых служб ролей удаленного рабочего стола, включаются в основных серверных компонентов (посредника подключений, лицензирование, узел виртуализации), а другие — нет (шлюз RD Session Host Web Access).

- Сервер печати сканирования
- Печать из Интернета
- Шлюз служб удаленных рабочих СТОЛОВ
- RDS-сервера удаленных рабочих Столов
- Веб-доступа к RDS
- Web-Mgmt-Console
- Веб Lgcy-Mgmt-Console
- Развертывания WDS
- WDS-Transport *(до Windows Server версии ниже 1803)*

## <a name="features-not-in-server-core"></a>Функции не в основных серверных компонентов

- BITS-IIS-Ext
- BitLocker NetworkUnlock
- Direct-Play
- Интернет Print-Client
- Монитор порта LPR
- Многоадресной рассылки MSMQ
- ПАКЕТ АДМИНИСТРИРОВАНИЯ ДИСПЕТЧЕРА ПОДКЛЮЧЕНИЙ
- Удаленный помощник
- СРЕДСТВА УДАЛЕННОГО АДМИНИСТРИРОВАНИЯ СЕРВЕРА SMTP
- RSAT-функция — Сервис BitLocker-RemoteAdminTool
- RSAT-сервер Bits
- RSAT-NLB
- RSAT-SNMP
- СРЕДСТВА УДАЛЕННОГО АДМИНИСТРИРОВАНИЯ СЕРВЕРА WINS
- Hyper-V-Tools
- Средства RSAT-служб удаленных рабочих СТОЛОВ
- RSAT-RDS-Gateway
- Средства удаленного администрирования сервера RDS-Licensing диагностики-пользовательского интерфейса
- RDS-лицензирования-пользовательский Интерфейс
- UpdateServices-пользовательского интерфейса
- RSAT-ADCS
- RSAT-ADCS-Mgmt
- RSAT--ответчика
- RSAT-ADRMS
- Средства удаленного администрирования сервера факсов
- RSAT-File-Services
- RSAT-DFS-Mgmt-Con
- RSAT-FSRM-Mgmt
- RSAT-NFS-Admin
- RSAT-NPAS
- RSAT-Print-Services
- Средства RSAT-ва
- WDS AdminPack
- SMTP-сервер
- Клиент TFTP
- Перенаправитель WebDAV
- Биометрическая платформа
- Windows Defender графического пользовательского интерфейса
- Windows Identity Foundation —
- Интегрированная среда Сценариев PowerShell
- Служба поиска
- Windows TIFF-IFilter
- Беспроводные сети
- Средство просмотра XPS

