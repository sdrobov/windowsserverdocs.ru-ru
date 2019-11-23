---
title: bootcfg query
description: Раздел команд Windows для запросов **bootcfg query** и отображает записи разделов [boot loader] и [Operating Systems] из Boot. ini.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a4cacfd1-10a6-4a11-b0c5-f8abde72bfc8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ae82357cfe178343872448c2ebd46c49a797b5a9
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379912"
---
# <a name="bootcfg-query"></a>bootcfg query

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запрашивает и отображает записи разделов [boot loader] и [Operating Systems] из Boot. ini.

## <a name="syntax"></a>Синтаксис
```
bootcfg /query [/s <computer> [/u <Domain>\<User> /p <Password>]]
```
## <a name="parameters"></a>Параметры

|        Термин         |                                                                                             Определение                                                                                              |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>    |                                         Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain>\\<User> | Выполняет команду с разрешениями учетной записи пользователя, указанного в <User>или <Domain>\\<User>. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
|    /p <Password>    |                                                        Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                        |
|         /?          |                                                                                Отображение справки в командной строке.                                                                                 |

##### <a name="remarks"></a>Замечания
- Ниже приведен пример выходных данных **bootcfg/query** .
  ```
  Boot Loader Settings
  ----------
  timeout: 30
  default: multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
  Boot Entries
  ------
  Boot entry ID:   1
  Friendly Name:   ""
  path:            multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
  OS Load Options: /fastdetect /debug /debugport=com1:
  ```
- В разделе параметры загрузчика в выходных данных **запроса bootcfg** отображаются все записи в раздел [boot loader] файла Boot. ini.
- В разделе загрузочные записи в выходных данных **bootcfg query** отображаются следующие сведения для каждой записи операционной системы в секции [Operating Systems] файла Boot. ini: идентификатор загрузочной записи, понятное имя, путь и параметры загрузки ОС.
  ## <a name="BKMK_examples"></a>Примеров
  В следующих примерах показано, как можно использовать команду **bootcfg/query** :
  ```
  bootcfg /query
  bootcfg /query /s srvmain /u maindom\hiropln /p p@ssW23
  bootcfg /query /u hiropln /p p@ssW23
  ```
  #### <a name="additional-references"></a>Дополнительные ссылки
  [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
