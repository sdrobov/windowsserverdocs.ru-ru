---
title: bootcfg timeout
description: Раздел команд Windows для команды bootcfg timeout, который изменяет значение времени ожидания операционной системы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aa858eac-2bb7-4a27-a9bc-3e4a6eb8b2c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b56e609d5e3b7c92a887a98ae5d02bfbfb7a78e6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848497"
---
# <a name="bootcfg-timeout"></a>bootcfg timeout

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет значение времени ожидания операционной системы.

## <a name="syntax"></a>Синтаксис

```
bootcfg /timeout <timeOutValue> [/s <computer> [/u <Domain\User>/p <Password>]]
```

### <a name="parameters"></a>Параметры


|        Параметр        |                                                                                                                                                                                  Описание                                                                                                                                                                                   |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /timeout <timeOutValue> | Задает значение времени ожидания в разделе [boot loader]. <timeOutValue> — число секунд, в течение которых пользователь должен выбрать операционную систему на экране загрузчика, прежде чем NTLDR загрузит значение по умолчанию. Допустимый диапазон для <timeOutValue> — 0-999. Если значение равно 0, то NTLDR сразу запускает операционную систему по умолчанию без отображения экрана загрузчика загрузки. |
|      /s <computer>      |                                                                                                                               Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                                                                                                               |
|    /u < домен \ пользователь >     |                                                                                       Выполняет команду с разрешениями учетной записи пользователя, заданного <User> или < домен \ пользователь >. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду.                                                                                        |
|      /p <Password>      |                                                                                                                                            Указывает <Password> учетной записи пользователя, указанной в параметре **/u** .                                                                                                                                             |
|           /?            |                                                                                                                                                                      Отображает справку в командной строке.                                                                                                                                                                      |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
В следующих примерах показано, как можно использовать команду **bootcfg/timeout** :
```
bootcfg /timeout 30
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /timeout 50
```
## <a name="additional-references"></a>Дополнительные материалы
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
