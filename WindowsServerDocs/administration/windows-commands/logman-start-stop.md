---
title: Logman start | остановить
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a40006a1-876e-474b-aaf1-f365c730deea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 47d5bda20c79ac069c8c51e51535de49b5ca380d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821895"
---
# <a name="logman-start--stop"></a>Logman start | остановить

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

запустить сборщик данных и ручная установка времени начала или остановить сборщика данных задайте и ручная установка времени окончания.  
  
## <a name="syntax"></a>Синтаксис  
```  
logman start <[-n] <name>> [options]  
logman stop <[-n] <name>> [options]  
```  
## <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|-?|Отображение контекстной справки.|  
|-s <computer name>|Выполнение команды на удаленный компьютер.|  
|-config <value>|Указывает файл параметров, содержащий параметры команды.|  
|[-n]. <name>|Имя целевого объекта.|  
|-ets|Отправьте команды сеансам трассировки событий напрямую без сохранения или планирования.|  
|-как|Асинхронно выполните запрошенную операцию.|  
## <a name="BKMK_examples"></a>Примеры  
Следующая команда запускает perf_log сборщик данных на удаленном компьютере server_1.  
```  
logman start perf_log -s server_1  
```  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Logman](logman.md)  
