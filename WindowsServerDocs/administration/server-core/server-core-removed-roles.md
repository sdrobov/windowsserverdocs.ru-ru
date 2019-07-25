---
title: Роли, службы ролей и компоненты, отсутствующие в Windows Server — Server Core
description: Сведения о ролях и компонентах, не включенных в вариант установки Server Core для Windows Server.
ms.prod: windows-server-threshold
ms.mktglfcycl: manage
ms.sitesec: library
author: lizap
ms.localizationpriority: medium
ms.date: 02/23/2018
ms.openlocfilehash: ce5107e8e0ab573df7588428db65c8b223cf1f13
ms.sourcegitcommit: 216d97ad843d59f12bf0b563b4192b75f66c7742
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68476517"
---
# <a name="roles-role-services-and-features-not-in-windows-server---server-core"></a>Роли, службы ролей и компоненты, отсутствующие в Windows Server — Server Core

> Относится к: Windows Server 2019, Windows Server 2016 и Windows Server (половина ежегодного канала)

Следующие роли, службы ролей и компоненты были удалены из варианта установки Server Core Windows Server. Используйте эти сведения, чтобы определить, работает ли параметр Server Core для вашей среды.

> [!NOTE]
> Вы также можете просмотреть список ролей, служб ролей и компонентов, [входящих в Server Core](server-core-roles-and-services.md). Это очень большой список, поэтому для получения наилучших результатов найдите в списке конкретную роль или интересующую вас функцию.

## <a name="roles-not-in-server-core"></a>Роли, не являющиеся базовыми для сервера

- Факс
- мултипоинтсерверроле
- NPAS
- WDS

## <a name="role-services-not-in-server-core"></a>Службы ролей не в Server Core
Обратите внимание, что некоторые службы роли удаленный рабочий стол включены в Server Core (посредник подключений, лицензирование, узел виртуализации), а другие — нет (шлюз, узел сеансов удаленных рабочих столов, Веб-доступ).

- Print-Scan-Server
- Печать — Интернет
- Шлюз RDS
- RDS-RD-Server
- RDS-Web — доступ
- Веб-управление — консоль
- Web-Лгци-руководства-консоль
- Развертывание WDS
- WDS — транспорт *(до Windows Server версии 1803)*

## <a name="features-not-in-server-core"></a>Компоненты, отсутствующие в Server Core

- BITS-IIS-Ext
- BitLocker — Нетворкунлокк
- Прямое воспроизведение
- Internet-Print-Client
- Порт LPR-Monitor
- MSMQ — многоадресная рассылка
- CMAK
- Удаленная поддержка
- RSAT — SMTP
- RSAT-Feature-Tools-BitLocker-Ремотеадминтул
- RSAT-BITS-Server
- RSAT — NLB
- RSAT — SNMP
- RSAT — WINS
- Средства Hyper-V-Tools
- RSAT-RDS-Tools
- RSAT-RDS-Gateway
- RSAT-RDS-Licensing-диагностика — пользовательский интерфейс
- RDS-Licensing — пользовательский интерфейс
- UpdateServices — пользовательский интерфейс
- RSAT — ADCS
- RSAT-ADCS-управление
- RSAT-Online-ответчик
- RSAT-ADRMS
- RSAT-Fax
- RSAT-File-Services
- RSAT-DFS-SC-Con
- RSAT-FSRM-управление
- RSAT-NFS-Admin
- RSAT-NPAS
- RSAT-Print-Services
- RSAT-ва-Tools
- WDS — Админпакк
- SMTP-сервер
- TFTP — клиент
- WebDAV — перенаправитель
- Биометрический — платформа
- Защитник Windows-GUI
- Windows-Identity-Foundation
- PowerShell — интегрированная среда сценариев
- Поиск-служба
- Windows-TIFF-IFilter
- Беспроводные сети
- Средство просмотра XPS

