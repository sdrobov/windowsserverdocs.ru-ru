---
title: convert
description: Справочная статья по команде Convert, которая преобразует диск с одного типа диска в другой.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ae151297-af21-4701-bd69-21d775518e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f93f2b16838a6f54af3f28b7e0883808a6cd013a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928902"
---
# <a name="convert"></a>convert

Преобразует диск с одного типа диска в другой.

## <a name="syntax"></a>Синтаксис

```
convert basic
convert dynamic
convert gpt
convert mbr
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| [Команда CONVERT Basic](convert-basic.md) | Преобразовывает пустой динамический диск в базовый. |
| [преобразовать динамическую команду](convert-dynamic.md) | Преобразует базовый диск в динамический диск. |
| [Команда CONVERT GPT](convert-gpt.md) | Преобразует пустой базовый диск с стилем разделов основной загрузочной записи (MBR) в базовый диск с стилем разделов GPT. |
| [Команда CONVERT MBR](convert-mbr.md) | Преобразует пустой базовый диск со стилем разделов GPT в базовый диск с стилем разделов основной загрузочной записи (MBR). |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
