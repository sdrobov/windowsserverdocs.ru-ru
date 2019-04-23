---
title: clean
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 6e7d7613784f3e599005b25259f70466db60e626
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59877435"
---
# <a name="clean"></a>clean

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Команды Diskpart очистки удаляет все разделы или тома на диске с фокусом.
## <a name="syntax"></a>Синтаксис
```
clean [all]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|all|Указывает, что каждый сектор на диске устанавливается равным нулю, который полностью удаляет все данные, содержащиеся на диске.|
## <a name="remarks"></a>Примечания
-   На основной загрузочной записью (MBR) будут перезаписаны только MBR, секционирование и скрытые сектора информацию.
-   На дисках таблица разделов GUID (gpt) сведения, включая защитную MBR разделов gpt перезаписывается. Нет данных скрытые сектора.
-   Для успешного выполнения этой операции необходимо выбрать диск. Используйте **выберите диск** команду, чтобы выбрать диск и перетянуть внимание к нему.
## <a name="BKMK_examples"></a>Примеры
Чтобы удалить все форматирование для выбранного диска, введите следующую команду:
```
clean
```

[Clear-Disk](https://technet.microsoft.com/library/hh848661.aspx)
