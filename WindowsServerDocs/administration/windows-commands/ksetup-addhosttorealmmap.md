---
title: 'ksetup: аддхосттореалммап'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 237742d5-fa68-466c-b97e-636f489248ea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1ee8f434482b0658194daed46b62f6f7f70abae1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841847"
---
# <a name="ksetupaddhosttorealmmap"></a>ksetup: аддхосттореалммап



Добавляет сопоставление имени участника-службы (SPN) между указанным узлом и областью. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addhosttorealmmap <HostName> <RealmName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<имя узла >|Имя узла — это имя компьютера, оно может быть указано в качестве полного доменного имени компьютера.|
|\<Реалмнаме >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM.|

## <a name="remarks"></a>Примечания

Эта команда позволяет сопоставлять узел или несколько узлов, совместно использующих один и тот же DNS-суффикс к области.

Сопоставление записывается в реестр в **HKEY_LOCAL_MACHINE \систем\куррентконтолсет\лса\керберос\хосттореалм**.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

В рамках настройки сферы CONTOSO сопоставьте главный компьютер IPops897 области:
```
ksetup /addhosttorealmmap IPops897 CONTOSO
```
Проверьте в реестре, что сопоставление выполняется правильно.

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup:delhosttorealmmap](ksetup-delhosttorealmmap.md)
-   [Ksetup](ksetup.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)