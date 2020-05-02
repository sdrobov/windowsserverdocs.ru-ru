---
title: bitsadmin listfiles
description: Справочный раздел для команды битсадмин листфилес, в которой перечислены файлы в указанном задании.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ad0d1eaa-3bd8-45e5-8f72-4da7366f0d59
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6826c1ec2f624a06d11fedcb8ca9f14d86b7ec27
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717420"
---
# <a name="bitsadmin-listfiles"></a>bitsadmin listfiles

Перечисляет файлы в указанном задании.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /listfiles <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить список файлов для задания с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /listfiles myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
