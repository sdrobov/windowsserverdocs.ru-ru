---
title: clean
description: Команды Windows для команды DiskPart Clean, которая удаляет все разделы или форматирование томов с диска, на котором находится фокус.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9bbe6fd3-e07e-487b-9035-910957a1d326
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d573a0480c24a2a622618197dea7dccaeddac271
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847757"
---
# <a name="clean"></a>clean

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Команда DiskPart clean удаляет все разделы или тома с диска, на котором находится фокус.

## <a name="syntax"></a>Синтаксис
```
clean [all]
```
### <a name="parameters"></a>Параметры

| Параметр |                                                        Описание                                                        |
|-----------|---------------------------------------------------------------------------------------------------------------------------|
|    all    | Указывает, что каждый сектор диска имеет значение 0, что полностью удаляет все данные, содержащиеся на диске. |

## <a name="remarks"></a>Примечания
- На дисках основной загрузочной записи (MBR) перезаписываются только сведения о разделах MBR и скрытых секторах.
- На дисках с таблицей разделов GPT сведения о секционировании GPT, включая защитный код MBR, перезаписываются. Нет сведений о скрытых секторах.
- Для выполнения этой операции необходимо выбрать диск. Используйте команду **Выбор диска** , чтобы выбрать диск и переместить фокус на него.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
  Чтобы удалить все форматирование с выбранного диска, введите:
  ```
  clean
  ```

## <a name="additional-references"></a>Дополнительные материалы
[Clear — диск](https://technet.microsoft.com/library/hh848661.aspx)
