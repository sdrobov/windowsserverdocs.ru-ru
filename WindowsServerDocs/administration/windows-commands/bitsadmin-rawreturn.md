---
title: bitsadmin rawreturn
description: Справочный раздел по команде битсадмин равретурн, который возвращает данные, подходящие для синтаксического анализа.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bbe97130-26f6-4cdd-84f1-baf530ce38b7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: af465bb9f51ab6f43980c43bf2be1f5158429a82
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717086"
---
# <a name="bitsadmin-rawreturn"></a>bitsadmin rawreturn

Возвращает данные, подходящие для синтаксического анализа. Как правило, эта команда используется совместно с параметрами **/CREATE** и **/Get*** для получения только значения. Этот параметр необходимо указать перед другими коммутаторами.

> [!NOTE]
> Эта команда удаляет символы новой строки и форматирование из выходных данных.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /rawreturn
```

## <a name="examples"></a>Примеры

Чтобы получить необработанные данные для состояния задания с именем *мидовнлоаджоб*:

```
bitsadmin /rawreturn /getstate myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
