---
title: wbadmin get status
description: Справочная статья для Wbadmin get status, которая сообщает о состоянии операции резервного копирования или восстановления, выполняемой в данный момент.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2911b944-7b95-46aa-8c1e-1d55a2fcc94c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a9a2a71ed8477722b32b06f37c88b373d6889568
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86954626"
---
# <a name="wbadmin-get-status"></a>wbadmin get status



Сообщает состояние операции резервного копирования или восстановления, которая выполняется в данный момент.

Чтобы использовать эту подкоманду, необходимо быть членом группы " **Операторы архива** " или " **Администраторы** ", либо вам должны быть делегированы соответствующие разрешения. Кроме того, необходимо запустить программу **Wbadmin** из командной строки с повышенными привилегиями. (Чтобы открыть командную строку с повышенными привилегиями, щелкните правой кнопкой мыши пункт **Командная строка**и выберите команду **Запуск от имени администратора**.)

## <a name="syntax"></a>Синтаксис

```
wbadmin get status
```

### <a name="parameters"></a>Параметры

Эта подкоманда не имеет параметров.

## <a name="remarks"></a>Комментарии

-   Эта подкоманда не будет прерываться до завершения текущей операции резервного копирования или восстановления — подкоманда продолжит работу, даже если закрыть командное окно.
-   Если вы хотите прерывать текущую операцию резервного копирования или восстановления, используйте подкоманду **Wbadmin останавливают задание** .

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   Командлет [Get-вбжоб](/powershell/module/windowserverbackup/?view=winserver2012r2-ps)
