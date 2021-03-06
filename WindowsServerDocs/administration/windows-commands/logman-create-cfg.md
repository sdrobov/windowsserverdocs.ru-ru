---
title: logman create cfg
description: Справочная статья по команде Logman Create cfg, которая создает сборщик данных конфигурации.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bfc87093-3ff5-4e19-aa93-d185fb8e2239
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f4ae073561ddfc26f4a6a1af834113cff0cc9e29
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932081"
---
# <a name="logman-create-cfg"></a>logman create cfg

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает сборщик данных конфигурации.

## <a name="syntax"></a>Синтаксис

```
logman create cfg <[-n] <name>> [options]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| -s`<computer name>` | Выполняет команду на указанном удаленном компьютере. |
| -config`<value>` | Указывает файл параметров, содержащий параметры команды. |
| [-n]`<name>` | Имя целевого объекта. |
| -[-] u`<user [password]>` | Указывает пользователя для запуска от имени. При вводе \* для пароля выводится запрос на ввод пароля. Пароль не отображается при вводе. |
| -m`<[start] [stop] [[start] [stop] [...]]>` | Изменения в начале или в ручном режиме вместо запланированного начала или окончания. |
| -RF`<[[hh:]mm:]ss>` | Запускает сборщик данных за указанный период времени. |
| -б`<M/d/yyyy h:mm:ss[AM|PM]>` | Начинает сбор данных в указанное время. |
| -e `<M/d/yyyy h:mm:ss[AM|PM]>` | Завершает сбор данных в указанное время. |
| -Si`<[[hh:]mm:]ss>` | Указывает интервал выборки для собираются данных счетчиков производительности. |
| -o`<path|dsn!log>` | Указывает выходной файл журнала или имя DSN и набора журналов в базе данных SQL. |
| -[-] r | Повторяет сборщик данных ежедневно с заданным временем начала и окончания. |
| -[-] a | Добавляет существующий файл журнала. |
| -[-] | Перезаписывает существующий файл журнала. |
| -[-] v`<nnnnnn|mmddhhmm>` | Присоединяет сведения о управлении версиями файлов к концу имени файла журнала. |
| -[-] RC`<task>` | Выполняет команду, указанную при каждом закрытии журнала. |
| -[-] максимум`<value>` | Максимальный размер файла журнала (в МБ или в максимальном количестве записей для журналов SQL). |
| -[-] cnf`<[[hh:]mm:]ss>` | Если указано время, создает новый файл по истечении указанного времени. Если параметр time не указан, создает новый файл при превышении максимального размера. |
| -y | Отвечает Да на все вопросы без запроса. |
| -[-] Ni | Включает (-Ni) или отключает (-Ni) запрос сетевого интерфейса. |
| -REG`<path [path [...]]>` | Указывает значения реестра для накопления. |
| -центр`<query [query [...]]>` | Указывает WMI-объекты для собираются с помощью языка запросов SQL. |
| -ФТК`<path [path [...]]>` | Указывает полный путь к файлам для собраний. |
| /? | Отображает контекстную справку. |

#### <a name="remarks"></a>Комментарии

- Где [-] присутствует, Добавление дополнительного дефиса (-) инвертирует параметр.

### <a name="examples"></a>Примеры

Чтобы создать сборщик данных конфигурации с именем cfg_log, в разделе реестра `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Currentverion\` введите:

```
logman create cfg cfg_log -reg HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Currentverion\\
```

Чтобы создать сборщик данных конфигурации с именем cfg_log, который записывает все объекты WMI из `root\wmi` столбца базы данных `MSNdis_Vendordriverversion` , введите:

```
logman create cfg cfg_log -mgt root\wmi:select * FROM MSNdis_Vendordriverversion
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [команда logman Update cfg](logman-update-cfg.md)

- [команда logman](logman.md)
