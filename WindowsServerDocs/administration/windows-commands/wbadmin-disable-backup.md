---
title: Отключите WBADMIN резервное копирование
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5176cbd9-0696-4b3f-9c35-272dd84f7898
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3fcaf9e8b6ef052b01b5a3184dd8f94bba433cd7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821795"
---
# <a name="wbadmin-disable-backup"></a>Отключите WBADMIN резервное копирование



Останавливает существующих запланированное ежедневное резервное копирование.

Чтобы отключить запланированное ежедневное резервное копирование, необходимо быть членом **Администраторы** группа, или должна была быть делегированы соответствующие разрешения. Кроме того, необходимо запустить **wbadmin** из командной строки с повышенными правами. (Чтобы открыть командную строку, щелкните правой кнопкой мыши **командной** и нажмите кнопку **Запуск от имени администратора**.)

## <a name="syntax"></a>Синтаксис

```
wbadmin disable backup
[-quiet]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-quiet|Запускает подкоманды без вывода сообщений для пользователя.|

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [WBADMIN](wbadmin.md)