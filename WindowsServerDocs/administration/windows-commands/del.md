---
title: del
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 346eede2-2085-44f5-9936-6877b5d5a833
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a1c2756e53d9f047160ddd037b3868e47d6e3181
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59822995"
---
# <a name="del"></a>del



Удаляет один или несколько файлов. Эта команда совпадает со значением **стереть** команды.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
del [/p] [/f] [/s] [/q] [/a[:]<Attributes>] <Names>
erase [/p] [/f] [/s] [/q] [/a[:]<Attributes>] <Names>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имена >|Задает список одного или нескольких файлов или каталогов. Чтобы удалить несколько файлов, может использовать подстановочные знаки. Если задан каталог, будут удалены все файлы в каталоге.|
|/p|Запрашивает подтверждение перед удалением указанного файла.|
|/f|Задает удаление файлов только для чтения.|
|/s|Удаляет заданные файлы текущего каталога и всех подкаталогах. Отображает имена файлов, так как они будут удалены.|
|/q|Задает тихий режим. Подтверждение удаления не запрашиваются.|
|/ a [::]\<атрибуты >|Удаляет файлы, на основе следующих атрибутов:</br>**r** файлы, доступные только для чтения</br>**h** скрытые файлы</br>**я** не индексированных файлов содержимого</br>**s** системные файлы</br>**** готовые к архивированию</br>**l** точки повторного анализа</br>— Префикс «not»|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

> [!CAUTION]
> Если вы используете **del** для удаления файла с диска, его нельзя будет восстановить.
-   Если вы используете **/p**, **del** отображает имя файла и отправляет следующее сообщение:

    `FileName, Delete (Y/N)?`

    Чтобы подтвердить удаление, нажмите клавишу "Y". Для отмены удаления и отображаемое имя следующего файла (то есть, если задана группа файлов), клавишу N. Чтобы остановить **del** команду, нажмите клавиши CTRL + C.
-   При отключении расширения команд **/s** отображает имена файлов, которые не были найдены вместо отображения имен файлов, которые удаляются (то есть имеет противоположный).
-   Если необходимо указать папку в *имена*, будут удалены все файлы в папке. Например следующая команда удаляет все файлы в папке \Work:  
    ```
    del \work
    ```  
-   Можно использовать подстановочные знаки (**&#42;** и **?**) удалить более одного файла за раз. Тем не менее, чтобы избежать нежелательных удалений, следует использовать подстановочные знаки с осторожностью **del** команды. Например, если ввести следующую команду:  
    ```
    del *.*
    ```  
    **Del** команда отображает следующее сообщение:

    `Are you sure (Y/N)?`

    Чтобы удалить все файлы в текущем каталоге, нажмите клавишу Y и нажмите клавишу ВВОД. Для отмены удаления, нажмите клавишу N и нажмите клавишу ВВОД.

> [!NOTE]
> Прежде чем использовать подстановочные знаки с **del** команды, используйте те же символы подстановки с **dir** команду, чтобы вывести список всех файлов, которые будут удалены.
-   **Del** команда, с различными параметрами доступна в консоли восстановления.

## <a name="BKMK_examples"></a>Примеры

Чтобы удалить все файлы в папку с именем теста на диске C, введите одно из следующих:
```
del c:\test
del c:\test\*.*
```
Чтобы удалить все файлы с расширением .bat из текущего каталога, введите следующую команду:
```
del *.bak
```
Чтобы удалить все файлы только для чтения в текущем каталоге, введите следующую команду:
```
del /a:r *.*
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)