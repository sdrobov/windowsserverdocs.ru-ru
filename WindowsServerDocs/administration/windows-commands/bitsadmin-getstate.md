---
title: bitsadmin getstate
description: Справочный раздел по команде битсадминического состояния, который получает состояние указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1252d6cf-14ca-44df-beb2-930ff011f297
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ab014c96c6d5d62232243d704d41d33cfcfc50f0
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717541"
---
# <a name="bitsadmin-getstate"></a>bitsadmin getstate

Возвращает состояние указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getstate <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание: |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

#### <a name="output"></a>Вывод

Возвращаемые выходные значения могут быть:

| Область | Описание |
| --------------- | ----------- |
| Поставлено в очередь | Задание ожидает запуска. |
| Соединение | Служба BITS свяжется с сервером. |
| Передача | BITS передает данные. |
| Передаются | Служба BITS успешно передала все файлы в задании. |
| Приостановлена | Задание приостановлено. |
| Error | Произошла неустранимая ошибка; Повторная попытка перемещения не выполняется. |
| Transient_Error | Произошла устранимая ошибка; Повторная попытка передачи после истечения минимальной задержки. |
| Подтверждено | Задание завершено. |
| Отменено | Задание отменено. |

## <a name="examples"></a>Примеры

Чтобы получить состояние для задания с именем *мидовнлоаджоб*:

```
bitsadmin /getstate myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
