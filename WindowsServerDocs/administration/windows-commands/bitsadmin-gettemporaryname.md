---
title: битсадмин жеттемпораринаме
description: Раздел команд Windows для **битсадмин жеттемпораринаме**, который сообщает о временном имени файла в задании.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 68925edc-a801-4292-a812-7471c4f60fdd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6c331ecf12cb02d34c76692158c79eafbe5691c5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850457"
---
# <a name="bitsadmin-gettemporaryname"></a>битсадмин жеттемпораринаме

Сообщает имя временного файла заданного файла в задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /gettemporaryname <job> <file_index>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| file_index | Начинается с 0. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере выводится временное имя файла 2 для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /gettemporaryname myDownloadJob 1
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)