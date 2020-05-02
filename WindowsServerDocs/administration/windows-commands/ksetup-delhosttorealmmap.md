---
title: 'ksetup: делхосттореалммап'
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3faee482-a96c-4614-86fd-aaa446643ec4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2b6b14785f254a63f0e16fcd16f1cd464a2d69c8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724695"
---
# <a name="ksetupdelhosttorealmmap"></a>ksetup: делхосттореалммап



Удаляет сопоставление имени участника-службы (SPN) между указанным узлом и областью.

## <a name="syntax"></a>Синтаксис

```
ksetup /delhosttorealmmap <HostName> <RealmName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя узла>|Имя узла — это имя компьютера, оно может быть указано в качестве полного доменного имени компьютера.|
|\<Реалмнаме>|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM.|

## <a name="remarks"></a>Примечания

При наличии сопоставления между узлами (или несколькими узлами для области) Эта команда удаляет это сопоставление.

Сопоставление записывается в реестр в **HKEY_LOCAL_MACHINE \систем\куррентконтолсет\лса\керберос\хосттореалм**. При использовании этой команды следует проверить сопоставление в реестре.

## <a name="examples"></a>Примеры

При изменении конфигурации сферы CONTOSO удалите сопоставление главного компьютера IPops897 с областью:
```
ksetup /delhosttorealmmap IPops897 CONTOSO
```
После выполнения этой команды можно проверить в реестре, что сопоставление выполняется правильно.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Ksetup:addhosttorealmmap](ksetup-addhosttorealmmap.md)
-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)