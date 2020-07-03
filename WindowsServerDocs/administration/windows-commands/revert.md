---
title: восстановить
description: Справочная статья для * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75ad40e4-502a-401e-b11e-8b31e00424b5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8d2d8bfbfa10df9776e849b1450c2fce47c097b7
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933040"
---
# <a name="revert"></a>восстановить



Возврат тома к указанной теневой копии. Это поддерживается только для теневых копий в контексте КЛИЕНТАКЦЕССИБЛЕ. Эти теневые копии являются постоянными и могут быть сделаны только поставщиком системы. Если используется без параметров, команда **отменить** отображение справки в командной строке.

## <a name="syntax"></a>Синтаксис

```
revert <ShadowCopyID>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<ShadowCopyID>|Указывает идентификатор теневой копии для восстановления тома.|

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)