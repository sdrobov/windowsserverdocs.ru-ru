---
title: Wbadmin get Status
description: Команды Windows для Wbadmin get status, сообщающие о состоянии операции резервного копирования или восстановления, выполняемой в данный момент.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2911b944-7b95-46aa-8c1e-1d55a2fcc94c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f8ebf1a078632f78dc8d58c232550345f0de78f2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80829747"
---
# <a name="wbadmin-get-status"></a>Wbadmin get Status



Сообщает состояние операции резервного копирования или восстановления, которая выполняется в данный момент.

Чтобы использовать эту подкоманду, необходимо быть членом группы " **Операторы архива** " или " **Администраторы** ", либо вам должны быть делегированы соответствующие разрешения. Кроме того, необходимо запустить программу **Wbadmin** из командной строки с повышенными привилегиями. (Чтобы открыть командную строку с повышенными привилегиями, щелкните правой кнопкой мыши пункт **Командная строка**и выберите команду **Запуск от имени администратора**.)

## <a name="syntax"></a>Синтаксис

```
wbadmin get status
```

### <a name="parameters"></a>Параметры

Эта подкоманда не имеет параметров.

## <a name="remarks"></a>Примечания

-   Эта подкоманда не будет прерываться до завершения текущей операции резервного копирования или восстановления — подкоманда продолжит работу, даже если закрыть командное окно.
-   Если вы хотите прерывать текущую операцию резервного копирования или восстановления, используйте подкоманду **Wbadmin останавливают задание** .

## <a name="additional-references"></a>Дополнительные материалы

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   Командлет [Get-вбжоб](https://technet.microsoft.com/library/jj902426.aspx)