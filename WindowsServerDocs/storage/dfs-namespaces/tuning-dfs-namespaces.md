---
title: Настройка пространств имен DFS
description: В этой статье рассматривается, как проводить тонкую настройку или оптимизацию пространств имен DFS.
ms.date: 6/5/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: c11bbf65c3baebebe1e5143a5e694ca752500aca
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59844635"
---
# <a name="tuning-dfs-namespaces"></a>Настройка пространств имен DFS

> Относится к: Windows Server 2019, Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

После создания пространства имен и добавления папок и целевых объектов, обратитесь к следующим разделам, чтобы настроить или оптимизировать способ пространств имен DFS дескрипторы ссылок и опросов доменных служб Active Directory (AD DS) для обновленных данных пространства имен:

-   [Включить перечисление на основе доступа в пространстве имен](enable-access-based-enumeration-on-a-namespace.md)
-   [Включение и отключение ссылок и восстановление размещения клиента](enable-or-disable-referrals-and-client-failback.md)
-   [Изменить количество времени, которого клиенты кэшируют ссылки](change-the-amount-of-time-that-clients-cache-referrals.md)
-   [Выбор метода упорядочения конечных объектов в ссылках](set-the-ordering-method-for-targets-in-referrals.md)
-   [Установка приоритета переопределить сортировку ссылок](set-target-priority-to-override-referral-ordering.md)
-   [Оптимизация опроса пространства имен](optimize-namespace-polling.md)
-   [Использование наследуемых разрешений с перечислением на основе доступа](using-inherited-permissions-with-access-based-enumeration.md)

> [!NOTE]
> Для поиска папок или конечных объектов папок выберите пространство имен, перейдите на вкладку **Поиск**, введите строку поиска в текстовом поле и нажмите кнопку **Поиск**.