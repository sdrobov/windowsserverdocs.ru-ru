---
title: Настройка пространств имен DFS
description: В этой статье рассматривается, как проводить тонкую настройку или оптимизацию пространств имен DFS.
ms.date: 6/5/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 011512deaeb99ded7d0bfc32a48f19ab3b622475
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386152"
---
# <a name="tuning-dfs-namespaces"></a>Настройка пространств имен DFS

> Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

После создания пространства имен и добавления папок и целевых объектов ознакомьтесь со следующими разделами, чтобы настроить или оптимизировать способ, которым пространство имен DFS обрабатывает ссылки и опросы домен Active Directory Services (AD DS) для обновленных данных пространства имен.

-   [Включение перечисления на основе доступа в пространстве имен](enable-access-based-enumeration-on-a-namespace.md)
-   [Включение и отключение ссылок и восстановление размещения клиента](enable-or-disable-referrals-and-client-failback.md)
-   [Изменение времени, в течение которого клиенты кэшируют ссылки](change-the-amount-of-time-that-clients-cache-referrals.md)
-   [Задание метода сортировки конечных объектов в ссылках](set-the-ordering-method-for-targets-in-referrals.md)
-   [Задание приоритета конечных объектов для переопределения порядка в ссылках](set-target-priority-to-override-referral-ordering.md)
-   [Оптимизация опроса пространства имен](optimize-namespace-polling.md)
-   [Использование наследуемых разрешений с перечислением на основе доступа](using-inherited-permissions-with-access-based-enumeration.md)

> [!NOTE]
> Для поиска папок или конечных объектов папок выберите пространство имен, перейдите на вкладку **Поиск**, введите строку поиска в текстовом поле и нажмите кнопку **Поиск**.