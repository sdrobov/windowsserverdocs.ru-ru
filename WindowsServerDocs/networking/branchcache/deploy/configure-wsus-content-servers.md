---
title: Настройка серверов содержимого служб Windows Server Update Services (WSUS)
description: Эта статья является частью руководства по развертыванию BranchCache для Windows Server 2016, в котором демонстрируется развертывание службы BranchCache в распределенном и размещенном режимах кэша для оптимизации использования пропускной способности глобальной сети в филиалах.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 9724aa8d-e4ae-404c-bee6-cef1534cd3ca
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 0836c91948b13d2e6bac540294a55cb49523158d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71406421"
---
# <a name="configure-windows-server-update-services-wsus-content-servers"></a>Настройка серверов содержимого служб Windows Server Update Services (WSUS)

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

После установки компонента BranchCache и запуска службы BranchCache серверы WSUS должны быть настроены для хранения файлов обновления на локальном компьютере. 

При настройке серверов WSUS для хранения файлов обновления на локальном компьютере метаданные обновлений и файлы обновления загружаются и хранятся непосредственно на сервере WSUS. Это гарантирует получение клиентскими компьютерами службы BranchCache файлов обновления продуктов Майкрософт с сервера WSUS, а не непосредственно с веб-сайта Центр обновления Майкрософт.  
  
Дополнительные сведения о синхронизации WSUS см. в разделе [Настройка синхронизации обновлений](https://technet.microsoft.com/library/mt612311.aspx) .  