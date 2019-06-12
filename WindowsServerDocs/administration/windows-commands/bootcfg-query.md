---
title: bootcfg query
description: Раздел Windows команды для **запроса bootcfg** -запросы и отображает [загрузчик] и [операционные системы], раздел записи из файла Boot.ini.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: e79acc100a9ec9955f2692a3c6ee812d0310b687
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66434728"
---
# <a name="bootcfg-query"></a>bootcfg query

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запрос и отображение [загрузчик] и [операционные системы] разделе записей из файла Boot.ini.

## <a name="syntax"></a>Синтаксис
```
bootcfg /query [/s <computer> [/u <Domain>\<User> /p <Password>]]
```
## <a name="parameters"></a>Параметры

|        Термин         |                                                                                             Определение                                                                                              |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>    |                                         Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain>\\<User> | Выполняет команду с разрешениями учетной записи пользователя, указанного по <User>или <Domain> \\ <User>. По умолчанию используется разрешения текущего, вошедшего в систему пользователя на компьютере, используя следующую команду. |
|    /p <Password>    |                                                        Указывает пароль для учетной записи пользователя, который указан в **/u** параметра.                                                        |
|         /?          |                                                                                Отображение справки в командной строке.                                                                                 |

##### <a name="remarks"></a>Примечания
- Ниже приведен пример **неправильный** выходные данные:
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
- Параметры загрузки часть **запроса bootcfg** выходных данных отображает каждый элемент в разделе [загрузчик] файла Boot.ini.
- Загрузочные записи часть **запроса bootcfg** выходных данных отображаются следующие сведения для каждой записи операционной системы в разделе [operating systems] файла Boot.ini: Загрузочной записи, понятное имя, путь и параметры загрузки операционной системы.
  ## <a name="BKMK_examples"></a>Примеры
  В следующих примерах показано, как можно использовать **неправильный** команды:
  ```
  bootcfg /query
  bootcfg /query /s srvmain /u maindom\hiropln /p p@ssW23
  bootcfg /query /u hiropln /p p@ssW23
  ```
  #### <a name="additional-references"></a>Дополнительные ссылки
  [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
