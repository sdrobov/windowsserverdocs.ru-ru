---
title: bitsadmin getnoprogresstimeout
description: Раздел команд Windows для **битсадмин жетнопрогресстимеаут** . Получает время в секундах, в течение которого служба пытается переместить файл после возникновения временной ошибки.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9cd9b19b-cbb4-4352-8419-978080f016b6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7dcc0e445f4cae25c27f5ff70c73f4f2f23975aa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381501"
---
# <a name="bitsadmin-getnoprogresstimeout"></a>bitsadmin getnoprogresstimeout



Возвращает продолжительность времени в секундах, в течение которого служба пытается переместить файл после возникновения временной ошибки.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetNoProgressTimeout <Job>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров

В следующем примере извлекается значение времени ожидания выполнения для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /GetNoProgressTimeout myDownloadJob
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)