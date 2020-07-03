---
title: bitsadmin wrap
description: Справочная статья по команде битсадмин Wrap, которая заключает в оболочку любую строку выходного текста, выходящего за пределы крайнего правого края окна команд, на следующую строку.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 14e57522-539d-4621-ad15-09f7a44ccab7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e47f5e38555eb2464d3febf5f958ce5a6af20452
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927251"
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
