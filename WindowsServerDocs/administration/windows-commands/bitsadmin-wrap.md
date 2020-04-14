---
title: bitsadmin wrap
description: Команды Windows для **битсадмин Wrap**, которая заключает в оболочку любую строку выходного текста, расположенную за крайней правой границей окна команд, до следующей строки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 14e57522-539d-4621-ad15-09f7a44ccab7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e754a765d94661baf24190431b455584d29991ec
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122567"
---
# <a name="bitsadmin-wrap"></a>bitsadmin wrap

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Заключает строку выходного текста, выходящего за пределы крайнего правого края окна команд, на следующую строку. Этот параметр необходимо указать перед любыми другими параметрами.

По умолчанию все коммутаторы, кроме коммутатора [монитора битсадмин](bitsadmin-monitor.md) , заключают выходной текст в оболочку.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /wrap <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ---------- |
| Job | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

В следующем примере извлекаются сведения о задании с именем *мидовнлоаджоб* и переносятся выходные данные.

```
C:\>bitsadmin /wrap /info myDownloadJob /verbose
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
