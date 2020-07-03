---
title: bitsadmin getstate
description: Справочная статья по команде битсадминического состояния, которая получает состояние указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1252d6cf-14ca-44df-beb2-930ff011f297
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fd698727cba25f15a12a331f847e7f8436d3d54e
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926679"
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

#### <a name="output"></a>Выходные данные

Возвращаемые выходные значения могут быть:

| Состояние | Описание |
| --------------- | ----------- |
| Поставлено в очередь | Задание ожидает запуска. |
| Соединение | Служба BITS свяжется с сервером. |
| Передача | BITS передает данные. |
| Передаются | Служба BITS успешно передала все файлы в задании. |
| Приостановлена | Задание приостановлено. |
| Ошибка | Произошла неустранимая ошибка; Повторная попытка перемещения не выполняется. |
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
