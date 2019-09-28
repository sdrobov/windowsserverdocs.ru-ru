---
title: Wbadmin get Status
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 0270a29e557ec135301753dd66c1f5f2404a8acc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362390"
---
# <a name="wbadmin-get-status"></a>Wbadmin get Status



Сообщает состояние операции резервного копирования или восстановления, которая выполняется в данный момент.

Чтобы использовать эту подкоманду, необходимо быть членом группы " **Операторы архива** " или " **Администраторы** ", либо вам должны быть делегированы соответствующие разрешения. Кроме того, необходимо запустить программу **Wbadmin** из командной строки с повышенными привилегиями. (Чтобы открыть командную строку с повышенными привилегиями, щелкните правой кнопкой мыши пункт **Командная строка**и выберите команду **Запуск от имени администратора**.)

## <a name="syntax"></a>Синтаксис

```
wbadmin get status
```

## <a name="parameters"></a>Параметры

Эта подкоманда не имеет параметров.

## <a name="remarks"></a>Примечания

-   Эта подкоманда не будет прерываться до завершения текущей операции резервного копирования или восстановления — подкоманда продолжит работу, даже если закрыть командное окно.
-   Если вы хотите прерывать текущую операцию резервного копирования или восстановления, используйте подкоманду **Wbadmin останавливают задание** .

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   Командлет [Get-вбжоб](https://technet.microsoft.com/library/jj902426.aspx)