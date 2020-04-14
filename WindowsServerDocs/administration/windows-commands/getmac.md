---
title: getmac
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a749a348-7cd1-4336-9f33-bb42dd0e31e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6b593bf61bb08d2c1c7868b1bbb175ed64a8bcf7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842617"
---
# <a name="getmac"></a>getmac

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает MAC-адрес и список сетевых протоколов, связанных с каждым адресом для всех сетевых карт на каждом компьютере (локально или по сети). 
## <a name="syntax"></a>Синтаксис
```
getmac[.exe][/s <computer> [/u <Domain\<User> [/p <Password>]]][/fo {TABLE | list | CSV}][/nh][/v]
```
#### <a name="parameters"></a>Параметры

|             Параметр              |                                                                                          Описание                                                                                          |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           /s <computer>            |                                      Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                       |
|        /u <Domain>\\<User>         | Выполняет команду с разрешениями учетной записи пользователя, указанного пользователем или домен \ пользователь. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
|           /p <Password>            |                                                     Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                     |
| /FO {CSV &#124; -&#124; файл списка таблиц} |                       Указывает формат, используемый для вывода запроса. Допустимые значения: **Table**, **List**и **CSV**. Формат выходных данных по умолчанию — **Table**.                        |
|                использован                 |                                             Подавляет вывод заголовка столбца в выходных данных. Допустим, если для параметра **/FO** задано значение **Table** или **CSV**.                                              |
|                 /v                 |                                                                    Указывает, что выходные данные отображают подробные сведения.                                                                     |
|                 /?                 |                                                                                                                                                                                               |

## <a name="remarks"></a>Примечания
**жетмак** может быть полезен либо при необходимости ввода Mac-адреса в анализатор сети, либо при необходимости узнать, какие протоколы используются на каждом сетевом адаптере компьютера.
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров
В следующих примерах показано, как можно использовать команду **жетмак** :
```
getmac /fo table /nh /v
```
```
getmac /s srvmain
```
```
getmac /s srvmain /u maindom\hiropln
```
```
getmac /s srvmain /u maindom\hiropln /p p@ssW23
```
```
getmac /s srvmain /u maindom\hiropln /p p@ssW23 /fo list /v
```
```
getmac /s srvmain /u maindom\hiropln /p p@ssW23 /fo table /nh
```
## <a name="additional-references"></a>Дополнительные материалы
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
