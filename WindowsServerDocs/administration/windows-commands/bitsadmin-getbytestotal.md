---
title: bitsadmin getbytestotal
description: Раздел команд Windows для **битсадмин жетбитестотал**, который получает размер указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 784e0bfa-7b09-4262-9104-adbc9beb479b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 84e3e0311ead0eb79f9247d4f06844ece5f20fa2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850787"
---
# <a name="bitsadmin-getbytestotal"></a>bitsadmin getbytestotal

Возвращает размер указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getbytestotal <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается размер задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getbytestotal myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)