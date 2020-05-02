---
title: bitsadmin wrap
description: Справочная информация по команде битсадмин Wrap, которая заключает в оболочку любую строку выходного текста, выходящего за пределы крайнего правого края окна команд, на следующую строку.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 14e57522-539d-4621-ad15-09f7a44ccab7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8c1c2c78fd3cc78674ef497526ba236ad058fe83
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707575"
---
# <a name="bitsadmin-wrap"></a>bitsadmin wrap

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Заключает строку выходного текста, выходящего за пределы крайнего правого края окна команд, на следующую строку. Этот параметр необходимо указать перед любыми другими параметрами.

По умолчанию все коммутаторы, кроме коммутатора [монитора битсадмин](bitsadmin-monitor.md) , заключают выходной текст в оболочку.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /wrap <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ---------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Для получения сведений о задании с именем *мидовнлоаджоб* и обертывания выходного текста:

```
bitsadmin /wrap /info myDownloadJob /verbose
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
