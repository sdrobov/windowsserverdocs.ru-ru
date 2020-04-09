---
title: bootcfg query
description: Раздел команд Windows для bootcfg query, который запрашивает и отображает записи раздела Boot Loader и операционной системы из Boot. ini.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a4cacfd1-10a6-4a11-b0c5-f8abde72bfc8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1ac80c802b1d30dcf7221f94f761233c6b6fc6b6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848527"
---
# <a name="bootcfg-query"></a>bootcfg query

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Запрашивает и отображает записи разделов [boot loader] и [Operating Systems] из Boot. ini.

## <a name="syntax"></a>Синтаксис
```
bootcfg /query [/s <computer> [/u <Domain>\<User> /p <Password>]]
```
### <a name="parameters"></a>Параметры

|        Термин         |                                                                                             Определение                                                                                              |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    /s <computer>    |                                         Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.                                          |
| /u <Domain>\\<User> | Выполняет команду с разрешениями учетной записи пользователя, указанного в <User>или <Domain>\\<User>. По умолчанию заданы разрешения текущего вошедшего в систему пользователя на компьютере, выполняющем команду. |
|    /p <Password>    |                                                        Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                        |
|         /?          |                                                                                Отображает справку в командной строке.                                                                                 |

##### <a name="remarks"></a>Примечания
- Ниже приведен пример выходных данных **bootcfg/query** .
  ```
  Boot Loader Settings
  ----------
  timeout: 30
  default: multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
  Boot Entries
  ------
  Boot entry ID:   1
  Friendly Name:   
  path:            multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
  OS Load Options: /fastdetect /debug /debugport=com1:
  ```
- В разделе параметры загрузчика в выходных данных **запроса bootcfg** отображаются все записи в раздел [boot loader] файла Boot. ini.
- В разделе загрузочные записи в выходных данных **bootcfg query** отображаются следующие сведения для каждой записи операционной системы в секции [Operating Systems] файла Boot. ini: идентификатор загрузочной записи, понятное имя, путь и параметры загрузки ОС.
  ## <a name="examples"></a><a name=BKMK_examples></a>Примеров
  В следующих примерах показано, как можно использовать команду **bootcfg/query** :
  ```
  bootcfg /query
  bootcfg /query /s srvmain /u maindom\hiropln /p p@ssW23
  bootcfg /query /u hiropln /p p@ssW23
  ```
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
