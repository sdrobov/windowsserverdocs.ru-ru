---
title: Настройка серверов содержимого служб Windows Server Update Services (WSUS)
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, который показывает, как развернуть BranchCache в режимах распределенный и размещенный кэш, чтобы оптимизировать использование пропускной способности глобальной сети в филиалах.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 9724aa8d-e4ae-404c-bee6-cef1534cd3ca
ms.author: pashort
author: shortpatti
ms.openlocfilehash: e8576282be92f02daf716da82ea75eddc755ee5c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59873845"
---
# <a name="configure-windows-server-update-services-wsus-content-servers"></a>Настройка серверов содержимого служб Windows Server Update Services (WSUS)

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

После установки компонента BranchCache и запуск службы BranchCache, серверы WSUS должны быть настроены так, чтобы хранить файлы обновлений на локальном компьютере. 

При настройке серверов WSUS, чтобы хранить файлы обновлений на локальном компьютере, метаданные и файлы обновления загружаются по и хранятся непосредственно на сервере WSUS. Это гарантирует, что клиентские компьютеры BranchCache получать файлы обновлений продуктов Майкрософт, с сервера WSUS, а не непосредственно с сайта Центра обновления Майкрософт.  
  
Дополнительные сведения о синхронизации WSUS, см. в разделе [Настройка синхронизации обновлений](https://technet.microsoft.com/library/mt612311.aspx)  