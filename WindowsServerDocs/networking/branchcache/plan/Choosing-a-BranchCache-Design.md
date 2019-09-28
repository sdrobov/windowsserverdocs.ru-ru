---
title: Выбор схемы BranchCache
description: Эта статья является частью руководства по развертыванию BranchCache для Windows Server 2016, в котором показано, как развернуть BranchCache в распределенном и размещенном режимах кэша для оптимизации использования пропускной способности глобальной сети в филиалах.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 86c1ccad-2aa4-40fe-84c1-f77c49eb1216
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 2a1b4615dfda3989f0321725fd27da066fcb8a5e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71406317"
---
# <a name="choosing-a-branchcache-design"></a>Выбор схемы BranchCache

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела можно узнать о режимах BranchCache и выбрать оптимальные режимы развертывания.  
  
Это руководством можно использовать для развертывания BranchCache в следующих режимах и сочетаниях режимов.  
  
-   Все офисы филиалов настроены для режима распределенного кэша.  
  
-   Все офисы филиалов настроены для режима размещенного кэша и имеют сервер размещенного кэша на сайте.  
  
-   Некоторые офисы филиалов настроены для режима распределенного кэша, а некоторые офисы филиалов имеют сервер кэширования на сайте и настроены для режима размещенного кэша.  
  
На следующем рисунке показана установка в двойном режиме с одним офисом филиала, настроенным для режима распределенного кэша, и одним филиалом, настроенным для режима размещенного кэша.  
  
![Выбор схемы BranchCache](../../media/Choosing-a-BranchCache-Design/bc_new_modes.jpg)  
  
Перед развертыванием BranchCache выберите предпочтительный режим для каждого офиса филиала в Организации.  
  


