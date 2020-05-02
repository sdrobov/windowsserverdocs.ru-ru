---
title: bitsadmin getminretrydelay
description: Справочный раздел по команде битсадмин жетминретриделай, который получает время ожидания (в секундах), в течение которого служба будет ожидать временной ошибки, прежде чем пытаться переместить файл.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a50b9d98fe0b873dc58b8e86dc672a8f4157208a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717849"
---
# <a name="bitsadmin-getminretrydelay"></a>bitsadmin getminretrydelay

Возвращает продолжительность времени в секундах, в течение которого служба будет ожидать после возникновения временной ошибки, прежде чем пытаться переместить файл.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getminretrydelay <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Для получения минимальной задержки повтора для задания с именем *мидовнлоаджоб*:

```
bitsadmin /getminretrydelay myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
