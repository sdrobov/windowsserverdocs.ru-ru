---
title: bitsadmin getfilestotal
description: Справочная статья по команде битсадмин жетфилестотал, которая получает количество файлов в указанном задании.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c5de113e-f29c-4cd3-9392-0e300018d516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7592f783d17e31fe8a1e7fbf82cb41e20171c9fd
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928285"
---
# <a name="bitsadmin-getfilestotal"></a>bitsadmin getfilestotal

Извлекает количество файлов в указанном задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getfilestotal <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить количество файлов, включаемых в задание с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /getfilestotal myDownloadJob
```

## <a name="see-also"></a>См. также

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
