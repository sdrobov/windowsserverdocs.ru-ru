---
title: Тип FTP
description: Справочный раздел по команде типа FTP, который задает или отображает тип перемещения файла.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e96dcd4-08f8-4e7b-90b7-1e1761fea4c7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 02b6d5b4bd7944c9f4126ba4877360de02586cfb
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820274"
---
# <a name="ftp-type"></a>Тип FTP

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает или отображает тип перемещения файла. Команда **FTP** поддерживает как ASCII (по умолчанию), так и типы перемещения файлов с двоичными изображениями:

- При передаче текстовых файлов рекомендуется использовать ASCII. В режиме ASCII выполняется преобразование символов в стандартную сетевую кодировку и из нее. Например, символы конца строки при необходимости преобразуются в зависимости от целевой операционной системы.

- При передаче исполняемых файлов рекомендуется использовать двоичный формат. В двоичном режиме файлы передаются в однобайтовых единицах.

## <a name="syntax"></a>Синтаксис

```
type [<typename>]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `[<typename>]` | Определяет тип передачи файла. Если этот параметр не указан, отображается текущий тип.|

### <a name="examples"></a>Примеры

Чтобы задать тип перемещения файла ASCII, введите:

```
type ascii
```

Чтобы задать тип файла для перемещения binary, введите:

```
type binary
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
