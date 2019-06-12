---
title: Используйте Windows Admin Center для управления обновлениями операционной системы с управлением обновлениями Azure
description: Обновляет использования Windows Admin Center (Гонолулу проекта) для настройки управления обновлениями в Azure для управления операционной системы.
ms.technology: manage
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 07/17/2018
ms.localizationpriority: low
ms.prod: windows-server-threshold
ms.openlocfilehash: 79b18e9963fba0993a7f34b1409edba6abfd48f0
ms.sourcegitcommit: 48bb3e5c179dc520fa879b16c9afe09e07c87629
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66452543"
---
# <a name="use-windows-admin-center-to-manage-operating-system-updates-with-azure-update-management"></a>Используйте Windows Admin Center для управления обновлениями операционной системы с управлением обновлениями Azure

[Дополнительные сведения о Azure интеграция с Windows Admin Center.](../plan/azure-integration-options.md)

Azure управление обновлениями — это решение в службе автоматизации Azure, которая позволяет управлять обновлениями и исправлениями для нескольких машин, в одном месте, а не на каждом из серверов. Управление обновлениями Azure можно быстро оценить состояние доступных обновлений, запланировать установку необходимых обновлений и проверить результаты развертывания, чтобы убедиться, что обновления, которые успешно применены. Это возможно, являются ли компьютеры виртуальных машин Azure, размещена в других поставщиков облачных служб или в локальной среде. [Дополнительные сведения об управлении обновлениями в Azure.](https://docs.microsoft.com/azure/automation/automation-update-management)

С помощью Windows Admin Center можно легко установить и использовать управление обновлениями Azure обновления на управляемых серверах. Если у вас нет рабочей области Log Analytics в подписке Azure, Windows Admin Center автоматически настроить сервер и создать необходимые ресурсы Azure в подписке и указанном вами расположении. При наличии существующую рабочую область Log Analytics, Windows Admin Center может автоматически настроить сервер для использования обновлений из управления обновлениями в Azure.  

Чтобы начать работу, перейти к средству обновления в соединении сервер и выберите «Настроить сейчас» и укажите параметры для связанных ресурсов Azure. 

После настройки сервера осуществляется посредством управления обновлениями в Azure, можно получить доступ к управления обновлениями в Azure с помощью средства обновления гиперссылки. 

[Узнайте, как прекратить использование Azure управление обновлениями для обновления сервера.](azure-monitor.md#disabling-monitoring)

Обратите внимание, что следует [регистрации шлюза Windows Admin Center с помощью Azure](../configure/azure-integration.md) перед настройкой управления обновлениями в Azure.

