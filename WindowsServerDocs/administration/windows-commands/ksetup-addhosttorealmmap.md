---
title: 'ksetup: аддхосттореалммап'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 237742d5-fa68-466c-b97e-636f489248ea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e6a28c6001707fac245de7136b5fb5bd38495027
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375648"
---
# <a name="ksetupaddhosttorealmmap"></a>ksetup: аддхосттореалммап



Добавляет сопоставление имени участника-службы (SPN) между указанным узлом и областью. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addhosttorealmmap <HostName> <RealmName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<имя узла >|Имя узла — это имя компьютера, оно может быть указано в качестве полного доменного имени компьютера.|
|\<Реалмнаме >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM.|

## <a name="remarks"></a>Замечания

Эта команда позволяет сопоставлять узел или несколько узлов, совместно использующих один и тот же DNS-суффикс к области.

Сопоставление записывается в реестр в **HKEY_LOCAL_MACHINE \систем\куррентконтолсет\лса\керберос\хосттореалм**.

## <a name="BKMK_Examples"></a>Примеров

В рамках настройки сферы CONTOSO сопоставьте главный компьютер IPops897 области:
```
ksetup /addhosttorealmmap IPops897 CONTOSO
```
Проверьте в реестре, что сопоставление выполняется правильно.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup:delhosttorealmmap](ksetup-delhosttorealmmap.md)
-   [Ksetup](ksetup.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)