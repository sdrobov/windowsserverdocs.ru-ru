---
title: Wbadmin отключить архивацию
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 405bbb3c07206032f1a9e3039c563e7c842e362e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362491"
---
# <a name="wbadmin-disable-backup"></a>Wbadmin отключить архивацию



Прекращает выполнение существующих запланированных ежедневных резервных копий.

Чтобы отключить запланированное ежедневное резервное копирование, необходимо быть членом группы " **Администраторы** ", либо вам должны быть делегированы соответствующие разрешения. Кроме того, необходимо запустить программу **Wbadmin** из командной строки с повышенными привилегиями. (Чтобы открыть командную строку с повышенными привилегиями, щелкните правой кнопкой мыши пункт **Командная строка** и выберите команду **Запуск от имени администратора**.)

## <a name="syntax"></a>Синтаксис

```
wbadmin disable backup
[-quiet]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-quiet|Выполняет подкоманду без запросов пользователю.|

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)