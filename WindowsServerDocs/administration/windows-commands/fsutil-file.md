---
ms.assetid: 9f3dc104-dd69-4b03-b824-a29896780164
title: файл fsutil
ms.prod: windows-server-threshold
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: ffaf02f74f20f4eb94b94d8f0ffc51f26a62390e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59828125"
---
# <a name="fsutil-file"></a>файл fsutil
>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Поиск файла по имени пользователя (если включены дисковые квоты), запрашивает выделенные для файла, задает короткое имя файла, файла допустимой длины данных, нулевых данных для файла или создает новый файл.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
fsutil file [createnew] <filename> <length>
fsutil file [findbysid] <username> <directory>
fsutil file [optimizemetadata] [/A] <filename>
fsutil file [queryallocranges] offset=<offset> length=<length> <filename>
fsutil file [queryextents] [/R] <filename> [<startingvcn> [<numvcns>]]
fsutil file [queryfileid] <filename>
fsutil file [queryfilenamebyid] <volume> <fileid>
fsutil file [queryoptimizemetadata] <filename>
fsutil file [queryvaliddata] [/R] [/D] <filename>
fsutil file [seteof] <filename> <length>
fsutil file [setshortname] <filename> <shortname>
fsutil file [setvaliddata] <filename> <datalength>
fsutil file [setzerodata] offset=<offset> length=<length> <filename>

```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|CreateNew|Создает файл с заданным именем и размером, с содержимым, которое состоит из нулей.|
|\<Имя файла >|Указывает полный путь к файлу, включая имя файла и расширение, например C:\documents\filename.txt.|
|\<Длина >|Указывает длину файла допустимые данные.|
|Findbysid|Поиск файлов, принадлежащих указанному пользователю на томах NTFS, которых включены квоты.|
|\<имя пользователя >|Указывает имя пользователя или имя входа пользователя.|
|\<каталог >|Указывает полный путь к каталогу, например C:\users.|
|optimizemetadata|Это сжатие немедленно метаданные для заданного файла.|
|/A|Анализ файла метаданных, до и после оптимизации.|
|queryallocranges|Запрашивает выделенные для файла в томе NTFS. Это удобно для определения, имеет ли файл разреженным регионов.|
|offset=\<offset>|Указывает начало диапазона, который следует задать в нули.|
|Длина =\<длины >|Указывает длину диапазона (в байтах).|
|queryextents|Запрашивает экстентов для файла.|
|/R|Если <filename> является повторного анализа точки, откройте его, а не своей цели.|
|\<startingvcn>|Указывает первый VCN для запроса. Если этот параметр опущен, начните с VCN 0.|
|\<numvcns>|Число VCNs для запроса. Если опущен, либо 0, запрос до конца файла.|
|queryfileid|Запрашивает идентификатор файла в томе NTFS.<br /><br />Этот параметр применяется к:  Windows Server 2008 R2 и Windows 7.|
|\<Тома >|Указывает том, как имя диска, за которым следует двоеточие.|
|queryfilenamebyid|Отображает имя случайных ссылку для идентификатора указанного файла на томе NTFS. Так как файл будет иметь более одного имя ссылки, указывающие на этот файл, не гарантируется ссылки файла будет предоставляться в результате запроса для имени файла.<br /><br />Этот параметр применяется к:  Windows Server 2008 R2 и Windows 7.|
|\<Идентификатор файла >|Указывает идентификатор файла в томе NTFS.|
|queryoptimizemetadata|Запрашивает состояние метаданных файла.|
|queryvaliddata|Запрашивает допустимую длину данных для файла.|
|/D|Отображают сведения подробные допустимые данные.|
|seteof|Задает конец файла для заданного файла.|
|setshortname|Задает короткое имя (8.3 знаков имя файла) для файла в томе NTFS.|
|\<ShortName >|Задает короткое имя файла.|
|setvaliddata|Задает допустимую длину данных для файла в томе NTFS.|
|\<DATALENGTH >|Указывает длину файла в байтах.|
|setzerodata|Задает диапазон (определяется *смещение* и *длина*) файла в нули, который очищает файл. Если файл является разреженным, базовые кластеры не выделяются.|

## <a name="remarks"></a>Примечания

-   Возможности файловой системы NTFS, существует два основных понятия длина файла: маркер конец файла (EOF) и допустимый длина данных (VDL). EOF указывает фактическую длину файла. Параметр VDL определяет длину допустимых данных на диске. Все операции чтения между VDL и EOF автоматически возвращают 0 для сохранения объекта C2 требование повторного использования.

-   **Setvaliddata** параметр доступен только для администраторов, поскольку она требует обслуживания задачи (SeManageVolumePrivilege) выполнять тома привилегий. Этот параметр требуется только для сложных мультимедиа и области сценариев сети. **Setvaliddata** параметр должен иметь положительное значение, это больше, чем текущий VDL, но меньше, чем текущий размер файла.

    Это полезно для программ задать допустимой длины данных при:

    -   Запись исходных кластеров непосредственно на диск через канал оборудования. Это позволяет программе для информирования файловой системы, что этот диапазон содержит допустимые данные, которые могут быть возвращены для пользователя.

    -   Создание больших файлов, когда важна производительность. Это позволяет избежать время, затрачиваемое на заполнение файла нулями, при создании или расширенных файл.

## <a name="BKMK_examples"></a>Примеры
Чтобы найти файлы, которые принадлежат scottb на диске C, введите:

```
fsutil file findbysid scottb c:\users  
```

Чтобы запросить выделенные для файла на томе NTFS, введите:

```
fsutil file queryallocranges offset=1024 length=64 c:\temp\sample.txt  
```

Чтобы оптимизировать метаданные файла, введите следующую команду:

```
fsutil file optimizemetadata C:\largefragmentedfile.txt
```

Чтобы запросить экстентов для файла, введите следующую команду:

```
fsutil file queryextents C:\Temp\sample.txt
```

Чтобы задать EOF для файла, введите следующую команду:

```
fsutil file seteof C:\testfile.txt 1000
```

Чтобы задать короткое имя для файла Longfilename.txt на диске C, чтобы Longfile.txt, введите следующую команду:

```
fsutil file setshortname c:\longfilename.txt longfile.txt  
```

Чтобы задать допустимую длину данных до 4096 байт откроется файл с именем Testfile.txt в томе NTFS, введите:

```
fsutil file setvaliddata c:\testfile.txt 4096  
```

Чтобы установить ряд файлов на томе NTFS нулями до его пустым, введите следующую команду:

```
fsutil file setzerodata offset=100 length=150 c:\temp\sample.txt  
```

#### <a name="additional-references"></a>Дополнительная справка
[Ключ синтаксиса командной строки](Command-Line-Syntax-Key.md)

[fsutil](Fsutil.md)


