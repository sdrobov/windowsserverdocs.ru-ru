---
title: 'ksetup: делхосттореалммап'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3faee482-a96c-4614-86fd-aaa446643ec4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 70b54aaebc0b7b46c34c6f52e45f6583afd6c477
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375153"
---
# <a name="ksetupdelhosttorealmmap"></a>ksetup: делхосттореалммап



Удаляет сопоставление имени участника-службы (SPN) между указанным узлом и областью. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /delhosttorealmmap <HostName> <RealmName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<имя узла >|Имя узла — это имя компьютера, оно может быть указано в качестве полного доменного имени компьютера.|
|\<Реалмнаме >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM.|

## <a name="remarks"></a>Замечания

При наличии сопоставления между узлами (или несколькими узлами для области) Эта команда удаляет это сопоставление.

Сопоставление записывается в реестр в **HKEY_LOCAL_MACHINE \систем\куррентконтолсет\лса\керберос\хосттореалм**. При использовании этой команды следует проверить сопоставление в реестре.

## <a name="BKMK_Examples"></a>Примеров

При изменении конфигурации сферы CONTOSO удалите сопоставление главного компьютера IPops897 с областью:
```
ksetup /delhosttorealmmap IPops897 CONTOSO
```
После выполнения этой команды можно проверить в реестре, что сопоставление выполняется правильно.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup:addhosttorealmmap](ksetup-addhosttorealmmap.md)
-   [Ksetup](ksetup.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)