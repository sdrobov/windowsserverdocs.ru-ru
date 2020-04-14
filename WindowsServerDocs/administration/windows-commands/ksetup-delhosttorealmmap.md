---
title: 'ksetup: делхосттореалммап'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3faee482-a96c-4614-86fd-aaa446643ec4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 85e9f6b4a9f1c9050ed843f3837a2bd87aaf6eae
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841737"
---
# <a name="ksetupdelhosttorealmmap"></a>ksetup: делхосттореалммап



Удаляет сопоставление имени участника-службы (SPN) между указанным узлом и областью. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /delhosttorealmmap <HostName> <RealmName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<имя узла >|Имя узла — это имя компьютера, оно может быть указано в качестве полного доменного имени компьютера.|
|\<Реалмнаме >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM.|

## <a name="remarks"></a>Примечания

При наличии сопоставления между узлами (или несколькими узлами для области) Эта команда удаляет это сопоставление.

Сопоставление записывается в реестр в **HKEY_LOCAL_MACHINE \систем\куррентконтолсет\лса\керберос\хосттореалм**. При использовании этой команды следует проверить сопоставление в реестре.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

При изменении конфигурации сферы CONTOSO удалите сопоставление главного компьютера IPops897 с областью:
```
ksetup /delhosttorealmmap IPops897 CONTOSO
```
После выполнения этой команды можно проверить в реестре, что сопоставление выполняется правильно.

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup:addhosttorealmmap](ksetup-addhosttorealmmap.md)
-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)