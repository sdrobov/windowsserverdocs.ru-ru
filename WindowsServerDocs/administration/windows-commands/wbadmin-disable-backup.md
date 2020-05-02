---
title: Wbadmin отключить архивацию
description: Справочный раздел по параметру wbadmin disable backup, который прекращает выполнение запланированных ежедневных резервных копий.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5176cbd9-0696-4b3f-9c35-272dd84f7898
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b38460b5b8408d73c857cf7314805f33adfa3108
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720195"
---
# <a name="wbadmin-disable-backup"></a>Wbadmin отключить архивацию



Прекращает выполнение существующих запланированных ежедневных резервных копий.

Чтобы отключить запланированное ежедневное резервное копирование, необходимо быть членом группы " **Администраторы** ", либо вам должны быть делегированы соответствующие разрешения. Кроме того, необходимо запустить программу **Wbadmin** из командной строки с повышенными привилегиями. (Чтобы открыть командную строку с повышенными привилегиями, щелкните правой кнопкой мыши пункт **Командная строка** и выберите команду **Запуск от имени администратора**.)

## <a name="syntax"></a>Синтаксис

```
wbadmin disable backup
[-quiet]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-quiet|Выполняет подкоманду без запросов пользователю.|

## <a name="additional-references"></a>Дополнительные ссылки

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)