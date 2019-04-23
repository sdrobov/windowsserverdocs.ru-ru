---
title: ksetup:addhosttorealmmap
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 25cf258309c94f0efde980018dd5dcf3c7df4d60
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59837505"
---
# <a name="ksetupaddhosttorealmmap"></a>ksetup:addhosttorealmmap



Добавляет сопоставление службы имя участника (SPN) указанного узла и областью. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addhosttorealmmap <HostName> <RealmName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя узла >|Имя узла — имя компьютера, и он может быть задана как полное доменное имя компьютера.|
|\<RealmName>|Имя области указывается как верхний регистр DNS-имя, например CORP. CONTOSO.COM.|

## <a name="remarks"></a>Примечания

Эта команда позволяет сопоставить узел или несколько узлов, совместно использующих один и тот же суффикс DNS к области.

Сопоставление регистрируется в реестре в **HKEY_LOCAL_MACHINE\SYSTEM\CurrentContolSet\Lsa\Kerberos\HostToRealm**.

## <a name="BKMK_Examples"></a>Примеры

Как часть настройки области CONTOSO сопоставьте главного компьютера IPops897 к области:
```
ksetup /addhosttorealmmap IPops897 CONTOSO
```
Убедитесь в реестре, что сопоставление должным образом.

#### <a name="additional-references"></a>Дополнительная справка

-   [ksetup:delhosttorealmmap](ksetup-delhosttorealmmap.md)
-   [Ksetup](ksetup.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)