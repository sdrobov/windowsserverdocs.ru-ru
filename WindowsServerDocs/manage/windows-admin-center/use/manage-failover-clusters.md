---
title: Управления отказоустойчивыми кластерами с помощью Windows Admin Center
description: Управления отказоустойчивыми кластерами с помощью Windows Admin Center (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 06/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: f7e14581f7f6b14b0cf39308de236b68a07e8c9f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59824075"
---
# <a name="manage-failover-clusters-with-windows-admin-center"></a>Управления отказоустойчивыми кластерами с помощью Windows Admin Center

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

> [!Tip]
> Только начинаете знакомство с Windows Admin Center?
> [Узнайте дополнительные сведения о Windows Admin Center](../understand/windows-admin-center.md) или [скачайте платформу](https://aka.ms/windowsadmincenter).

## <a name="managing-failover-clusters"></a>Управлению отказоустойчивыми кластерами
[Отказоустойчивая кластеризация](https://docs.microsoft.com/windows-server/failover-clustering/failover-clustering-overview) — это функция Windows Server, которая позволяет сгруппировать несколько серверов в отказоустойчивый кластер для повышения доступности и масштабируемости приложений и служб, таких как Scale-Out File Server, Hyper-V и Microsoft SQL Server.

Хотя вы можете управлять узлами отказоустойчивого кластера в отдельных серверов, добавив их в виде [соединений с сервером](manage-servers.md) в Windows Admin Center, можно также добавить их как отказоустойчивые кластеры для просмотра и управления ресурсами кластера, хранилища, сети, узлы, роли, виртуальные машины и виртуальные коммутаторы.

![Экран обзора кластера отработки отказа](../media/manage-failover-clusters/fcm-overview.png)

## <a name="adding-a-failover-cluster-to-windows-admin-center"></a>Добавление отказоустойчивый кластер Windows Admin Center
Чтобы добавить кластер Windows Admin Center:

1. Нажмите кнопку **+ добавить** под все подключения.
2. Выберите добавление **отработки отказа подключения**.
3. Введите имя кластера и, если будет предложено, учетные данные, используемые.
4. Имеется параметр для добавления узлов кластера в Windows Admin Center подключения отдельного сервера.
5. Нажмите кнопку **отправить** до конца.

Кластера будут добавляться в список соединений на странице "Обзор". Щелкните его, чтобы подключиться к кластеру.

> [!NOTE]
> Вы также можете управлять гиперконвергентной clustered, добавив в кластер в качестве [подключение к кластеру Hyper-Converged](manage-hyper-converged.md) в Windows Admin Center.

## <a name="tools"></a>Инструменты

Для подключений к кластеру отработки отказа, доступны следующие средства:

| Инструмент | Описание |
| ---- | ----------- |
| Обзор | Просмотреть сведения об отработке отказа кластера и управление кластерными ресурсами |
| Диски | Просмотр кластера общих дисков и томов |
| Сети | Просмотр сетей в кластере |
| Узлы | Просмотр и управление узлами кластера |
| Роли | Управление ролями кластера или создать пустую роль |
| Обновления | Управление обновлениями с поддержкой кластера |
| [Виртуальные машины](manage-virtual-machines.md) | Просмотр и управление виртуальными машинами |
| Виртуальные коммутаторы | Просмотр и управление ими виртуальные коммутаторы |

## <a name="more-coming"></a>Дополнительные поступающих

Управление отказоустойчивыми кластерами в Windows Admin Center активно находится в стадии разработки и новые функции будут добавляться в ближайшем будущем. Можно просмотреть состояние и проголосовать за функции в UserVoice:

|Запрос функции|
|-------|
| [Показать более кластеризованный сведений о диске](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/31740424--cluster-more-disk-info-in-failover-cluster-manag) |
| [Действия для поддержки дополнительных кластера](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/33558076--fcm-full-csv-management-cycle-in-one-place) |
| [Поддерживает кластер под управлением Hyper-V и масштабируемого файлового сервера в разных кластерах](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/31729741--cluster-support-for-converged-architecture) |
| [Блочным кэшем CSV представления](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/31669477--cluster-csv-block-cache) |
| [Просмотреть все или предложить новые функции](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5Bcluster%5D) |