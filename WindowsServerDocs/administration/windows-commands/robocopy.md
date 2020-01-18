---
title: robocopy
description: Узнайте, как использовать команду Robocopy в Windows и Windows Server для копирования файлов
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d4c6e8e9-fcb3-4a4a-9d04-2d8c367b6354
author: coreyp-at-msft
ms.author: coreyp
manager: lizapo
ms.date: 07/25/2018
ms.openlocfilehash: f675f66eaafbfd79ac6b452a92417159d8ebb28c
ms.sourcegitcommit: 51e0b575ef43cd16b2dab2db31c1d416e66eebe8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2020
ms.locfileid: "76259040"
---
# <a name="robocopy"></a>robocopy

Копирует данные файла.

## <a name="syntax"></a>Синтаксис

```
robocopy <Source> <Destination> [<File>[ ...]] [<Options>]
```

## <a name="parameters"></a>Параметры

|   Параметр    |                                                                                            Описание                                                                                           |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   > источника \<    |                                                                            Указание пути к исходному каталогу.                                                                           |
| > назначения \< |                                                                          Указание пути к целевому каталогу.                                                                        |
|    \<файл >     | Указывает копируемый файл или файлы. При необходимости можно использовать подстановочные **&#42;** знаки (или **?** ). Если параметр **файла** не указан, в качестве значения по умолчанию используется **\*.\*** . |
|   Параметры \<   |                                                                    Указывает параметры для использования с командой **Robocopy** .                                                                   |

### <a name="copy-options"></a>Параметры копирования

