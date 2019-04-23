---
title: Развертывание служб Windows Server Update Services
description: Раздел службы Windows Server Update Service (WSUS) — Обзор процесса развертывания со ссылками на четыре шага для ее выполнения
ms.prod: windows-server-threshold
ms.reviewer: na
ms.technology: manage-wsus
ms.topic: get-started-article
ms.assetid: 2708f6b2-4252-4b8f-9b7e-84c9b4222075
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 51972ad352f6530c8ee2aa84aec57b62784da728
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873185"
---
# <a name="deploy-windows-server-update-services"></a>Развертывание служб Windows Server Update Services

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Службы Windows Server Update Services (WSUS) позволяют ИТ-администраторам развертывать новейшие обновления продуктов Майкрософт. WSUS — это роль сервера Windows Server, который может быть установлен для распространения обновлений и управление ими. Сервер служб WSUS может быть источником обновлений для других серверов WSUS в организации. Сервер WSUS, действующий как источник обновлений, называется вышестоящим сервером.  

При реализации служб WSUS хотя бы один сервер служб WSUS в сети должен быть подключен к Центру обновления Майкрософт для получения информации о доступных обновлениях. Можно определить, на основе сетевой безопасности и конфигурации, сколько других серверов, на которое имеется подключение непосредственно к центру обновления Майкрософт.  

В этом руководстве содержатся сведения по планированию и развертыванию службы Центра обновления Windows Server.  

-   [Планирование развертывания WSUS](../plan/plan-your-wsus-deployment.md)  

-   [Шаг 1. Установка роли сервера WSUS](1-install-the-wsus-server-role.md)  

-   [Шаг 2. Настройка служб WSUS](2-configure-wsus.md)  

-   [Шаг 3. Утверждение и развертывание обновлений в WSUS](3-approve-and-deploy-updates-in-wsus.md)  

-   [Шаг 4. Настройка параметров групповой политики для автоматического обновления](4-configure-group-policy-settings-for-automatic-updates.md)  
