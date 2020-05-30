---
title: lpq
description: Справочный раздел по команде lpq, отображающей состояние очереди печати на компьютере, на котором запущена программа LPD.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bb6abcc4-310a-4fa4-927b-4084b62ca02e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1ecce9b1b4255e5e769fe76b0f753226d61fa916
ms.sourcegitcommit: 29bc8740e5a8b1ba8f73b10ba4d08afdf07438b0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2020
ms.locfileid: "84222729"
---
# <a name="lpq"></a>lpq

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает состояние очереди печати на компьютере, на котором запущена управляющая программа LPR.

## <a name="syntax"></a>Синтаксис

```
lpq -S <servername> -P <printername> [-l]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| -S`<servername>` | Указывает (по имени или IP-адресу) устройство общего доступа к компьютеру или принтеру, на котором размещена очередь печати LPD, с состоянием, которое необходимо отобразить. Этот параметр является обязательным и должен быть прописным. |
| -P`<Printername>` | Указывает (по имени) принтер для очереди печати с состоянием, которое необходимо отобразить. Этот параметр является обязательным и должен быть прописным. |
| -l | Указывает, что необходимо отобразить сведения о состоянии очереди печати. |
| /? | Отображение справки в командной строке. |

### <a name="examples"></a>Примеры

Чтобы отобразить состояние очереди печати *Laserprinter1* на узле LPD в *10.0.0.45*, введите:

```
lpq -S 10.0.0.45 -P Laserprinter1
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Справочник по командам системы печати](print-command-reference.md)
