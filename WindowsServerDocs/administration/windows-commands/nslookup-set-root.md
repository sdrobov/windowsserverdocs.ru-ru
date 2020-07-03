---
title: nslookup set root
description: Справочная статья по команде nslookup set root, которая изменяет имя корневого сервера, используемого для запросов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8ad5393c-d4fd-4594-8187-576b1dcde60a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 866cc0f9c7c7e4ea99416c1be1fd8de3d374ca64
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935677"
---
# <a name="nslookup-set-root"></a>nslookup set root

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет имя корневого сервера, используемого для запросов.

> [!NOTE]
> Эта команда поддерживает команду [nslookup root](nslookup-root.md) .

## <a name="syntax"></a>Синтаксис

```
set root=<rootserver>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| ---------- | ---------- |
| `<rootserver>` | Указывает новое имя для корневого сервера. Значение по умолчанию — **ns.NIC.DDN.MIL**. |
| /? | Отображение справки в командной строке. |
| /help | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [nslookup root](nslookup-root.md)
