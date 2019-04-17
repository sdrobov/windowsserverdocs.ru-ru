---
title:
- НАЗВАНИЕ СТАТЬИ
description: ''
author:
- GITHUB USERNAME
ms.author:
- MICROSOFT ALIAS
ms.date:
- DATE
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: ''
ms.localizationpriority:
- high/medium/low
ms.openlocfilehash: 4f885680426c0bfa55d5f73a7ef0c2143a8dd5a9
ms.sourcegitcommit: e0479b0114eac7f232e8b1e45eeede96ccd72b26
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2018
ms.locfileid: "2082541"
---
# <a name="metadata-and-markdown-template"></a>Метаданные и наценки шаблона

Этот шаблон операций содержит примеры синтаксиса наценки, а также инструкции по заданию метаданных. Для обеспечения наибольшей его, необходимо просмотреть [необработанные наценки](https://raw.githubusercontent.com/Microsoft/WindowsServerDocs-pr/master/Contributor-guide/ws-template.md?token=AG1vEhARRHNLtPgKXP35BGjNZGajKOArks5YLNIwwA%3D%3D) и [визуализации представления](https://github.com/Microsoft/WindowsServerDocs-pr/blob/master/Contributor-guide/ws-template.md). (Необработанные наценки перечислены блока метаданных, а не отображению представления.)

При создании файла наценки, должен скопировать этот шаблон в новый файл, заполнять метаданные как указано ниже, набор H1 заголовок над заголовком статьи и удалять содержимое. Что-либо из прописных букв в квадратные скобки требуют вашего внимания.


## <a name="metadata"></a>Метаданные 

Блокировать полный метаданных находится сверху. Некоторые ключевые особенности:

- **Необходимо** иметь пробела между двоеточие (:) и значение для элемента метаданных.
- Двоеточие в значение (например, заголовок) приостановки выполнения синтаксического анализа метаданных. Вместо них используется кодировка HTML-код для двоеточие из `&#58;` (например, `"title: Azure Rights Management&#58; the basics | Azure RMS"`).
- **заголовок**: это название будет отображаться в результатах поиска модуля. 
- **Автор**: поля "Автор" должен содержать **имя пользователя репозиториев** автора, не их псевдоним.
- **MS.PROD**, **ms.technology**: используйте «порога windows server» для ms.prod (или w10, если вы используете этот шаблон для создания контента для Windows 10). Поговорите с CX контакт для получения значения ms.technology.

## <a name="basic-markdown-gfm-and-special-characters"></a>Базовая наценки, GFM и специальные символы

Поддерживаются все основные и flavored репозиториев наценки. Дополнительные сведения см.

- [Синтаксис наценки базового плана](https://daringfireball.net/projects/markdown/syntax)
- [Flavored репозиториев документации наценки (GFM)](https://guides.github.com/features/mastering-markdown)

Наценки использует специальные знаки, такие как \ *, \ ", и \ # для форматирования. Если вы хотите включить один из следующих знаков в ваш контент, необходимо выполнить одно из следующих действий:

- Поместите обратная косая черта перед специальный символ «escape» (например, \\\ * для \ *)
- Используйте [объект HTML-код](http://www.ascii.cl/htmlcodes.htm) для знаков (например, \ & \#42\; для & #42;).

## <a name="headings"></a>Заголовки

Заголовки, необходимо провести то есть, с помощью стиля atx, использовать символы хэш-функции 1 – 6 (#) в начале строки для указания заголовок, соответствующий HTML-код заголовки уровни H1 до H6. Примеры первого и второго уровня заголовков используются выше. 

Наличие **должен** быть только один заголовка первого уровня (H1) в разделе, который будет отображаться в виде заголовка на странице.  

Заголовки второго уровня создаст Оглавления на веб-страница, которая отображается в разделе «в этой статье» под заголовком на страницы.

### <a name="third-level-heading"></a>Заголовок третьего уровня
#### <a name="fourth-level-heading"></a>Заголовок четвертого уровня
##### <a name="fifth-level-heading"></a>Пятый уровня заголовка
###### <a name="sixth-level-heading"></a>Заголовок уровня шестой

## <a name="text-styling"></a>Стиль текста

*Курсив* 

**Bold** 

~~Зачеркивание~~

## <a name="links"></a>Ссылки

### <a name="internal-links"></a>Внутренние ссылки

Чтобы связать заголовок в один и тот же файл наценки, просмотр источника опубликованной статьи, найдите идентификатор элемента head (, например `id="blockquote"`) и связывания с помощью # + идентификатор (например, `#blockquote`).

- Пример: [Blockquotes](#blockquote)

Чтобы связать файл наценки в одном repo, используйте [относительные ссылки](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), включая публикацию «повторно» в конце имени файла.

- Пример: [Советы и проблемы](tips-gotchas.md)
- Пример: [средства и программы установки для участников](../readme.md)

Для связи с заголовком в файле наценки в одном repo, используется относительный связывание + связывание хэш-тег.

- Пример: [Удаление файлов](tips-gotchas.md#deleting-files)

### <a name="external-links"></a>Внешние ссылки

Чтобы связать внешнего файла, используйте полный URL-адрес в качестве ссылки.

- Пример: [репозиториев](http://www.github.com)

Если в файле наценки отображается URL-адрес, он будет преобразован в ссылку.

- Пример:http://www.github.com

## <a name="lists"></a>Списки

### <a name="ordered-lists"></a>Упорядоченные списки

1. Это 
1. — Это
1. An
1. Упорядоченные
1. Список  


#### <a name="ordered-list-with-an-embedded-list"></a>Упорядоченный список с внедренным списка

1. Здесь
1. поступающие
1. an
1. внедренные
    1. Пропустите Scarlett
    1. Профессора слива
1. упорядоченные
1. list


### <a name="unordered-lists"></a>Неупорядоченные списки

- Это
-  с помощью 
- а
- Маркированный
- list


##### <a name="unordered-list-with-an-embedded-list"></a>Маркированный список с внедренным списка

- Это 
- Маркированный 
- list
    - Госпожа Петров
    - Зеленый г
- содержит  
- другое
    1. Вашего colonel
    1. Технический Госпожа
- списки


## <a name="horizontal-rule"></a>Горизонтальная линия

---

## <a name="tables"></a>Таблицы

В почти каждый экземпляр используйте MD форматирования для таблиц. В то время как HTML-таблицы большей гибкостью, мы не следует использовать их в материалами. Если в вашей статье HTML-таблицы, мы не будут объединены этой статьи.

| Таблицы        | Являются           | Классно  |
| ------------- |:-------------:| -----:|
| — Это столбец 3      | по правому краю | 1600 $ |
| — Это столбец 2      | по центру      |   12 долл. США |
| по умолчанию выбрана столбца 1 | по левому краю     |    $1 |


## <a name="code"></a>Код

### <a name="generic-codeblock"></a>Универсальный codeblock

Отступ кода четырех пробелов для универсального codeblock написания кода.

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }


### <a name="codeblocks-with-language-identifier"></a>Codeblocks с идентификатором языка

Используйте три backticks (#96; #96; & #96;) + идентификатор языка для применения цвета зависящие от языка программирования с блока кода.  Ниже приведен полный список [идентификаторы языка репозиториев Flavored наценки (GFM)](https://github.com/jmm/gfm-lang-ids/wiki/GitHub-Flavored-Markdown-(GFM)-language-IDs).

##### <a name="c9839"></a>C & #9839;

```c#
using System;
namespace HelloWorld
{
    class Hello 
    {
        static void Main() 
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```
#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```
#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="inline-code"></a>Встроенного кода

Используйте backticks (и #96;) для `inline code`.

## <a name="blockquotes"></a>Blockquotes

> Drought продолжалась теперь 10 миллионов лет и reign видеть lizards срок, поскольку завершено. Здесь на экватора в континент которого будет один день известных как Африка, эти технологии существование связаться с вами нового climax ferocity и Виктор еще не видны. В этом Земля пустынный и desiccated только небольшой или swift из-за жесткой может Цветистый или даже надеюсь выдержать.

## <a name="images"></a>Изображения

### <a name="static-image"></a>Статическое изображение

![Это альтернативный текст](../windowsserverdocs/get-started/media/wsbanner.png)

### <a name="linked-image"></a>Связанные изображения

[![alt текст для связанного изображения](../windowsserverdocs/get-started/nano.png)](../windowsserverdocs/get-started/getting-started-with-nano-server.md) 

## <a name="alerts"></a>Alerts

### <a name="note"></a>Примечание.

> [!NOTE]
> Это примечание

### <a name="warning"></a>Warning

> [!WARNING]
> Это предупреждение

### <a name="tip"></a>Совет

> [!TIP]
> Это ПОДСКАЗКИ

### <a name="important"></a>Важно!

> [!IMPORTANT]
> Это важно

