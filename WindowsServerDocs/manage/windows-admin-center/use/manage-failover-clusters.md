---
title: Управление отказоустойчивыми кластерами с помощью Windows Admin Center
description: Управление отказоустойчивыми кластерами с помощью Windows Admin Center (проект Honolulu)
ms.technology: manage
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 06/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 63f5fca8e7ef63200e01cfc6e00a979e7f045b51
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9296676"
---
# Управление отказоустойчивыми кластерами с помощью Windows Admin Center

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

> [!Tip]
> Только начинаете знакомство с Windows Admin Center?
> [Узнайте дополнительные сведения о Windows Admin Center](../understand/windows-admin-center.md) или [скачайте платформу](https://aka.ms/windowsadmincenter).

## Для управления отказоустойчивыми кластерами
[Отказоустойчивая кластеризация](https://docs.microsoft.com/windows-server/failover-clustering/failover-clustering-overview) — это компонент Windows Server, которая позволяет сгруппировать несколько серверов в отказоустойчивом кластере для повышения доступности и масштабируемости приложений и служб, таких как масштабируемого файлового сервера, Hyper-V и Microsoft SQL Server.

Хотя вы можете управлять узлах кластера отдельных серверов, добавляя их в Windows Admin Center [подключений к серверу](manage-servers.md) , вы также можете добавить их как отказоустойчивых кластеров для просмотра и управления ресурсами кластера, хранилища, сети, узлы, ролей, виртуальный компьютеры и виртуальные коммутаторы.

![Обзор экрана отказоустойчивого кластера](../media/manage-failover-clusters/fcm-overview.png)

## Добавление отказоустойчивого кластера в Windows Admin Center
Чтобы добавить кластера Windows Admin Center:

1. Выберите вариант **+ Добавить** всех подключений.
2. При необходимости добавьте **Отработки отказа подключения**.
3. Введите имя кластера и, если появится запрос, учетные данные для использования.
4. У вас будет возможность добавлять узлы кластера в Windows Admin Center подключения отдельного сервера.
5. Нажмите кнопку **Отправить** до конца.

Кластер будет добавлен в список подключения на странице "Обзор". Щелкните его, чтобы подключиться к кластеру.

> [!NOTE]
> Вы также можете управлять гиперконвергентной кластеры, добавив кластера как [гиперконвергированном кластере подключения](manage-hyper-converged.md) в Windows Admin Center.

## Средства

Для подключения отказоустойчивого кластера доступны следующие инструменты:

| Инструмент | Описание |
| ---- | ----------- |
| Обзор | Просмотреть сведения о отказоустойчивого кластера и управления ресурсами кластера |
| Диски | Представление кластера общих томов и дисков |
| Сети | Просмотр сетей в кластере |
| Узлы | Просмотр и управление узлами кластера |
| Роли | Управление кластерных ролей или создать пустую роль |
| Обновления | Управление кластерное обновление (требуется [CredSSP](../understand/faq.md#does-windows-admin-center-use-credssp)) |
| [Виртуальные машины](manage-virtual-machines.md) | Просмотр и управление виртуальными машинами |
| Виртуальные коммутаторы | Просмотр и управление виртуальных коммутаторов |

## Несколько ближайших

Управление отказоустойчивым кластером в Windows Admin Center активно находится в стадии разработки и в ближайшем будущем будут добавлены новые функции. Вы можете просмотреть состояние и проголосовать за функции в UserVoice:

|Функция запроса|
|-------|
| [Более кластерными дисками информации](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/31740424--cluster-more-disk-info-in-failover-cluster-manag) |
| [Поддержка кластера дополнительные действия](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/33558076--fcm-full-csv-management-cycle-in-one-place) |
| [Поддержка стойке кластерах Hyper-V и масштабируемого файлового сервера в разных кластерах](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/31729741--cluster-support-for-converged-architecture) |
| [Кэш CSV-файла блокировки представления](https://windowsserver.uservoice.com/forums/295071-management-tools/suggestions/31669477--cluster-csv-block-cache) |
| [Просмотреть все или предложить новые функции](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5Bcluster%5D) |