---
title: bitsadmin rawreturn
description: Справочная статья по команде битсадмин равретурн, которая возвращает данные, подходящие для синтаксического анализа.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bbe97130-26f6-4cdd-84f1-baf530ce38b7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1b537b21678c100364406d4c59eaa02efd143e21
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926464"
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
