---
title: Выбор схемы BranchCache
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, который показывает, как развернуть BranchCache в режимах распределенный и размещенный кэш, чтобы оптимизировать использование пропускной способности глобальной сети в филиалах
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 86c1ccad-2aa4-40fe-84c1-f77c49eb1216
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 330dcbee26f52ff69cd85ef8dc78d2e161b943d1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59811915"
---
# <a name="choosing-a-branchcache-design"></a>Выбор схемы BranchCache

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Дополнительные сведения о режимах BranchCache и выбрать лучший режимы развертывания можно использовать в этом разделе.  
  
В этом руководстве можно использовать для развертывания BranchCache в следующих режимах и режиме сочетания.  
  
-   Все офисы которых настроен режим распределенного кэша.  
  
-   Все офисы которых настроен режим размещенного кэша и иметь на сайте сервера размещенного кэша.  
  
-   Некоторых филиалах которых настроен режим распределенного кэша и некоторых филиалах нет сервера размещенного кэша на сайте и настроены на режим размещенного кэша.  
  
На следующем рисунке показана двойного режима в случае установки с помощью одного офиса, работающем в режиме распределенного кэша и одном филиале, работающем в режиме размещенного кэша.  
  
![Выбор схемы BranchCache](../../media/Choosing-a-BranchCache-Design/bc_new_modes.jpg)  
  
Перед развертыванием BranchCache, выберите режим предпочтительный для каждого филиала в вашей организации.  
  


