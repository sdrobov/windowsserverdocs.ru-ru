---
title: состояние WBADMIN get
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2911b944-7b95-46aa-8c1e-1d55a2fcc94c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 35fd640aa56bca7c5f5d6f3901fe095d0b8a73cc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863415"
---
# <a name="wbadmin-get-status"></a>состояние WBADMIN get



Сообщает о состоянии операции резервного копирования и восстановления, которая выполняется в данный момент.

По использованию этого, необходимо быть членом **операторы архива** группы или **Администраторы** группа, или должна была быть делегированы соответствующие разрешения. Кроме того, необходимо запустить **wbadmin** из командной строки с повышенными правами. (Чтобы открыть командную строку, щелкните правой кнопкой мыши **командной**, а затем нажмите кнопку **Запуск от имени администратора**.)

## <a name="syntax"></a>Синтаксис

```
wbadmin get status
```

## <a name="parameters"></a>Параметры

Подкоманды не имеет параметров.

## <a name="remarks"></a>Примечания

-   Подкоманды не помешает до текущего резервного копирования или восстановления операция завершена — подкоманды продолжат работать, даже если закройте командное окно.
-   Если вы хотите остановить текущей резервной копии или операции восстановления, используйте **wbadmin остановки задания** подкоманды.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [WBADMIN](wbadmin.md)
-   [Get-WBJob](https://technet.microsoft.com/library/jj902426.aspx) командлета