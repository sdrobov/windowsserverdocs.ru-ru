---
title: secedit
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58ed57ed-08e3-403d-a363-0620b358637a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5598f830ad4cef8d45c99594da12cbcdd84e7eef
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71371109"
---
# <a name="secedit"></a>secedit



Настраивает и анализирует систему безопасности системы, сравнивая текущую конфигурацию с заданными шаблонами безопасности.

## <a name="syntax"></a>Синтаксис

```
secedit 
[/analyze /db <database file name> /cfg <configuration file name> [/overwrite] /log <log file name> [/quiet]]
[/configure /db <database file name> [/cfg <configuration filename>] [/overwrite] [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]]
[/export /db <database file name> [/mergedpolicy] /cfg <configuration file name> [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>]]
[/generaterollback /db <database file name> /cfg <configuration file name> /rbk <rollback file name> [/log <log file name>] [/quiet]]
[/import /db <database file name> /cfg <configuration file name> [/overwrite] [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]]
[/validate <configuration file name>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[Secedit:analyze](secedit-analyze.md)|Позволяет анализировать текущие системные параметры по базовым параметрам, хранящимся в базе данных.  Результаты анализа хранятся в отдельной области базы данных, и их можно просмотреть в оснастке "Настройка и анализ безопасности".|
|[Secedit:configure](secedit-configure.md)|Позволяет настроить систему с параметрами безопасности, хранящимися в базе данных.|
|[Secedit:export](secedit-export.md)|Позволяет экспортировать параметры безопасности, хранящиеся в базе данных.|
|[Secedit:generaterollback](secedit-generaterollback.md)|Позволяет создать шаблон отката по отношению к шаблону конфигурации.|
|[Secedit:import](secedit-import.md)|Позволяет импортировать шаблон безопасности в базу данных, чтобы параметры, заданные в шаблоне, можно было применять к системе или анализировать в системе.|
|[Secedit:validate](secedit-validate.md)|Позволяет проверить синтаксис шаблона безопасности.|

## <a name="remarks"></a>Примечания

Для всех имен файлов используется текущий каталог, если путь не указан.

При создании шаблона безопасности с помощью оснастки "Шаблоны безопасности" и запуска оснастки "Настройка и анализ безопасности" создаются следующие файлы:


|           Файл           |                                                                                                                                                                                                                                                               Описание                                                                                                                                                                                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        Scesrv. log        |                                                                                                                             **Расположение**:%виндир%\секурити\логс</br>**Кем создано**: операционная система</br>**Тип файла**: текст</br>**Частота обновления**: Перезаписано при запуске Secedit/Analyze,/configure,/Export или/import.</br>**Содержимое**: Содержит результаты анализа, сгруппированные по типу политики.                                                                                                                             |
| *Выбранное пользователем имя*. sdb |                                                                                    **Расположение**:% windir% \*user учетная запись @ no__t-2\Documents\Security\Database</br></em> *, созданный*<em>: Запуск оснастки "Настройка и анализ безопасности"</br></em>,*Тип файла*<em>: частный</br>*Частота обновления*</em> <em>: Обновляется при создании нового шаблона безопасности.</br></em>*содержимого*\*: Локальные политики безопасности и шаблоны безопасности, созданные пользователем.                                                                                    |
| *Выбранное пользователем имя*. log | **Расположение**. Определяемый пользователем, но по умолчанию имеет значение% WINDIR% \*user учетная запись @ no__t-1\Documents\Security\Logs</br></em> *, созданный*<em>: Выполнение подкоманд/Analyze и/configure (или с помощью оснастки "Настройка безопасности и анализ")</br>*Тип файла*</em> <em>: Text</br>*Частота обновления*</em> <em>: Выполнение подкоманд/Analyze и/configure (или с помощью оснастки "Настройка безопасности и анализ"); перезаписаны.</br></em>*содержимого*\*:</br>1.  Имя файла журнала</br>2.  Дата и время</br>3.  Результаты анализа или исследования. |
| *Выбранный пользователем файл name*. INF |                                                                                     **Расположение**:% windir% \*user учетная запись @ no__t-2\Documents\Security\Templates</br></em> *, созданный*<em>: Запуск оснастки "шаблон безопасности"</br>*Тип файла*</em> <em>: Text</br></em>*Частота обновления*<em>: каждый раз при обновлении шаблона безопасности</br></em>*содержимого*\*: Содержит сведения о настройке шаблона для каждой политики, выбранной с помощью оснастки.                                                                                     |

> [!NOTE]
> Консоль управления (MMC) и оснастка "Настройка и анализ безопасности" недоступны в Server Core.

#### <a name="additional-references"></a>Дополнительная справка

Примеры использования этой команды см. в разделе "примеры" в любом из файлов подкоманд.
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)