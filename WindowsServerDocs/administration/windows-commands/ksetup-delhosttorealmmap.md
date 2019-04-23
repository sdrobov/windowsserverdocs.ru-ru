---
title: ksetup:delhosttorealmmap
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: cf01edc4932fd5ec1cf98043de04286b3a100a34
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59882345"
---
# <a name="ksetupdelhosttorealmmap"></a>ksetup:delhosttorealmmap



Удаляет сопоставление службы имя участника (SPN) указанного узла и областью. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /delhosttorealmmap <HostName> <RealmName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Имя узла >|Имя узла — имя компьютера, и он может быть задана как полное доменное имя компьютера.|
|\<RealmName>|Имя области указывается как верхний регистр DNS-имя, например CORP. CONTOSO.COM.|

## <a name="remarks"></a>Примечания

Если существует узел в области (или несколько узлов для сферы) сопоставление, эта команда удаляет это сопоставление.

Сопоставление регистрируется в реестре в **HKEY_LOCAL_MACHINE\SYSTEM\CurrentContolSet\Lsa\Kerberos\HostToRealm**. Следует проверить сопоставление в реестре после с помощью следующей команды.

## <a name="BKMK_Examples"></a>Примеры

Изменение конфигурации области CONTOSO, удалите сопоставление главного компьютера IPops897 к области:
```
ksetup /delhosttorealmmap IPops897 CONTOSO
```
После выполнения этой команды, вы можете проверить в реестре что сопоставление является должным образом.

#### <a name="additional-references"></a>Дополнительная справка

-   [ksetup:addhosttorealmmap](ksetup-addhosttorealmmap.md)
-   [Ksetup](ksetup.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)