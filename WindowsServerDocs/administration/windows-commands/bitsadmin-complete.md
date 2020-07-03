---
title: bitsadmin complete
description: Справочная статья по команде битсадмин Complete, которая завершает задание.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a5e86677-8f7b-43b3-929e-97706c57e7f1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 08fb74690f5a8f70611bb6ca52a291bec89d81e8
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928353"
---
# <a name="bitsadmin-complete"></a>bitsadmin complete

Завершает задание. Используйте этот параметр после перемещения задания в состояние "передано". В противном случае будут доступны только те файлы, которые были успешно переданы.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /complete <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="example"></a>Пример

Чтобы завершить задание *мидовнлоаджоб* , после достижения `TRANSFERRED` состояния выполните следующие действия.

```
bitsadmin /complete myDownloadJob
```

Если несколько заданий используют *мидовнлоаджоб* в качестве имени, необходимо использовать идентификатор GUID задания, чтобы однозначно идентифицировать его для завершения.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
