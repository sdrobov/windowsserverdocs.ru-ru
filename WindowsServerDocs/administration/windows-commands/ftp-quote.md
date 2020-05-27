---
title: Цитата FTP
description: Справочный раздел по команде FTP quote, который отправляет точные аргументы на удаленный FTP-сервер.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4500a1d3-c091-42c7-a909-f61df7f2e993
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 87dd81d4feb6a5509a8609f5c479e3352d5fb7ea
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820344"
---
# <a name="ftp-quote"></a>Цитата FTP

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет точные аргументы на удаленный FTP-сервер. Возвращается один код ответа FTP.

> [!NOTE]
> Эта команда аналогична [команде FTP Literal](ftp-literal_1.md).

## <a name="syntax"></a>Синтаксис

```
quote <argument>[ ]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<argument>` | Указывает аргумент для отправки на FTP-сервер. |

### <a name="examples"></a>Примеры

Чтобы отправить команду **Quit** на удаленный FTP-сервер, введите:

```
quote quit
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Литеральная команда FTP](ftp-literal_1.md)

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))