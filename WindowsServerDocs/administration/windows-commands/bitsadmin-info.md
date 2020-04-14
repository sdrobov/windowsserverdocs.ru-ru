---
title: bitsadmin info
description: Раздел команд Windows для **битсадмин info**, в котором отображаются сводные сведения об указанном задании.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5c306677-0d64-41c0-8276-5bba7750cecb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 20b8358caba3e0c07b0c985cb24e8f7bde43b06c
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123119"
---
# <a name="bitsadmin-info"></a>bitsadmin info

Отображает сводную информацию об указанном задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /info <job> [/verbose]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| /verbose | Необязательно. Предоставляет подробные сведения о каждом задании. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекаются сведения о задании с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /info myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [bitsadmin info](bitsadmin-info.md)