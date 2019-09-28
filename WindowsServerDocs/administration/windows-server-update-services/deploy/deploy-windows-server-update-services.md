---
title: Развертывание служб Windows Server Update Services
description: Раздел "Служба обновления Windows Server (WSUS)". Обзор процесса развертывания со ссылками на четыре шага для его выполнения
ms.prod: windows-server
ms.reviewer: na
ms.technology: manage-wsus
ms.topic: get-started-article
ms.assetid: 2708f6b2-4252-4b8f-9b7e-84c9b4222075
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e3e6bcd5f90d1a7df2a35dda45b4bf8951940815
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71361676"
---
# <a name="deploy-windows-server-update-services"></a>Развертывание служб Windows Server Update Services

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Службы Windows Server Update Services (WSUS) позволяют ИТ-администраторам развертывать новейшие обновления продуктов Майкрософт. WSUS — это роль сервера Windows Server, которая может быть установлена для управления и распространения обновлений. Сервер служб WSUS может быть источником обновлений для других серверов WSUS в организации. Сервер WSUS, действующий как источник обновлений, называется вышестоящим сервером.  

При реализации служб WSUS хотя бы один сервер служб WSUS в сети должен быть подключен к Центру обновления Майкрософт для получения информации о доступных обновлениях. Вы можете определить, на основе сетевой безопасности и конфигурации, сколько других серверов напрямую подключаются к Центр обновления Майкрософт.  

Это краткое описание содержит общие сведения о планировании и развертывании службы обновления Windows Server.  

-   [Планирование развертывания WSUS](../plan/plan-your-wsus-deployment.md)  

-   [Шаг 1. Установка роли сервера WSUS](1-install-the-wsus-server-role.md)  

-   [Шаг 2. Настройка служб WSUS](2-configure-wsus.md)  

-   [Шаг 3. Утверждение и развертывание обновлений в службах WSUS](3-approve-and-deploy-updates-in-wsus.md)  

-   [Шаг 4. Настройка параметров групповой политики для автоматического обновления](4-configure-group-policy-settings-for-automatic-updates.md)  
