---
title: nlbmgr
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 89cb8590-b7cf-4a27-89fa-0fa62ea1a1ca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9ed11e702aeae66458f888e454c1bc1d1bc22630
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59887085"
---
# <a name="nlbmgr"></a>nlbmgr

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

С помощью диспетчера балансировки сетевой нагрузки, можно настроить и управлять кластеров балансировки сетевой нагрузки и все узлы кластера с одного компьютера, и вы можете реплицировать конфигурацию кластера на другие узлы. Диспетчер балансировки сетевой нагрузки можно запустить из командной строки с помощью команды **nlbmgr.exe**, который устанавливается на **systemroot\System32** папки.
## <a name="syntax"></a>Синтаксис
```
nlbmgr [/help] [/noping] [/hostlist <filename>] [/autorefresh <interval>]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/help|Отображение справки в командной строке.|
|/ noping|Запрещает проверку связи узлов до попытки связаться с ними через инструментарий управления Windows (WMI) диспетчер балансировки сетевой нагрузки. Используйте этот параметр, если вы отключили сообщений протокола ICMP (Internet Control) на всех доступных сетевых адаптеров. Диспетчер балансировки сетевой нагрузки обращаться к узлу, который недоступен, если при использовании этого параметра столкнется с задержкой.|
|/ hostlist <filename>|Загружает узел, указанный в filename в диспетчер балансировки сетевой нагрузки.|
|/autorefresh <interval>|Заставляет диспетчер балансировки сетевой нагрузки для обновления его узлов и кластера сведения о каждом <interval> секунд. Если интервал не указан, данные обновляются каждые 60 секунд.|
|/?|Отображение справки в командной строке.|
## <a name="additional-references"></a>Дополнительные ссылки
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)

