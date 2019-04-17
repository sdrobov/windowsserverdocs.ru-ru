---
title: Выбор схемы BranchCache
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, которой показано, как развернуть BranchCache в режиме распределенного и размещенного кэша для оптимизации использования пропускной способности глобальной сети в филиалах
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 86c1ccad-2aa4-40fe-84c1-f77c49eb1216
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 4fe40b3d9ece771a46af8ecc70297b8713d65875
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="choosing-a-branchcache-design"></a>Выбор схемы BranchCache

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать сведения о режимах BranchCache и выберите наиболее режимы для развертывания.  
  
Можно использовать это руководство по развертыванию BranchCache в режиме сочетаниях и следующие режимы.  
  
-   Все офисы филиалов, настраиваются для режима распределенного кэша.  
  
-   Все филиалах настроен режим размещенного кэша и у сервера размещенного кэша на сайте.  
  
-   Некоторых филиалах настраиваются для режима распределенного кэша и некоторых филиалах на сервере размещенного кэша на сайте а настроен режим размещенного кэша.  
  
На рисунке ниже показаны две режим установки, с одного офиса, настроены для использования режима распределенного кэша и одном филиале настроен режим размещенного кэша.  
  
![Выбор схемы BranchCache](../../media/Choosing-a-BranchCache-Design/bc_new_modes.jpg)  
  
Прежде чем развернуть BranchCache, выберите режим, который вы предпочитаете для каждого филиала компании в вашей организации.  
  


