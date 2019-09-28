---
title: bitsadmin complete
description: Раздел команд Windows для **битсадмин завершен** — завершает задание. Загруженные файлы недоступны, пока вы не используете этот параметр.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5e86677-8f7b-43b3-929e-97706c57e7f1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d5a1dc5dbbf2d5b3207b5423f338e0caf4412599
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381816"
---
# <a name="bitsadmin-complete"></a>bitsadmin complete

Завершает задание. Загруженные файлы недоступны, пока вы не используете этот параметр. Используйте этот параметр после перемещения задания в состояние "передано". В противном случае будут доступны только файлы, которые были успешно переданы.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /complete <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

При передаче состояния задания служба BITS успешно передала все файлы в задании. Однако файлы недоступны до тех пор, пока не будет использован параметр **/комплете** . Если несколько заданий используют *мидовнлоаджоб* в качестве имени, необходимо заменить *мидовнлоаджоб* на GUID задания для уникальной идентификации задания.
```
C:\>bitsadmin /complete myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)