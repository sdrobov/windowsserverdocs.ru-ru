---
title: findstr
description: Справочная статья по команде findstr, которая выполняет поиск шаблонов текста в файлах.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c2d803fb-4cd2-46a1-a1b7-6f5e0249c418
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f0cf30f19ef23c1b3275b6b7632b03f0dd8e433a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931437"
---
# <a name="findstr"></a>findstr

Выполняет поиск шаблонов текста в файлах.

## <a name="syntax"></a>Синтаксис

```
findstr [/b] [/e] [/l | /r] [/s] [/i] [/x] [/v] [/n] [/m] [/o] [/p] [/f:<file>] [/c:<string>] [/g:<file>] [/d:<dirlist>] [/a:<colorattribute>] [/off[line]] <strings> [<drive>:][<path>]<filename>[ ...]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /b | Соответствует шаблону текста, если он находится в начале строки. |
| /e | Соответствует шаблону текста, если он находится в конце строки. |
| /l | Обрабатывает строки поиска буквально. |
| /r | Обрабатывает строки поиска в виде регулярных выражений. Это параметр по умолчанию. |
| /s | Выполняет поиск в текущем каталоге и во всех подкаталогах. |
| /i | Игнорирует регистр символов при поиске строки. |
| /x | Выводит строки, которые точно соответствуют друг другу. |
| /v | Выводит только те строки, которые не содержат совпадений. |
| /n | Выводит номер строки каждой соответствующей строки. |
| /m | Печатает только имя файла, если файл содержит совпадение. |
| /o | Выводит смещение символов перед каждой совпадающей строкой. |
| /p | Пропускает файлы с непечатаемыми символами. |
| "/OFF" [строка] | Не пропускает файлы с установленным атрибутом offline. |
| ключа`<file>` | Возвращает список файлов из указанного файла. |
| /c:`<string>` | Использует указанный текст в качестве литеральной строки поиска. |
| /g`<file>` | Возвращает строки поиска из указанного файла. |
| /d`<dirlist>` | Выполняет поиск в указанном списке каталогов. Каждый каталог должен быть отделен точкой с запятой (например,;) `dir1;dir2;dir3` . |
| /`<colorattribute>` | Задает атрибуты цвета с двумя шестнадцатеричными цифрами. Введите дополнительные `color /?` сведения. |
| `<strings>` | Задает текст для поиска в файле *filename*. Обязательный. |
| `[\<drive>:][<path>]<filename>[ ...]` | Указывает расположение и файл или файлы для поиска. Требуется по крайней мере одно имя файла. |
| /? | Отображает справку в командной строке. |

#### <a name="remarks"></a>Комментарии

- Все параметры командной строки **findstr** должны предшествовать *строкам* и *именам файлов* в строке команды.

- Для поиска шаблонов текста в регулярных выражениях используются как литеральные символы, так и мета-символы, а не точные строки символов.

  - Литеральный символ — это символ, который не имеет особого значения в синтаксисе регулярных выражений; Вместо этого он соответствует вхождению этого символа. Например, буквы и цифры являются литеральными символами.

  - Мета-символ — это символ с особым значением (оператор или разделитель) в синтаксисе регулярных выражений.

    Допустимые мета-символы:

    | Мета-символ | Значение |
    | -------------- | ----- |
    | `.` | **Подстановочный** знак — любой символ |
    | `*` | **Повтор** — ноль или более вхождений предыдущего символа или класса. |
    | `^` | **Начальное расположение строки** — начало строки. |
    | `$` | **Конечное расположение строки** — конец строки. |
    | `[class]` | **Класс символов** — любой символ в наборе. |
    | `[^class]` | **Обратный класс** — любой символ, не наявляющийся в наборе. |
    | `[x-y]` | **Range** — все символы в указанном диапазоне. |
    | `\x` | **Escape** -литеральное использование мета-символа. |
    | `<string` | **Начальное расположение слова** — начало слова. |
    | `string>` | **Конечное расположение слова** -конец слова. |

    Специальные символы в синтаксисе регулярных выражений обеспечивают наибольшее энергопотребление при совместном использовании. Например, используйте сочетание символа-шаблона ( `.` ) и Repeat ( `*` ), чтобы соответствовать любой строке символов:`.*`

    Используйте следующее выражение как часть выражения большего размера для сопоставления любой строки, начинающейся с *b* , *и заканчивая оператором with:*`b.*ing`

- Для поиска нескольких строк в наборе файлов необходимо создать текстовый файл, содержащий каждый критерий поиска в отдельной строке.

- Используйте пробелы для разделения нескольких строк поиска, если только аргумент не имеет префикса с параметром **/c**.

### <a name="examples"></a>Примеры

Для поиска *Hello* *или в* файле *x. y*введите:

```
findstr hello there x.y
```

Чтобы найти *Hello* в файле *x. y*, введите:

```
findstr /c:hello there x.y
```

Чтобы найти все вхождения слова *Windows* (с заглавной буквой W) в файле *proposal.txt*, введите:

```
findstr Windows proposal.txt
```

Для поиска всех файлов в текущем каталоге и всех подкаталогах, содержащих слово *Windows*, независимо от регистра букв, введите:

```
findstr /s /i Windows *.*
```

Чтобы найти все вхождения строк, начинающихся с и, предшествует нулю или большему числу пробелов (как в цикле компьютерной программы *) и для* вывода номера строки, где найдено каждое вхождение, введите:

```
findstr /b /n /r /c:^ *FOR *.bas
```

Чтобы получить список точных файлов, которые необходимо найти в текстовом файле, используйте условия поиска в файле *stringlist.txt*, чтобы найти файлы, перечисленные в *filelist.txt*, а затем сохраните результаты в файле *Results. out*, введите:

```
findstr /g:stringlist.txt /f:filelist.txt > results.out
```

Чтобы получить список всех файлов, содержащих слово *Computer* в текущем каталоге и всех подкаталогах, не зависимо от регистра, введите:

```
findstr /s /i /m <computer> *.*
```

Чтобы получить список всех файлов, содержащих слово Computer, и других слов, начинающихся с «Comp» (например, «Привет» и «конкурировать»), введите:

```
findstr /s /i /m <comp.* *.*
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)