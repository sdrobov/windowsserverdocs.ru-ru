---
title: bitsadmin getowner
description: Справочная статья по команде битсадмин, которая получает владельца указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5203f84c-a879-4f31-ae3e-7ea74bd63ca5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f530952e510fdff1a30dfd7c6081e112d841f401
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926893"
---
# <a name="bitsadmin-getowner"></a>bitsadmin getowner

Отображает отображаемое имя или идентификатор GUID владельца указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getowner <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы отобразить владельца для задания с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /getowner myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
