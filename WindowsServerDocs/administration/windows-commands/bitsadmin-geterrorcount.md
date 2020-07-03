---
title: bitsadmin geterrorcount
description: Справочная статья по команде битсадмин жетерроркаунт, которая извлекает количество раз, когда указанное задание создало временную ошибку.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8840ae78-52b0-4c7e-b592-0547359a237e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 90eaa150f2decba4bbee693ac117cd269d5a7c97
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923059"
---
# <a name="bitsadmin-geterrorcount"></a>bitsadmin geterrorcount

Извлекает число раз, когда указанное задание создало временную ошибку.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /geterrorcount <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить сведения о количестве ошибок для задания с именем *мидовнлоаджоб*:

```
bitsadmin /geterrorcount myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
