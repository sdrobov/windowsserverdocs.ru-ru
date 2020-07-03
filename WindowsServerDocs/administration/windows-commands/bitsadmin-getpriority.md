---
title: bitsadmin getpriority
description: Справочная статья по команде битсадмин предшествовал, которая получает приоритет указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 39ce769e2eb1dcf7a05d416dc2a66c6c082c9ae4
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926852"
---
# <a name="bitsadmin-getpriority"></a>bitsadmin getpriority

Возвращает приоритет указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getpriority <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

#### <a name="output"></a>Выходные данные

Для этой команды может быть возвращен следующий приоритет:

- **ПЕРЕДНЕГО плана**

- **ВЫСОКОМ**

- **ОБЫЧНО**

- **НИЗШУЮ**

- **UNKNOWN**

## <a name="examples"></a>Примеры

Чтобы получить приоритет для задания с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /getpriority myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
