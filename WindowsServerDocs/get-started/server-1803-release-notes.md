---
title: Заметки о выпуске — важные проблемы в Windows Server версии 1803
description: Дополнительные сведения об известных проблемах, ограничения или другие сведения, необходимые перед установкой Windows Server версии 1803
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.date: 05/07/2018
ms.technology: server-general
ms.tgt_pltfrm: na
ms.topic: article
author: lizap
ms.author: elizapo
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: e9bd860769ec375a6d89ac452e3430b791fff3ad
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868505"
---
# <a name="release-notes-important-issues-in-windows-server-version-1803"></a>Заметки о выпуске: Важные проблемы в Windows Server версии 1803

>Область применения. Windows Server Semi-Annual Channel

Эти заметки о выпуске суммировать самые важные проблемы в операционной системе Windows Server, включая информацию о способах устранения или обхода проблемы. Чтобы узнать о новых возможностях в этом выпуске, см. в разделе [новые возможности в Windows Server версии ниже 1803](whats-new-in-windows-server-1803.md). Ознакомьтесь с [контейнеры Windows о](https://docs.microsoft.com/virtualization/windowscontainers/about/) тем, кто заинтересован в под управлением Windows Server, версии 1803, контейнер. 

Если не указано обратное, эти заметки распространяются на все выпуски и варианты установки Windows Server версии 1803.  

Мы постоянно обновлять эту статью. В случае обнаружения известных проблем, мы будем их здесь описать. 


## <a name="software-defined-datacenter"></a>Программно определяемого центра обработки данных

Функции программно определяемого центра обработки данных, такие как дисковые пространства, программно конфигурируемой сети и экранированных виртуальных машин не включены в Windows Server версии 1803. Как описано в разделе [обновления Windows Server Semi-Annual Channel](https://cloudblogs.microsoft.com/windowsserver/2018/03/29/windows-server-semi-annual-channel-update/), Windows Server полугодовой канал предназначен для контейнеров и сценариев приложений, которые выигрывают от ускорит внедрение инноваций. 

Если вам нужна инфраструктурные роли, используйте выпуск Long-Term Servicing Channel: Windows Server 2016 (доступен) или [Windows Server 2019](https://cloudblogs.microsoft.com/windowsserver/2018/03/20/introducing-windows-server-2019-now-available-in-preview) (ожидается в этом году).

Мы стремимся к созданию лучшей платформой для гиперконвергентной инфраструктуры, и мы продолжим для разработки новых компонентов и улучшения существующих на основе ваших отзывов. Благодарим вас за помощь в [более 10 000 кластеров дисковых](https://blogs.technet.microsoft.com/filecab/2018/03/27/storage-spaces-direct-momentum)! Мы будем рады общий доступ к более позднее в этом году.