|Параметр|Описание|
|------|-----------|
|/s|Копирует подкаталоги. Обратите внимание, что этот параметр исключает пустые каталоги.|
|/e|Копирует подкаталоги. Обратите внимание, что этот параметр включает пустые каталоги. Дополнительные сведения см. в разделе [Примечания](#remarks).|
|/Лев:\<N >|Копирует только *N* верхних уровней исходного дерева каталогов.|
|/z|Копирование файлов в перезапускаемом режиме.|
|/b|Копирует файлы в режиме резервного копирования.|
|/zb|Использует перезапускаемый режим. Если доступ запрещен, то для этого параметра используется режим резервного копирования.|
|/efsraw|Копирует все зашифрованные файлы в режиме файловой системы EFS RAW.|
|/Copy:\<Копифлагс >|Задает свойства файла для копирования. Ниже приведены допустимые значения для этого параметра.</br>**D** данных</br>**Атрибуты**</br>Метки времени **T**</br>Список управления доступом (ACL) **для NTFS**</br>**O** сведения о владельце</br>**U** . сведения аудита</br>Значение по умолчанию для **копифлагс** — **dat** (данные, атрибуты и метки времени).|
|/дкопи:\<копифлагс\>|Определяет, какие объекты нужно копировать для каталогов. Значение по умолчанию — DA. Возможные варианты: D = Data, A = Attributes и T = timestamps.|
|/сек|Копирует файлы с безопасностью (эквивалентно **/Copy: DATS**).|
|/копялл|Копирует все сведения о файле (эквивалентно **/Copy: датсау**).|
|/нокопи|Не копирует сведения о файле (полезное с **/пурже**).|
|/секфикс|Исправляет безопасность файлов для всех файлов, даже пропущенных.|
|/тимфикс|Исправляет время файла для всех файлов, даже пропущенных.|
|/пурже|Удаляет целевые файлы и каталоги, которые больше не существуют в источнике. Дополнительные сведения см. в разделе [Примечания](#remarks).|
|/мир|Зеркальное отражение дерева каталогов (эквивалентно **/e** плюс **/пурже**). Дополнительные сведения см. в разделе [Примечания](#remarks).|
|/мов|Перемещает файлы и удаляет их из источника после копирования.|
|/Move|Перемещает файлы и каталоги и удаляет их из источника после копирования.|
|/a +: [РАШКНЕТ]|Добавляет указанные атрибуты в скопированные файлы.|
|/а-: [РАШКНЕТ]|Удаляет указанные атрибуты из скопированных файлов.|
|/CREATE|Создает дерево каталогов и только файлы нулевой длины.|
|/фат|Создает файлы назначения, используя только имена файлов FAT длиной 8,3 символов.|
|/256|Отключает поддержку слишком длинных путей (более 256 символов).|
|/Мон:\<N >|Отслеживает источник и выполняется снова при обнаружении более *N* изменений.|
|/МОТ:\<M >|Отслеживание источника и повторный запуск через *M* минут при обнаружении изменений.|
|/MT [: N]|Создает многопоточные копии с *N* потоками. Значение *N* должно быть целым числом от 1 до 128. Значение по умолчанию для *N* равно 8.</br>Параметр **/MT** не может использоваться с параметрами **/ИПГ** и **/ефсрав** .</br>Перенаправление вывода с помощью параметра **/log** для повышения производительности.</br>Примечание. параметр/MT применяется к Windows Server 2008 R2 и Windows 7.|
|/РХ: ЧЧММ — ЧЧММ|Указывает время выполнения, когда могут быть запущены новые копии.|
|/PF|Проверяет время выполнения для каждого файла (не для каждого прохода).|
|/ИПГ: n|Указывает зазор между пакетами для освобождения пропускной способности в медленной линии.|
|/сл|Не используйте символьные ссылки, а вместо этого создайте копию ссылки.|

> [!IMPORTANT]
> When using the **/SECFIX** copy option, specify the type of security information you want to copy by also using one of these additional copy options:
>- **/COPYALL**
>- **/COPY:O**
>- **/COPY:S**
>- **/COPY:U**
>- **/SEC**

### <a name="file-selection-options"></a>File selection options

|Параметр|Описание|
|------|-----------|
|/a|Copies only files for which the **Archive** attribute is set.|
|/m|Copies only files for which the **Archive** attribute is set, and resets the **Archive** attribute.|
|/ia:[RASHCNETO]|Includes only files for which any of the specified attributes are set.|
|/xa:[RASHCNETO]|Excludes files for which any of the specified attributes are set.|
|/xf \<FileName>[ ...]|Excludes files that match the specified names or paths. Note that *FileName* can include wildcard characters ( **&#42;** and **?** ).|
|/xd \<Directory>[ ...]|Excludes directories that match the specified names and paths.|
|/xc|Excludes changed files.|
|/xn|Excludes newer files.|
|/xo|Excludes older files.|
|/xx|Excludes extra files and directories.|
|/xl|Excludes "lonely" files and directories.|
|/is|Включает одни и те же файлы.|
|/it|Includes "tweaked" files.|
|/max:\<N>|Specifies the maximum file size (to exclude files bigger than *N* bytes).|
|/min:\<N>|Specifies the minimum file size (to exclude files smaller than *N* bytes).|
|/maxage:\<N>|Specifies the maximum file age (to exclude files older than *N* days or date).|
|/minage:\<N>|Specifies the minimum file age (exclude files newer than *N* days or date).|
|/maxlad:\<N>|Specifies the maximum last access date (excludes files unused since *N*).|
|/minlad:\<N>|Specifies the minimum last access date (excludes files used since *N*) If *N* is less than 1900, *N* specifies the number of days. Otherwise, *N* specifies a date in the format YYYYMMDD.|
|/xj|Excludes junction points, which are normally included by default.|
|/fft|Предположение времени файла FAT (двухсекундная точность).|
|/dst|Compensates for one-hour DST time differences.|
|/xjd|Excludes junction points for directories.|
|/xjf|Excludes junction points for files.|

### <a name="retry-options"></a>Retry options

|Параметр|Описание|
|------|-----------|
|/r:\<N>|Указание количества повторных попыток для неудавшихся копий. The default value of *N* is 1,000,000 (one million retries).|
|/w:\<N>|Указание времени ожидания между повторными попытками в секундах. The default value of *N* is 30  (wait time 30 seconds).|
|/reg|Saves the values specified in the **/r** and **/w** options as default settings in the registry.|
|/tbd|Specifies that the system will wait for share names to be defined (retry error 67).|

### <a name="logging-options"></a>Параметры ведения журнала

|Параметр|Описание|
|------|-----------|
|/l|Specifies that files are to be listed only (and not copied, deleted, or time stamped).|
|/x|Reports all extra files, not just those that are selected.|
|/v|Produces verbose output, and shows all skipped files.|
|/ts|Includes source file time stamps in the output.|
|/fp|Includes the full path names of the files in the output.|
|/bytes|Prints sizes, as bytes.|
|/ns|Specifies that file sizes are not to be logged.|
|/nc|Specifies that file classes are not to be logged.|
|/nfl|Указание, что имена файлов не должны регистрироваться.|
|/ndl|Указание, что имена каталогов не должны регистрироваться.|
|/np|Указывает, что не нужно отображать ход выполнения операции копирования (количество копируемых файлов или каталогов).|
|/eta|Shows the estimated time of arrival (ETA) of the copied files.|
|/log:\<LogFile>|Запись выходных данных о состоянии в файл журнала (перезапись существующего файла журнала).|
|/log+:\<LogFile>|Writes the status output to the log file (appends the output to the existing log file).|
|/unicode|Displays the status output as Unicode text.|
|/unilog:\<LogFile>|Writes the status output to the log file as Unicode text (overwrites the existing log file).|
|/unilog+:\<LogFile>|Writes the status output to the log file as Unicode text (appends the output to the existing log file).|
|/tee|Writes the status output to the console window, as well as to the log file.|
|/njh|Specifies that there is no job header.|
|/njs|Specifies that there is no job summary.|

### <a name="job-options"></a>Job options

|Параметр|Описание|
|------|-----------|
|/job:\<JobName>|Specifies that parameters are to be derived from the named job file.|
|/save:\<JobName>|Specifies that parameters are to be saved to the named job file.|
|/quit|Quits after processing command line (to view parameters).|
|/nosd|Указывает, что исходный каталог не указан.|
|/нодд|Указывает, что конечный каталог не указан.|
|/If|Включает указанные файлы.|

### <a name="exit-return-codes"></a>Коды выхода (Return)

Применение | Описание
-- | --
0 | Файлы не были скопированы. Сбой не обнаружен.  Нет несовпадающих файлов. Файлы уже существуют в целевом каталоге; Поэтому операция копирования была пропущена.
1 | Все файлы успешно скопированы.
2 | В целевом каталоге имеются дополнительные файлы, отсутствующие в исходном каталоге. Файлы не были скопированы.
3 | Некоторые файлы были скопированы. Имеются дополнительные файлы. Сбой не обнаружен.
5 | Некоторые файлы были скопированы. Некоторые файлы не совпали. Сбой не обнаружен.
6 | Существуют дополнительные файлы и несоответствующие файлы. Файлы не были скопированы, ошибок не обнаружено. Это означает, что файлы уже существуют в целевом каталоге.
7 | Файлы были скопированы, обнаружено несоответствие файлов, и имеются дополнительные файлы.
8 | Не удалось скопировать несколько файлов.

> [!NOTE]
> Любое значение больше 8 указывает, что во время операции копирования существовала хотя бы одна ошибка.

### <a name="remarks"></a>Примечания.

-   Параметр **/мир** равнозначен параметру **/e** Plus **/пурже** с одним небольшим различием в поведении:  
    -   Если задан параметр **/e** плюс **/пурже** , то при наличии конечного каталога параметры безопасности каталога назначения не перезаписываются.
    -   При использовании параметра **/мир** , если каталог назначения существует, параметры безопасности каталога назначения перезаписываются.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
