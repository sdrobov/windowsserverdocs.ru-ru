---
title: Настройка содержимого серверов Windows Server Update Services (WSUS)
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, которой показано, как развернуть BranchCache в режиме распределенного и размещенного кэша для оптимизации использования пропускной способности глобальной сети в филиалах.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 9724aa8d-e4ae-404c-bee6-cef1534cd3ca
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 8200a0905f7bc5c403288a22faece5f84eac8af9
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="configure-windows-server-update-services-wsus-content-servers"></a>Настройка содержимого серверов Windows Server Update Services (WSUS)

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

После установки компонента BranchCache и запускает службу BranchCache, серверы WSUS необходимо настроить для хранения файлов обновлений на локальном компьютере. 

При настройке серверов WSUS для хранения файлов обновлений на локальном компьютере, метаданные и файлы обновления для загрузки и хранятся непосредственно на сервере WSUS. Это гарантирует, что клиентских компьютеров BranchCache получает файлы обновлений продуктов Майкрософт, с сервера WSUS, а не непосредственно из сайта Центра обновления Майкрософт.  
  
Дополнительные сведения о синхронизации WSUS см. в разделе [Настройка синхронизации обновлений](https://technet.microsoft.com/en-us/library/mt612311.aspx)  