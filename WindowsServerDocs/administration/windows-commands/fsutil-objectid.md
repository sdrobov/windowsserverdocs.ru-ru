---
title: fsutil objectid
description: Справочная статья по команде fsutil ObjectID, которая управляет идентификаторами объектов для трассировки других объектов, таких как файлы, каталоги и ссылки.
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: 693ab895-9d0c-47c1-9f52-df5cd287842a
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 5ab0b95bdcde8bce51e1d5a2c14888229621fcaa
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925247"
---
# <a name="fsutil-objectid"></a>fsutil objectid

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8

Управляет идентификаторами объектов (OID), которые являются внутренними объектами, используемыми службой клиента DLT и службой репликации файлов (FRS), для отслеживания других объектов, таких как файлы, каталоги и ссылки. Идентификаторы объектов невидимы для большинства программ и никогда не должны изменяться.

> [!WARNING]
> Не удаляйте, не устанавливайте или иным образом изменяйте идентификатор объекта. Удаление или установка идентификатора объекта может привести к утрате данных из фрагментов файла, вплоть до целых объемов данных включительно. Кроме того, может вызвать неблагоприятное поведение в службе клиента DLT и службе репликации файлов (FRS).

## <a name="syntax"></a>Синтаксис

```
fsutil objectid [create] <filename>
fsutil objectid [delete] <filename>
fsutil objectid [query] <filename>
fsutil objectid [set] <objectID> <birthvolumeID> <birthobjectID> <domainID> <filename>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| create | Создает идентификатор объекта, если в указанном файле еще нет такого идентификатора. Если у файла уже есть идентификатор объекта, эта подкоманда эквивалентна подкоманде **Query** . |
| удалить | Удаляет идентификатор объекта. |
| query | Запрашивает идентификатор объекта. |
| set | Задает идентификатор объекта. |
| `<objectID>` | Задает 16-байтовый шестнадцатеричный идентификатор файла, который гарантированно уникален в пределах тома. Идентификатор объекта используется службой клиента DLT и службой репликации файлов (FRS) для идентификации файлов. |
| `<birthvolumeID>` | Указывает том, на котором был обнаружен файл при первом получении идентификатора объекта. Это значение представляет собой 16-байтовый шестнадцатеричный идентификатор, используемый службой клиента DLT. |
| `<birthobjectID>` | Указывает идентификатор исходного объекта файла ( *ObjectID* может изменяться при перемещении файла). Это значение представляет собой 16-байтовый шестнадцатеричный идентификатор, используемый службой клиента DLT. |
| `<domainID>` | 16-байтовый идентификатор домена в шестнадцатеричном формате. Это значение в настоящее время не используется и должно быть установлено в значение все нули. |
| `<filename>` | Указывает полный путь к файлу, включая имя файла и расширение, например *C:\documents\filename.txt*. |

#### <a name="remarks"></a>Комментарии

- Любой файл с идентификатором объекта также имеет идентификатор «рождения», идентификатор объекта «рождение» и идентификатор домена. При перемещении файла идентификатор объекта может измениться, но идентификаторы объекта "том рождения" и "объект рождения" остаются неизменными. Такое поведение позволяет операционной системе Windows всегда находить файл независимо от того, где он был перемещен.

### <a name="examples"></a>Примеры

Чтобы создать идентификатор объекта, введите:

`fsutil objectid create c:\temp\sample.txt`

Чтобы удалить идентификатор объекта, введите:

`fsutil objectid delete c:\temp\sample.txt`

Чтобы запросить идентификатор объекта, введите:

`fsutil objectid query c:\temp\sample.txt`

Чтобы задать идентификатор объекта, введите:

`fsutil objectid set 40dff02fc9b4d4118f120090273fa9fc f86ad6865fe8d21183910008c709d19e 40dff02fc9b4d4118f120090273fa9fc 00000000000000000000000000000000 c:\temp\sample.txt`

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [fsutil](fsutil.md)
