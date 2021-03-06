---
title: auditpol list
description: Справочная статья для команды auditpol list, в которой перечислены категории и подкатегории политики аудита, а также перечислены пользователи, для которых определена политика аудита на пользователя.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 45502abe-3d6e-4e13-94f0-8e6fcb6db860
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a0ce67b9907fa4c5207d75422dc972d70f5e6eea
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923719"
---
# <a name="auditpol-list"></a>auditpol list

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Список категорий и подкатегорий политики аудита, а также список пользователей, для которых определена политика аудита на пользователя.

Для выполнения операций *List* с политикой на *пользователя* необходимо иметь разрешение на **Чтение** для этого набора объектов в дескрипторе безопасности. Вы также можете выполнять операции с *списками* , если у вас есть права пользователя " **Управление аудитом и журналом безопасности** " (SeSecurityPrivilege). Однако это право предоставляет дополнительный доступ, ненеобходимый для выполнения общих операций *списка* .

## <a name="syntax"></a>Синтаксис

```
auditpol /list
[/user|/category|subcategory[:<categoryname>|<{guid}>|*]]
[/v] [/r]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ------- | -------- |
| WMIC | Извлекает всех пользователей, для которых определена политика аудита "на пользователя". При использовании с параметром/v отображается также идентификатор безопасности (SID) пользователя. |
| /category | Отображает имена категорий, распознаваемых системой. При использовании с параметром/v также отображается глобальный уникальный идентификатор (GUID) категории. |
| /субкатегори | Отображает имена подкатегорий и связанные с ними идентификаторы GUID. |
| /v | Отображает идентификатор GUID с категорией или подкатегорией или при использовании с параметром/User отображает идентификатор безопасности каждого пользователя. |
| /r | Отображает выходные данные в виде отчета в формате значений с разделителями-запятыми (CSV). |
| /? | Отображение справки в командной строке. |

## <a name="examples"></a>Примеры

Чтобы получить список всех пользователей, имеющих определенную политику аудита, введите:

```
auditpol /list /user
```

Чтобы получить список всех пользователей, которые имеют определенную политику аудита и связанные с ними идентификаторы безопасности, введите:

```
auditpol /list /user /v
```

Чтобы вывести список всех категорий и подкатегорий в формате отчета, введите:

```
auditpol /list /subcategory:* /r
```

Чтобы получить список подкатегорий подробного отслеживания и категорий доступа к службам каталогов, введите:

```
auditpol /list /subcategory:detailed Tracking,DS Access
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [команды auditpol](auditpol.md)
