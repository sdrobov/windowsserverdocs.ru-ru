---
title: bootcfg timeout
description: Справочный раздел по команде bootcfg timeout, который изменяет значение времени ожидания операционной системы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aa858eac-2bb7-4a27-a9bc-3e4a6eb8b2c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e10ccab69ca58a6cef260546e965f90eecfc8beb
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82708946"
---
# <a name="bootcfg-timeout"></a>bootcfg timeout

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет значение времени ожидания операционной системы.

## <a name="syntax"></a>Синтаксис

```
bootcfg /timeout <timeoutvalue> [/s <computer> [/u <domain>\<user> /p <password>]]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `/timeout <timeoutvalue>` | Задает значение времени ожидания в разделе [boot loader]. `<timeoutvalue>` Число секунд, в течение которых пользователь должен выбрать операционную систему на экране загрузчика, прежде чем NTLDR загрузит значение по умолчанию. Допустимый диапазон для `<timeoutvalue>` — 0-999. Если значение равно 0, NTLDR сразу запускает операционную систему по умолчанию без отображения экрана загрузчика загрузки. |
| `/s <computer>` | Указывает имя или IP-адрес удаленного компьютера (не используйте обратную косую черту). По умолчанию используется локальный компьютер. |
| `/u <domain>\<user>`  | Выполняет команду с разрешениями учетной записи пользователя, указанного `<user>` в `<domain>\<user>`параметре или. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
| `/p <password>` | Указывает пароль учетной записи пользователя, указанной в параметре **/u** . |
| /? | Отображение справки в командной строке. |

## <a name="examples"></a>Примеры

Для использования команды **bootcfg/timeout** :

```
bootcfg /timeout 30
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /timeout 50
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда bootcfg](bootcfg.md)
