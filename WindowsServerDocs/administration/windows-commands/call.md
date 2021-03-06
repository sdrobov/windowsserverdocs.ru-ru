---
title: вызывает
description: Справочная статья по команде Call, которая вызывает одну пакетную программу из другой без остановки родительской программы пакетной службы.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d34a41dc-e6c7-4467-bf6a-15cec704833e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 06/05/2018
ms.openlocfilehash: e73199b9d5633d5b3f1f7b8afd2bd35eb826bfd7
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85924834"
---
# <a name="call"></a>вызывает

Вызывает одну пакетную программу из другой без остановки родительской пакетной программы. Команда **Call** принимает метки в качестве целевого объекта вызова

> [!NOTE]
> Вызов не оказывает влияния на командную строку, если она используется вне скрипта или пакетного файла.

## <a name="syntax"></a>Синтаксис

```
call [drive:][path]<filename> [<batchparameters>] [:<label> [<arguments>]]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `[<drive>:][<path>]<filename>` | Указывает расположение и имя пакетной программы, которую необходимо вызвать. `<filename>`Параметр является обязательным и должен иметь расширение BAT или cmd. |
| `<batchparameters>` | Указывает все данные командной строки, необходимые для пакетной программы. |
| `:<label>` | Указывает метку, к которой должен перейти элемент управления программой пакетной службы. |
| `<arguments>` | Указывает сведения командной строки, передаваемые в новый экземпляр программы пакетной службы, начиная с `:<label>` .|
| /? | Отображение справки в командной строке. |

## <a name="batch-parameters"></a>Параметры пакета

Ссылки на аргумент скрипта пакетной службы (**%0**, **%1**,...) перечислены в следующих таблицах.

Использование значения **% &#42;** в пакетном скрипте означает все аргументы (например, **%1**, **%2**, **%3**...).

Можно использовать следующие необязательные синтаксисы в качестве подстановок для пакетных параметров (**% n**):

| Параметр Batch | Описание |
| --------------- | ----------- |
| % ~ 1 | Развертывает **%1** и удаляет окружающие кавычки. |
| % ~ F1 | Расширение **%1** до полного пути. |
| % ~ D1 | Расширение **%1** до буквы диска. |
| % ~ P1 | Развертывает **%1** только для пути. |
| % ~ N1 | Расширение **%1** только на имя файла. |
| % ~ x1 | Развертывает **%1** только для расширения имени файла. |
| % ~ S1 | Расширение **%1** до полного пути, содержащего только короткие имена. |
| % ~ a1 | Развертывает **%1** для атрибутов файла. |
| % ~ T1 | Увеличивает **%1** до даты и времени файла. |
| % ~ Z1 | Расширение **%1** до размера файла. |
| % ~ $PATH: 1 | Выполняет поиск в каталогах, перечисленных в переменной среды PATH, и разворачивает **%1** до полного имени найденного первого каталога. Если имя переменной среды не определено или файл не найден при поиске, то этот модификатор разворачивается до пустой строки. |

В следующей таблице показано, как можно объединить модификаторы с пакетными параметрами для составных результатов.

| Параметр Batch с модификатором | Описание |
| ----------------------------- | ----------- |
| % ~ DP1 | Расширение **%1** до буквы диска и пути. |
| % ~ nx1 | Развертывает **%1** только для имени файла и расширения. |
| % ~ точка DP $ PATH: 1 | Выполняет поиск в каталогах, перечисленных в переменной среды PATH для **%1**, а затем разворачивается на букву диска и путь к первому найденному каталогу. |
| % ~ ftza1 | Разворачивает **%1** для вывода выходных данных, аналогичных команде **dir** . |

В приведенных выше примерах **%1** и Path могут быть заменены другими допустимыми значениями. **%~** Синтаксис завершается допустимым номером аргумента. **%~** Модификаторы нельзя использовать с **% &#42;**.

### <a name="remarks"></a>Комментарии

- Использование параметров пакетной службы:

    Пакетные параметры могут содержать любые сведения, которые можно передать в пакетную программу, включая параметры командной строки, имена файлов, параметры пакета **%0** – **%9**и переменные (например, **% бод%**).

- С помощью `<label>` параметра:

    Используя **вызов** с `<label>` параметром, вы создаете новый контекст файла пакета и передаете управление оператору после указанной метки. При первом обнаружении конца пакетного файла (то есть после перехода к метке) управление возвращается оператору после оператора **Call** . При втором обнаружении конца пакетного файла пакетный сценарий завершается.

- Использование каналов и символов перенаправления:

    Не используйте каналы `(|)` или символы перенаправления ( `<` или `>` ) с **вызовом**.

- Выполнение рекурсивного вызова

    Можно создать пакетную программу, которая вызывает саму себя. Однако необходимо указать условие выхода. В противном случае родительские и дочерние пакетные программы могут подбираться бесконечно.

- Работа с расширениями команд

    Если расширения команд включены, **вызов** принимает `<label>` в качестве цели вызова. Правильный синтаксис:`call :<label> <arguments>`

## <a name="examples"></a>Примеры

Чтобы запустить checknew.bat программу из другой пакетной программы, введите следующую команду в родительской пакетной программе:

```
call checknew
```

Если родительская пакетная программа принимает два параметра пакета и требуется передать эти параметры в checknew.bat, введите следующую команду в родительской пакетной программе:

```
call checknew %1 %2
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
