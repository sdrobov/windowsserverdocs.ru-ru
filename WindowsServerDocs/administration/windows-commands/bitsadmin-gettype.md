---
title: bitsadmin gettype
description: Раздел команд Windows для **битсадмин GetType**, который получает тип задания для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bec16f04-3e95-4587-889e-3de6ad03c9c8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 66a1fc5b0478e1eec26557dc9a7f76d50abcb8b6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850447"
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
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="output"></a>Вывод

К выходным значениям относятся:

| Тип | Описание |
| --------------- | ----------- |
| Загрузить | Задание является загружаемым. |
| Отправка | Задание — это отправка. |
| Отправка и ответ | Задание представляет собой отправку и ответ. |
| Неизвестно | Задание имеет неизвестный тип. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается тип задания для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /gettype myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)