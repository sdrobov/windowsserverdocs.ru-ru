---
title:
- ЗАГОЛОВОК СТАТЬИ
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879565"
---
# <a name="metadata-and-markdown-template"></a>Шаблон метаданных и разметки

Этот шаблон OPS содержит примеры синтаксиса Markdown, а также указания по настройке метаданных. Чтобы получить максимальную пользу из ее, необходимо посмотреть [необработанной разметке Markdown](https://raw.githubusercontent.com/Microsoft/WindowsServerDocs-pr/master/Contributor-guide/ws-template.md?token=AG1vEhARRHNLtPgKXP35BGjNZGajKOArks5YLNIwwA%3D%3D) и [подготовленное к просмотру представление](https://github.com/Microsoft/WindowsServerDocs-pr/blob/master/Contributor-guide/ws-template.md). (Необработанной разметке Markdown виден блок метаданных, а отображаемого представления — нет.)

При создании файла Markdown следует скопировать этот шаблон в новый файл, заполнить метаданные как указано ниже, задать заголовок H1 над названием статьи и удалить содержимое. Ничего из прописных букв в квадратных скобках требует вашего внимания.


## <a name="metadata"></a>Метаданные 

Полный блок метаданных — выше. Важные примечания:

- Вы **необходимо** пробел между двоеточие (:) и значение для элемента метаданных.
- Двоеточия в значении (например, title) прервать средство синтаксического анализа метаданных. Вместо них используйте кодировку HTML для двоеточия `&#58;` (например, `"title: Azure Rights Management&#58; the basics | Azure RMS"`).
- **Заголовок**: Это название будет отображаться в результатах поисковой системы. 
- **Автор**: Поле author должно содержать **имя пользователя GitHub** автора, а не псевдоним.
- **MS.PROD**, **ms.technology**: Используйте «windows-server-threshold» ms.prod (или w10, если вы используете этот шаблон для создания содержимого для Windows 10). Попросите представителя CX, чтобы получить это значение ms.technology.

## <a name="basic-markdown-gfm-and-special-characters"></a>Базовая разметка Markdown, GFM и специальные символы

Поддерживаются все основные и GitHub flavored Markdown. Дополнительные сведения см. в разделе:

- [Базовый синтаксис Markdown](https://daringfireball.net/projects/markdown/syntax)
- [Документация по GitHub flavored Markdown (GFM)](https://guides.github.com/features/mastering-markdown)

Markdown используются специальные символы, такие как \*, \`, и \# для форматирования. Если вы хотите включить один из этих символов в содержимом, необходимо выполнить одно из следующих действий:

- Поставить обратную косую черту перед специальным символом для «подстановки» (например, \\ \* для \*)
- Используйте [код сущности HTML](http://www.ascii.cl/htmlcodes.htm) для символа (например, \& \#42\; для &#42;).

## <a name="headings"></a>Заголовки

Заголовки следует оформлять в стиле atx, то есть позволяет 1 – 6 символов решетки (#) в начале строки указывают заголовок, соответствующих уровням заголовков HTML H1 по H6. Примеры заголовков первого и второго уровня используются выше. 

Существует **необходимо** быть только один заголовок первого уровня (H1) в разделе, который будет отображаться как заголовок страницы.  

Заголовков второго уровня создается Оглавление на страницы, которое отображается в разделе «в этой статье» под заголовком страницы.

### <a name="third-level-heading"></a>Заголовок третьего уровня
#### <a name="fourth-level-heading"></a>Заголовок четвертого уровня
##### <a name="fifth-level-heading"></a>Заголовок пятого уровня
###### <a name="sixth-level-heading"></a>Заголовок шестого уровня

## <a name="text-styling"></a>Стиль текста

*Курсив* 

**Полужирный** 

~~Зачеркнутый~~

## <a name="links"></a>Ссылки

### <a name="internal-links"></a>Внутренние ссылки

Чтобы создать ссылку на заголовок в том же файле Markdown, просмотрите исходный код опубликованной статьи, найдите идентификатор заголовка (например, `id="blockquote"`) и компоновку с использованием # + идентификатор (например, `#blockquote`).

- Пример. [Цитаты](#blockquote)

Чтобы создать ссылку на файл Markdown в том же репозитории, используйте [относительные ссылки](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), включая «.md» в конце имени файла.

- Пример. [Советы и подводные камни](tips-gotchas.md)
- Пример. [Средства и программы установки для участников](../readme.md)

Чтобы создать ссылку на заголовок в файле Markdown в том же репозитории, используйте относительные ссылки и ссылки с хэштегами.

- Пример. [Удаление файлов](tips-gotchas.md#deleting-files)

### <a name="external-links"></a>Внешние ссылки

Чтобы создать ссылку на внешний файл, используйте полный URL-адрес в качестве ссылки.

- Пример. [GitHub](http://www.github.com)

Если URL-адрес появится в файле Markdown, он преобразуется в активную ссылку.

- Пример: http://www.github.com

## <a name="lists"></a>Списки

### <a name="ordered-lists"></a>Упорядоченные списки

1. Этот 
1. —
1. Инфракрасная
1. Упорядоченные
1. List  


#### <a name="ordered-list-with-an-embedded-list"></a>Упорядоченный список с внедренным списком

1. Здесь
1. поставляется
1. Объект
1. Embedded
    1. Мария Сазонова
    1. Юрий Богданов.
1. Упорядоченные
1. list


### <a name="unordered-lists"></a>Неупорядоченные списки

- Этот
- с помощью
- a
- Маркированный
- list


##### <a name="unordered-list-with-an-embedded-list"></a>Неупорядоченный список с внедренным списком

- Этот 
- Маркированный 
- list
    - Максим Измайлов
    - Никита Жданов.
- Содержит  
- др.
    1. Василий Бутусов
    1. Ольга Зуева.
- Списки


## <a name="horizontal-rule"></a>Горизонтальная линия

---

## <a name="tables"></a>Таблицы

В почти в каждом экземпляре с помощью MD форматирования в таблицах. А HTML-таблицы обеспечивают большую гибкость мы ВООБЩЕ не использовать их в наши материалы. Если HTML-таблицы в своей статье, мы не объединим эту статью.

| Таблицы        | являются           | Классно  |
| ------------- |:-------------:| -----:|
| столбец 3 выровнен      | по правому краю | $1600 |
| столбец 2 выровнен      | по центру      |   12 долл. США |
| 1 по умолчанию выровнен | По левому краю     |    $1 |


## <a name="code"></a>Код

### <a name="generic-codeblock"></a>Универсальный codeblock

Отступ кода четырех пространств для универсального codeblock кодирования.

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }


### <a name="codeblocks-with-language-identifier"></a>Codeblocks с идентификатором языка

Используйте три обратных апострофа (&#96;&#96;&#96;) + идентификатор языка, чтобы применить цвет определенного языка программирования к блоку кода.  Ниже приведен полный список [идентификаторы языков GitHub Flavored Markdown (GFM)](https://github.com/jmm/gfm-lang-ids/wiki/GitHub-Flavored-Markdown-(GFM)-language-IDs).

##### <a name="c9839"></a>C&#9839;

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

### <a name="inline-code"></a>Встроенный код

Использование обратных апострофа (&#96;) для `inline code`.

## <a name="blockquotes"></a>Цитаты

> Drought теперь продолжалась десять миллионов лет и reign ужасных давно завершен. Здесь Близ экватора, на материке, который бы один день известные как Африка, за существование дошло до новой яростью из борьба, и Виктор еще не виден. В этой бесплодной зноем Земле благоденствовать или только небольшую или swift или ярый удалось ловкие, или свирепые.

## <a name="images"></a>Изображений

### <a name="static-image"></a>Статическое изображение

![Это замещающий текст](../windowsserverdocs/get-started/media/wsbanner.png)

### <a name="linked-image"></a>Связанное изображение

[![Замещающий текст для связанного изображения](../windowsserverdocs/get-started/nano.png)](../windowsserverdocs/get-started/getting-started-with-nano-server.md) 

## <a name="alerts"></a>Предупреждения

### <a name="note"></a>Примечание.

> [!NOTE]
> Это Примечание.

### <a name="warning"></a>Предупреждение

> [!WARNING]
> Это предупреждение.

### <a name="tip"></a>Подсказка

> [!TIP]
> Это совет.

### <a name="important"></a>Важно.

> [!IMPORTANT]
> Это важно.

