---
title: "Настройка пространств имен DFS"
description: "В этой статье рассматривается, как проводить тонкую настройку или оптимизацию пространств имен DFS."
ms.date: 6/5/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 4614441fc54913ba5a8b547bbf1ad3e8ce7ee69b
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="tuning-dfs-namespaces"></a>Настройка пространств имен DFS

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008

После создания пространства имен и добавления папок и конечных объектов обратитесь к следующим разделам, чтобы настроить или оптимизировать то, как пространство имен DFS обрабатывает ссылки и опрашивает доменные службы Active Directory (AD DS) для получения актуальных данных пространства имен:

-   [Включение перечисления на основе доступа для пространства имен](enable-access-based-enumeration-on-a-namespace.md)
-   [Включение и отключение ссылок и переключение клиента на основной ресурс](enable-or-disable-referrals-and-client-failback.md)
-   [Изменение периода кэширования ссылок клиентами](change-the-amount-of-time-that-clients-cache-referrals.md)
-   [Задание метода сортировки конечных объектов в ссылках](set-the-ordering-method-for-targets-in-referrals.md)
-   [Задание приоритета конечных объектов для переопределения порядка в ссылках](set-target-priority-to-override-referral-ordering.md)
-   [Оптимизация опроса пространства имен](optimize-namespace-polling.md)
-   [Использование унаследованных разрешений с перечислением на основе доступа](using-inherited-permissions-with-access-based-enumeration.md)

> [!NOTE]
> Для поиска папок или конечных объектов папок выберите пространство имен, перейдите на вкладку **Поиск**, введите строку поиска в текстовом поле и нажмите кнопку **Поиск**.