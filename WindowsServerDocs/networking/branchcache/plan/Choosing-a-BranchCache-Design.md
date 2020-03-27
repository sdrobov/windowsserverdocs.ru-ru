---
title: Выбор схемы BranchCache
description: Эта статья является частью руководства по развертыванию BranchCache для Windows Server 2016, в котором показано, как развернуть BranchCache в распределенном и размещенном режимах кэша для оптимизации использования пропускной способности глобальной сети в филиалах.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 86c1ccad-2aa4-40fe-84c1-f77c49eb1216
ms.author: lizross
author: eross-msft
ms.openlocfilehash: ca605589d28811f96296f2ff865e8ae6923304c3
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80319115"
---
# <a name="choosing-a-branchcache-design"></a>Выбор схемы BranchCache

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела можно узнать о режимах BranchCache и выбрать оптимальные режимы развертывания.  
  
Это руководством можно использовать для развертывания BranchCache в следующих режимах и сочетаниях режимов.  
  
-   Все офисы филиалов настроены для режима распределенного кэша.  
  
-   Все офисы филиалов настроены для режима размещенного кэша и имеют сервер размещенного кэша на сайте.  
  
-   Некоторые офисы филиалов настроены для режима распределенного кэша, а некоторые офисы филиалов имеют сервер кэширования на сайте и настроены для режима размещенного кэша.  
  
На следующем рисунке показана установка в двойном режиме с одним офисом филиала, настроенным для режима распределенного кэша, и одним филиалом, настроенным для режима размещенного кэша.  
  
![Выбор схемы BranchCache](../../media/Choosing-a-BranchCache-Design/bc_new_modes.jpg)  
  
Перед развертыванием BranchCache выберите предпочтительный режим для каждого офиса филиала в Организации.  
  


