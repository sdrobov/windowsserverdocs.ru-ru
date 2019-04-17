---
title: "Задачи управления файлами"
description: "В этой статье описывается процесс автоматизации задач управления файлами"
ms.date: 7/7/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: e83d0b79117144d42a0aff748f482f3c181cb300
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="file-management-tasks"></a>Задачи управления файлами

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Задачи управления файлами автоматизируют процессы поиска наборов файлов на сервере и применения простых команд. Можно запланировать периодическое выполнение этих задач с целью сокращения повторяющихся расходов. Файлы, которые будут обрабатываться задачей управления файлами, можно определять с помощью любого из следующих свойств:

-   Location (расположение)
-   Classification properties (свойства классификации)
-   Creation time (время создания)
-   Modification time (время изменения)
-   Last accessed time (время последнего доступа)

Задачи управления файлами также можно настраивать на оповещение владельцев файлов о любых будущих политиках, которые будут применены к их файлам.

> [!Note]
> Отдельные задачи управления файлами выполняются в соответствии с независимыми расписаниями.

<br />
Этот раздел включает следующие статьи:

-   [Создание задачи срока окончания действия файла](create-file-expiration-task.md)
-   [Создание задачи управления пользовательскими файлами](create-custom-file-management-task.md)

> [!Note]
> Чтобы настроить уведомления по электронной почте и определенные возможности создания отчетов, необходимо сначала настроить общие параметры диспетчера ресурсов файлового сервера.

## <a name="see-also"></a>См. также:

-   [Настройка параметров диспетчера ресурсов файлового сервера](setting-file-server-resource-manager-options.md)


