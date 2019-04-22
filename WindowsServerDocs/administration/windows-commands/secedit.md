---
title: secedit
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 8aaa40f21c6f14dc7d686261e9980594c14a8032
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59818465"
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
|[Secedit: анализ](secedit-analyze.md)|Позволяет анализировать текущие параметры системы, от базовых показателей конфигурации, которые хранятся в базе данных.  Результаты анализа хранятся в отдельной области базы данных и можно просмотреть в оснастку анализа и конфигурации безопасности.|
|[Secedit: Настройка](secedit-configure.md)|Можно настроить в системе с параметрами безопасности, хранимые в базе данных.|
|[Secedit:Export](secedit-export.md)|Позволяет экспортировать параметры безопасности, хранящиеся в базе данных.|
|[Secedit:generaterollback](secedit-generaterollback.md)|Позволяет создать шаблон отката шаблон конфигурации.|
|[Secedit:import](secedit-import.md)|Позволяет импортировать шаблон безопасности в базу данных, таким образом, параметры, указанные в шаблоне можно применить к системе или проанализированных по отношению к системе.|
|[Secedit: проверка](secedit-validate.md)|Позволяет проверить синтаксис шаблона безопасности.|

## <a name="remarks"></a>Примечания

Для всех имен файлов используется текущий каталог, если путь не указан.

При создании шаблона безопасности с помощью оснастки шаблон безопасности и конфигурации безопасности и запустите оснастку анализа, создаются следующие файлы:

|Файл|Описание|
|----|-----------|
|Шаблоны безопасности создаются|**Расположение**: %windir%\security\logs</br>**Созданные**: операционной системы</br>**Тип файла**: текст</br>**Частота обновления**: Перезаписываются при secedit / проанализировать, и настройка/export или выполняются/import.</br>**Содержимое**: Содержит результаты анализа, сгруппированных по типу политики.|
|*Имя выбранного пользователем*.sdb|**Расположение**: % windir %\*учетной записи пользователя * \Documents\Security\Database</br>**Созданные**: под управлением оснастки Анализ и настройка безопасности</br>**Тип файла**: собственности</br>**Частота обновления**: Обновить каждый раз, когда создается новый шаблон безопасности.</br>**Содержимое**: Локальные политики безопасности и шаблоны безопасности, созданные пользователем.|
|*Имя выбранного пользователем*.log|**Расположение**. Определяемые пользователем, но по умолчанию — % windir %\*учетной записи пользователя * \Documents\Security\Logs</br>**Создал**. Запуск / analyze и / настройка подкоманды (или с помощью оснастки Анализ и настройка безопасности)</br>**Тип файла**: текст</br>**Частота обновления**: Запуск / analyze и / настройка подкоманды (или с помощью оснастки Анализ и настройка безопасности); перезаписано.</br>**Содержимое**:</br>1.  Имя файла журнала</br>2.  Дата и время</br>3.  Результаты анализа или исследование.|
|*Имя выбранного пользователем*.inf|**Расположение**: % windir %\*учетной записи пользователя * \Documents\Security\Templates</br>**Созданные**: под управлением в оснастке шаблон параметров безопасности</br>**Тип файла**: текст</br>**Частота обновления**: каждый раз, после обновления безопасности</br>**Содержимое**: Содержит набор сведений для шаблона для каждой политики, выбранного с помощью оснастки.|

> [!NOTE]
> Консоли управления (MMC) и конфигурации безопасности и анализа оснастки не доступны в Server Core.

#### <a name="additional-references"></a>Дополнительная справка

Примеры использования этой команды см. в разделе в подразделе примеров в любой из файлов подкоманды.
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)