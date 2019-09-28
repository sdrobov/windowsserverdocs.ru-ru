---
title: clean
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9bbe6fd3-e07e-487b-9035-910957a1d326
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f871ad1d13e06bf0cbb886ba64a52e7a55a9a797
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379320"
---
# <a name="clean"></a>clean

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Команда DiskPart clean удаляет все разделы или тома с диска, на котором находится фокус.
## <a name="syntax"></a>Синтаксис
```
clean [all]
```
## <a name="parameters"></a>Параметры

| Параметр |                                                        Описание                                                        |
|-----------|---------------------------------------------------------------------------------------------------------------------------|
|    all    | Указывает, что каждый сектор диска имеет значение 0, что полностью удаляет все данные, содержащиеся на диске. |

## <a name="remarks"></a>Примечания
- На дисках основной загрузочной записи (MBR) перезаписываются только сведения о разделах MBR и скрытых секторах.
- На дисках с таблицей разделов GPT сведения о секционировании GPT, включая защитный код MBR, перезаписываются. Нет сведений о скрытых секторах.
- Для выполнения этой операции необходимо выбрать диск. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.
  ## <a name="BKMK_examples"></a>Примеров
  Чтобы удалить все форматирование с выбранного диска, введите:
  ```
  clean
  ```

[Clear — диск](https://technet.microsoft.com/library/hh848661.aspx)
