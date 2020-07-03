---
title: bootcfg timeout
description: Справочная статья по команде bootcfg timeout, которая изменяет значение времени ожидания операционной системы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aa858eac-2bb7-4a27-a9bc-3e4a6eb8b2c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 280fb50f6e98024c58d33a174a294ac4309797ed
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85924952"
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
| `/timeout <timeoutvalue>` | Задает значение времени ожидания в разделе [boot loader]. `<timeoutvalue>`Число секунд, в течение которых пользователь должен выбрать операционную систему на экране загрузчика, прежде чем NTLDR загрузит значение по умолчанию. Допустимый диапазон для `<timeoutvalue>` — 0-999. Если значение равно 0, NTLDR сразу запускает операционную систему по умолчанию без отображения экрана загрузчика загрузки. |
| `/s <computer>` | Указывает имя или IP-адрес удаленного компьютера (не используйте обратную косую черту). По умолчанию это локальный компьютер. |
| `/u <domain>\<user>`  | Выполняет команду с разрешениями учетной записи пользователя, указанного в параметре `<user>` или `<domain>\<user>` . По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
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
