---
title: Управление — приостановка BDE
description: Справочная статья по команде Manage-bde Pause, которая приостанавливает шифрование или расшифровку BitLocker.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: efda0e08-b9ff-4e71-83d8-bb666b3032bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 244d18ff9763ccb12c9567fbab68e2fd72f0f076
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935468"
---
# <a name="manage-bde-pause"></a>Управление — приостановка BDE

Приостанавливает шифрование или расшифровку BitLocker.

## <a name="syntax"></a>Синтаксис

```
manage-bde -pause [<volume>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<volume>` | Указывает букву диска, за которой следует двоеточие, путь GUID тома или подключенный том. |
| -ComputerName | Указывает, что manage-bde.exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды. |
| `<name>` | Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера. |
| -? или/? | Отображает краткую справку в командной строке. |
| -Help или-h | Отображает полную справку в командной строке. |

### <a name="examples"></a>Примеры

Чтобы приостановить шифрование BitLocker на диске C, введите:

```
manage-bde pause C:
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Manage-bde в команде](manage-bde-on.md)

- [Команда управления-BDE Off](manage-bde-off.md)

- [Команда управления-bde resume](manage-bde-resume.md)

- [Команда Manage-bde](manage-bde.md)
