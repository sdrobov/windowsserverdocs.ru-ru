---
title: bitsadmin getstate
description: Раздел команд Windows для **битсадминного состояния**, который получает состояние указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1252d6cf-14ca-44df-beb2-930ff011f297
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 43cd8c8e614cce65f55b16fc5395b1d37de0cf95
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850467"
---
# <a name="bitsadmin-getstate"></a>bitsadmin getstate

Возвращает состояние указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getstate <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="output"></a>Вывод

К выходным значениям относятся:

| Состояние | Описание |
| --------------- | ----------- |
| Поставлена в очередь | Задание ожидает запуска. |
| Подключается | Служба BITS свяжется с сервером. |
| Передача | BITS передает данные. |
| Передаются | Служба BITS успешно передала все файлы в задании. |
| Suspended | Задание приостановлено. |
| Ошибка | Произошла неустранимая ошибка; Повторная попытка перемещения не выполняется. |
| Transient_Error | Произошла устранимая ошибка; Повторная попытка передачи после истечения минимальной задержки. |
| Подтверждения | Задание завершено. |
| Canceled (Отменено) | Задание отменено. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается состояние для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getstate myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
