---
title: Ведение журналов событий
description: Ведение журнала событий из Windows Admin Center (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 06/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: d91b92cb3bba99ae4aa96a96650a251a6df4cea5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59849305"
---
# <a name="use-event-logging-in-windows-admin-center-to-gain-insight-into-management-activities-and-track-gateway-usage"></a>Использовать ведение журнала событий в Windows Admin Center для лучшего понимания действий по управлению и отслеживать использование шлюза

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Windows Admin Center записывает журналы событий всегда просматривать действия по управлению, выполняемой на серверах в вашей среде, а также об устранении проблем Windows Admin Center.

## <a name="gain-insight-into-management-activities-in-your-environment-through-user-action-logging"></a>Анализировать активность управления в среде с помощью ведения журнала действий пользователя

Windows Admin Center позволяет отслеживать действия по управлению, выполняемых на серверах в вашей среде ведение журнала действий для **Microsoft ServerManagementExperience** канал событий в журнале событий, управляемых сервер, с EventID 4000 и SMEGateway источника. Windows Admin Center только регистрирует действия, на управляемом сервере, поэтому вы не увидите события, если пользователь обращается к серверу в целях только для чтения.

Зарегистрированные события включают следующие сведения:

| Ключ           | Значение                                                                                              |
|---------------|----------------------------------------------------------------------------------------------------|
| PowerShell    | Имя сценария PowerShell, запущенного на сервере, если действие выполнили сценарий PowerShell |
| CIM           | Вызов CIM, запущенного на сервере, если действие выполнялся вызов CIM                        |
| Модуль        | Средства (или модуля) где выполнялся действие                                                     |
| Шлюз       | Имя машины шлюза Windows Admin Center, где была запущена действие                     |
| UserOnGateway | Имя пользователя для доступа к шлюзу Windows Admin Center и для выполнения определенного действия                    |
| UserOnTarget  | Имя пользователя, используемое для доступа к целевой управляемого сервера, если он отличается от userOnGateway (т. е. пользователь, получить доступ с помощью сервера, используя учетные данные «Управление как») |
| Делегирование    | Логическое значение: Если целевой объект под отношениях доверия с сервером шлюза и удостоверения делегируются с клиентского компьютера пользователя             |
| LAPS          | Логическое значение: Если подключился пользователь к серверу с помощью [LAPS](https://technet.microsoft.com/mt227395.aspx) учетные данные                          |
| Файл          | Имя файла передачи, если действие было передачи файлов                                |

## <a name="learn-about-windows-admin-center-activity-with-event-logging"></a>Дополнительные сведения о действиях Windows Admin Center с ведением журнала событий

Windows Admin Center записывает действия шлюза канал событий на компьютере со шлюзом для устранения неполадок и просмотр метрик использования. Эти события регистрируются **Microsoft ServerManagementExperience** канал событий.

[Дополнительные сведения об устранении неполадок Windows Admin Center.](troubleshooting.md)
