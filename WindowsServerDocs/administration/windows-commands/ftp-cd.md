---
title: компакт-диск FTP
description: Справочный раздел по команде FTP CD, который изменяет рабочий каталог на удаленном компьютере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a574855a-31b4-45c6-bce2-581c7231c99b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dbeff9c2fca654120347f0f616325b700f5c9be3
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820004"
---
# <a name="ftp-cd"></a>компакт-диск FTP

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет рабочий каталог на удаленном компьютере.

## <a name="syntax"></a>Синтаксис

```
cd <remotedirectory>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| <remotedirectory> | Указывает каталог на удаленном компьютере, который необходимо изменить. |

### <a name="examples"></a>Примеры

Чтобы изменить каталог на удаленном компьютере на *документы*, введите:

```
cd Docs
```

Чтобы изменить каталог на удаленном компьютере на *возможные видеоролики*, введите:

```
cd  May Videos
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Дополнительные рекомендации по FTP](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
