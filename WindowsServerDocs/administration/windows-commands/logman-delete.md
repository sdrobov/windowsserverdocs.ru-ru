---
title: logman delete
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f3b2422-3dce-4fb4-adbb-8536b1d7da2b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 00473b5178eca93e9644888fbaa4c4c96c0dd683
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842065"
---
# <a name="logman-delete"></a>logman delete

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаление существующего сборщика данных.  
  
## <a name="syntax"></a>Синтаксис  
```  
logman delete <[-n] <name>> [options]  
```  
## <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|/?|Отображение контекстной справки.|  
|-s <computer name>|Выполнение команды на удаленный компьютер.|  
|-config <value>|Указывает файл параметров, содержащий параметры команды.|  
|[-n]. <name>|Имя целевой сборщика данных.|  
|-ets|Отправьте команды сеансам трассировки событий напрямую без сохранения или планирования.|  
|-[-]u <user [password]>|Указывает пользователя для запуска от имени. Введя * для пароля выводит приглашение для ввода пароля. Пароль не отображается при вводе пароля.|  
## <a name="BKMK_examples"></a>Примеры  
Следующая команда удаляет perf_log сборщика данных.  
```  
logman delete perf_log  
```  
#### <a name="additional-references"></a>Дополнительные ссылки  
[Logman](logman.md)  
