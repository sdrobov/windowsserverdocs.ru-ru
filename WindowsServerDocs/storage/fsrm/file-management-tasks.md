---
title: Задачи управления файлами
description: В этой статье описывается процесс автоматизации задач управления файлами
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 257ee2955c4f521d14f01ec197fd45e5194eef02
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71394100"
---
# <a name="file-management-tasks"></a>Задачи управления файлами

> Относится к: Windows Server 2019, Windows Server 2016, Windows Server (половина ежегодного канала), Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Задачи управления файлами автоматизируют процессы поиска наборов файлов на сервере и применения простых команд. Можно запланировать периодическое выполнение этих задач с целью сокращения повторяющихся расходов. Файлы, которые будут обрабатываться задачей управления файлами, можно определять с помощью любого из следующих свойств:

-   Location
-   Classification properties (свойства классификации)
-   Creation time (время создания)
-   Modification time (время изменения)
-   Last accessed time (время последнего доступа)

Задачи управления файлами также можно настраивать на оповещение владельцев файлов о любых будущих политиках, которые будут применены к их файлам.

> [!Note]
> Отдельные задачи управления файлами выполняются в соответствии с независимыми расписаниями.

<br />
Этот раздел содержит следующие темы:

-   [Создание задачи срока окончания действия файла](create-file-expiration-task.md)
-   [Создание задачи управления пользовательскими файлами](create-custom-file-management-task.md)

> [!Note]
> Чтобы настроить уведомления по электронной почте и определенные возможности создания отчетов, необходимо сначала настроить общие параметры диспетчера ресурсов файлового сервера.

## <a name="see-also"></a>См. также

-   [Настройка параметров диспетчера ресурсов файлового сервера](setting-file-server-resource-manager-options.md)


