---
title: WBADMIN остановка задания
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b83b398-39c7-4410-bf17-5c1fb1a4f46d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7a9e71fe2e4883c52c2418e21fc8764fd14e6c81
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889725"
---
# <a name="wbadmin-stop-job"></a>WBADMIN остановка задания



Отменяет операцию резервного копирования или восстановления, который выполняется в данный момент. Не удается перезапустить отмененных операций, необходимо повторно отмененной операции резервного копирования или восстановления с самого начала.

Для остановки операции резервного копирования или восстановления с помощью этой команды, необходимо быть членом **операторы архива** группы или **Администраторы** группа, или являться обладателем соответствующих делегированных полномочий. Кроме того, необходимо запустить **wbadmin** из командной строки с повышенными правами. (Чтобы открыть командную строку, щелкните правой кнопкой мыши **командной** и нажмите кнопку **Запуск от имени администратора**.)

## <a name="syntax"></a>Синтаксис

```
wbadmin stop job
[-quiet]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|-quiet|Запускает подкоманды без вывода сообщений для пользователя.|

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [WBADMIN](wbadmin.md)