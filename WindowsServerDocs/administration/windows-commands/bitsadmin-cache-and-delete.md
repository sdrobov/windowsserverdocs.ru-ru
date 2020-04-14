---
title: кэш битсадмин и удаление
description: Команды Windows для **кэша битсадмин и удаления**, удаляющие определенную запись кэша.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 22540273-55a5-46ea-869b-6df2aa6808a1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0fd7f1db83a62dd9c1085d6afdcf509c1c3ac8cf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850947"
---
# <a name="bitsadmin-cache-and-delete"></a>кэш битсадмин и удаление

Удаляет определенную запись кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cache /delete recordID
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| recordID | Идентификатор GUID, связанный с записью кэша. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере удаляется запись кэша с RecordID {6511FB02-E195-40A2-B595-E8E2F8F47702}.

```
C:\>bitsadmin /cache /delete {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)