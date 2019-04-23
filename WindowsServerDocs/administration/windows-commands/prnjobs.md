---
title: prnjobs
description: Узнайте, как управлять заданиями печати из командной строки.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ad34199-7a5a-40c1-8053-bccd5929df43
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 03a7f0cf36539272140ea39903bab585b4bc5c72
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889585"
---
# <a name="prnjobs"></a>prnjobs

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

приостанавливается, возобновляется, отменяет и перечисляет задания печати.

## <a name="syntax"></a>Синтаксис
```
cscript Prnjobs {-z | -m | -x | -l | -?} [-s <ServerName>] 
[-p <printerName>] [-j <JobID>] [-u <UserName>] [-w <Password>]
```

## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|-z|Приостанавливает задание печати, указанное с **-j** параметра.|
|-m|Возобновляет задание печати, указанное с **-j** параметра.|
|-x|Отменяет задание печати, указанное с **-j** параметра.|
|-l|список всех заданий печати в очереди печати.|
|-s \<ServerName >|Задает имя удаленного компьютера, на котором размещена принтера, которое вы хотите управлять. Если компьютер не указан, используется локальный компьютер.|
|-p \<Имя_принтера >|Задает имя используемого принтера, которое вы хотите управлять. Обязательный.|
|-j \<JobID >|Указывает задание печати, которое вы хотите отменить (по идентификатору).|
|-u \<UserName> -w <Password>|Задает учетную запись с разрешениями на подключение к компьютеру, на котором размещена принтера, которое вы хотите управлять. Эти разрешения всех членов локальной группы администраторов на конечном компьютере, но можно также выделить разрешения другим пользователям. Если не указать учетную запись, вы должны войти в систему с учетной записью с этими разрешениями для команды для работы.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания
-   **Prnjobs** команда — это сценарий Visual Basic, расположенный в %WINdir%\System32\printing_Admin_Scripts\\ <language> каталога. Чтобы использовать эту команду в командной строке, введите **cscript** следуют полный путь к файлу prnjobs, или изменить каталоги в соответствующую папку. Пример:
    ```
    cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnjobs
    ```
-   Если сведения, которые вы предоставляете содержит пробелы, используйте кавычки вокруг текста (например, `"computer Name"`).

## <a name="BKMK_examples"></a>Примеры
Чтобы приостановить задание на печать с Идентификатором 27, отправленных на удаленный компьютер с именем HRServer для печати на принтере с именем colorprinter задания, введите следующую команду:
```
cscript prnjobs -z -s HRServer -p colorprinter -j 27
```
Чтобы получить список всех текущих заданий печати в очереди с именем colorprinter_2 локальный принтер, введите следующую команду:
```
cscript prnjobs -l -p colorprinter_2
```

#### <a name="additional-references"></a>Дополнительная справка
[Ключ синтаксиса команд](command-line-syntax-key.md)
[команды печати](print-command-reference.md)
