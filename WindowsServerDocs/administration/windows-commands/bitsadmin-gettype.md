---
title: bitsadmin gettype
description: Справочный раздел для команды битсадмин GetType, который получает тип задания для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bec16f04-3e95-4587-889e-3de6ad03c9c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 151f9b8e81229a666111ebcd20f060d84160445a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717479"
---
# <a name="bitsadmin-gettype"></a>bitsadmin gettype

Возвращает тип задания для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /gettype <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

#### <a name="output"></a>Вывод

Возвращаемые выходные значения могут быть:

| Type | Описание |
| --------------- | ----------- |
| Скачать | Задание является загружаемым. |
| Передать | Задание — это отправка. |
| Отправка и ответ | Задание представляет собой отправку и ответ. |
| Неизвестно | Задание имеет неизвестный тип. |

## <a name="examples"></a>Примеры

Чтобы получить тип задания для задания с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /gettype myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
