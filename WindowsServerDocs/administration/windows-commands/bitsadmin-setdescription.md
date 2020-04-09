---
title: bitsadmin setdescription
description: Раздел команд Windows для битсадмин SetDescription, который задает описание указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1e46a5dd-4637-4a2e-b88f-d3f85b177db8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a17f864e3bc3b3cdc8ba0d76d553bcfcef27d29
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849567"
---
# <a name="bitsadmin-setdescription"></a>bitsadmin setdescription

Задает описание указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetDescription <Job> <Description>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Описание|Текст, используемый для описания задания.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается описание задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /SetDescription myDownloadJob Music Downloads
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)