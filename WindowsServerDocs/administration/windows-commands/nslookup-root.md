---
title: nslookup root
description: Справочная статья по команде nslookup root, которая изменяет сервер по умолчанию на сервер для корневого каталога пространства имен домена системы доменных имен (DNS).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9c29edc3-ec49-43f2-bc49-86bf0612d816
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 07dbfcf401314145cb0e7553d71480072da4b574
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936287"
---
# <a name="nslookup-root"></a>nslookup root

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет сервер по умолчанию на сервер для корня пространства имен домена службы доменных имен (DNS). В настоящее время используется сервер имен ns.nic.ddn.mil. Имя корневого сервера можно изменить с помощью команды [nslookup set root](nslookup-set-root.md) .

> [!NOTE]
> Эта команда совпадает с `lserver ns.nic.ddn.mil` .

## <a name="syntax"></a>Синтаксис

```
root
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| /? | Отображение справки в командной строке. |
| /help | Отображение справки в командной строке. |

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [nslookup set root](nslookup-set-root.md)
