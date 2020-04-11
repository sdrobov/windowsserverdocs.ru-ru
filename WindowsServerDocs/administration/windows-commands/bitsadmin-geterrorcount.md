---
title: bitsadmin geterrorcount
description: Раздел команд Windows для **битсадмин жетерроркаунт**, который извлекает количество раз, когда указанное задание создало временную ошибку.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8840ae78-52b0-4c7e-b592-0547359a237e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ef0bf043517d4edfa8d72888746ca5d9c92ecc21
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123135"
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
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается информация о количестве ошибок для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /geterrorcount myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)