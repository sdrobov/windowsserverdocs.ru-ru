---
title: getmac
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a749a348-7cd1-4336-9f33-bb42dd0e31e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c770f5da5159e0037af479f90fadb4cd83464c77
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375807"
---
# <a name="getmac"></a>getmac

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает MAC-адрес и список сетевых протоколов, связанных с каждым адресом для всех сетевых карт на каждом компьютере (локально или по сети). 
## <a name="syntax"></a>Синтаксис
```
getmac[.exe][/s <computer> [/u <Domain\<User> [/p <Password>]]][/fo {TABLE | list | CSV}][/nh][/v]
```
### <a name="parameters"></a>Параметры

|             Параметр              |                                                                                          Описание                                                                                          |
|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           /s <computer>            |                                      Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                       |
|        /u <Domain>\\<User>         | Выполняет команду с разрешениями учетной записи пользователя, указанного пользователем или домен \ пользователь. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
|           /p <Password>            |                                                     Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                     |
| /FO {CSV &#124; -&#124; файл списка таблиц} |                       Указывает формат, используемый для вывода запроса. Допустимые значения: **Table**, **List**и **CSV**. Формат выходных данных по умолчанию — **Table**.                        |
|                использован                 |                                             Подавляет вывод заголовка столбца в выходных данных. Допустим, если для параметра **/FO** задано значение **Table** или **CSV**.                                              |
|                 /v                 |                                                                    Указывает, что выходные данные отображают подробные сведения.                                                                     |
|                 /?                 |                                                                                                                                                                                               |

## <a name="remarks"></a>Замечания
**жетмак** может быть полезен либо при необходимости ввода Mac-адреса в анализатор сети, либо при необходимости узнать, какие протоколы используются на каждом сетевом адаптере компьютера.
## <a name="BKMK_Examples"></a>Примеров
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
## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
