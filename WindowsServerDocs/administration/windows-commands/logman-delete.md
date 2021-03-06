---
title: logman delete
description: Справочная статья по команде Logman DELETE, которая удаляет существующий сборщик данных.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8f3b2422-3dce-4fb4-adbb-8536b1d7da2b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 505cd8a09bcbb1e46f16242818825f3c504955b9
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85930426"
---
# <a name="logman-delete"></a>logman delete

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет существующий сборщик данных.

## <a name="syntax"></a>Синтаксис

```
logman delete <[-n] <name>> [options]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| -s`<computer name>` | Выполняет команду на указанном удаленном компьютере. |
| -config`<value>` | Указывает файл параметров, содержащий параметры команды. |
| [-n]`<name>` | Имя целевого объекта. |
| -ETS | Отправляет команды в сеансы трассировки событий напрямую без сохранения или планирования. |
| -[-] u`<user [password]>` | Указывает пользователя для запуска от имени. При вводе \* для пароля выводится запрос на ввод пароля. Пароль не отображается при вводе. |
| /? | Отображает контекстную справку. |

### <a name="examples"></a>Примеры

Чтобы удалить *perf_log*сборщика данных, введите:

```
logman delete perf_log
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [команда logman](logman.md)
