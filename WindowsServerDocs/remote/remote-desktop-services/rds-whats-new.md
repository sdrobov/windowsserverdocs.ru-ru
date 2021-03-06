---
title: Что нового в службах удаленных рабочих столов?
description: Содержит описание новых возможностей служб удаленных рабочих столов (RDS)в Windows Server 2016.
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.author: chrimo
ms.date: 10/11/2016
ms.topic: article
ms.assetid: 04d52dff-e61b-4633-9908-be8600abc2ba
author: ChristianMontoya
manager: scottman
ms.openlocfilehash: 43c280996334ea3b371c54f86b1cd4f86072124b
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86963316"
---
# <a name="whats-new-in-remote-desktop-services"></a>Что нового в службах удаленных рабочих столов?

Службы удаленных рабочих столов (RDS) на основе Windows Server 2016 — это платформа виртуализации, которая предоставляет широкий спектр сценариев клиентов. Улучшения в общем решении RDS включает работы, выполненные командой удаленного рабочего стола и другими партнерами по разработке технологий в корпорации Майкрософт. Следующие сценарии и технологии в Windows Server 2016 являются обновленными или улучшенными.

Также обязательно ознакомьтесь с нашим сеансом на конференции Ignite 2016. [Использование улучшенных возможностей RDS в Windows Server 2016](https://channel9.msdn.com/Events/Ignite/2016/BRK3098). В этом видео группы разработки продукта рассматривает все новые и улучшенные возможности служб удаленных рабочих столов, включая поддержку vGPU. 

## <a name="app-compatibility---windows-server-2016-and-windows-10"></a>Совместимость приложений — Windows Server 2016 и Windows 10
Основанная на той же платформе Windows 10, Windows Server 2016 имеет не только аналогичное оформление и предоставляет то, что вы ожидаете от рабочего стола, но также может запускать многие из тех же приложений. Связывание Windows Server 2016 с графическими возможностями (ниже) обеспечивает среду для продуктивной работы всех пользователей. 

## <a name="azure-sql-database---the-new-database-for-your-highly-available-environment"></a>База данных SQL Azure — новая база данных для вашей среды высокой доступности
Посредник подключений к удаленному рабочему столу имеет возможность сохранять сведения о развертывании (например, состояния подключения и сопоставления пользователя/узла) в общую базу данных SQL, на подобии базы данных Azure SQL. Откажитесь от руководства по развертыванию постоянно доступных групп SQL Server, скачайте строку подключения к базе данных SQL Azure и начните использовать среду высокой доступности.

Дополнительные сведения: [Использование базы данных SQL Azure для среды высокого доступа посредника подключений к удаленному рабочему столу](https://techcommunity.microsoft.com/t5/microsoft-security-and/new-windows-server-2016-capability-use-azure-sql-db-for-your/ba-p/249787)

## <a name="graphics---solving-graphics-needs-across-various-scenarios"></a>Графика — предоставление необходимой графики для различных сценариев
Благодаря дискретному назначению устройств в Hyper-V, теперь вы сможете выполнить сопоставление графических процессоров на хост-компьютере напрямую с виртуальной машины, которая будет использоваться приложениями, требующими графического процессора. Улучшения также были предприняты в vGPU RemoteFX, включая поддержку OpenGL 4.4, OpenCL 1.1, разрешения 4k и виртуальных машин Windows Server.

Дополнительные сведения: [Дискретное назначение устройств](https://techcommunity.microsoft.com/t5/virtualization/bg-p/Virtualization)

## <a name="rd-connection-broker---improved-connection-handling-during-logon-storms"></a>Посредник подключений к удаленному рабочему столу — улучшенная обработка подключения во время "штурмов входа"
Благодаря улучшенной обработке подключения, посредник подключений к удаленному рабочему столу теперь может обрабатывать больше 10 000 текущих запросов на вход, которые иногда можно увидеть во время так именуемых "штурмов входа". Улучшенный посредник подключений к удаленному рабочему столу также упрощает обслуживание развертывания, предоставляя возможность более быстрого повторного добавления серверов в среду.

Дополнительные сведения: [Улучшенная производительность службы посредника подключений к удаленному рабочему столу ](https://techcommunity.microsoft.com/t5/microsoft-security-and/improved-remote-desktop-connection-broker-performance-with/ba-p/249559)

## <a name="rdp-10---new-capabilities-built-into-the-protocol"></a>RDP 10 — новые возможности, встроенные в протокол
RDP 10 использует кодек H.264/AVC 444, который соответствующим образом оптимизирует как видео, так и текст. В этом выпуске также поддерживается удаленное взаимодействие с помощью пера. Благодаря этим возможностям, ваши удаленные сеансы будут больше походить на локальный сеанс.  

Дополнительные сведения: [Улучшения кодеков RDP 10 AVC/H.264 в Windows 10 и Windows Server 2016](https://techcommunity.microsoft.com/t5/microsoft-security-and/remote-desktop-protocol-rdp-10-avc-h-264-improvements-in-windows/ba-p/249588)

## <a name="personal-session-desktops---providing-individual-desktops-to-any-end-user"></a>Рабочие столы на базе личных сеансов предоставляют индивидуальные рабочие столы для каждого пользователя
Рабочие столы на базе личных сеансов —новый способ иметь свой личный рабочий стол, размещенный в облаке. Права администратора и выделенные хосты сеансов устраняют сложность сред хостинга, где пользователи хотят управлять рабочим столом, как своим собственным.

Дополнительные сведения: [Рабочие столы на базе личных сеансов](rds-personal-session-desktops.md)
