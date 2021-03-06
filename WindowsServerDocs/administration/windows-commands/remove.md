---
title: remove
description: Справочная статья по команде Remove, которая удаляет букву диска или точку подключения из тома.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b0886140-da8b-4231-8cb2-f280874d99c0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7fba062945effd49efa9987d2c7d23fc90552fd4
ms.sourcegitcommit: 145cf75f89f4e7460e737861b7407b5cee7c6645
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87409685"
---
# <a name="remove"></a>remove

Удаляет букву диска или точку подключения из тома, имеющего фокус. Если используется параметр ALL, удаляются все текущие буквы диска и точки подключения. Если буква диска или точка подключения не указана, программа DiskPart удаляет первую обнаруженную букву диска или точку подключения.

Команду Remove также можно использовать для изменения буквы диска, связанной со съемным носителем. Вы не можете удалить буквы дисков на системном диске, загрузочном томе или томах подкачки. Кроме того, нельзя удалить букву диска для раздела OEM, любой раздел GPT с нераспознаваемым GUID или любой из специальных разделов GPT, не связанных с данными, таких как системный раздел EFI.

> [!NOTE]
> Для завершения команды **удаления** необходимо выбрать том. Используйте команду [Выбор тома](select-volume.md) , чтобы выбрать диск и переместить фокус на него.

## <a name="syntax"></a>Синтаксис

```
remove [{letter=<drive> | mount=<path> [all]}] [noerr]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Letter =`<drive>` | Буква диска для удаления. |
| подключение =`<path>` | Путь к точке подключения для удаления. |
| все | Удаляет все текущие буквы дисков и точки подключения. |
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

### <a name="examples"></a>Примеры

Удаление d:\ диск, введите:

```
remove letter=d
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
