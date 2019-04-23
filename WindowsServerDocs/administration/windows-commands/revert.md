---
title: вернуть
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75ad40e4-502a-401e-b11e-8b31e00424b5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5bc77b17317f602d642c7a9e025b67be10ad7256
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59875115"
---
# <a name="revert"></a>вернуть



Возвращается к указанным теневого копирования тома. Это поддерживается только для теневых копий в контексте CLIENTACCESSIBLE. Эти теневые копии сохраняются и может содержать только системного поставщика. При использовании без параметров, **отменить** отображает справку в командной строке.

## <a name="syntax"></a>Синтаксис

```
revert <ShadowCopyID>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<ShadowCopyID>|Указывает идентификатор теневой копии для тома, который требуется восстановить.|

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)