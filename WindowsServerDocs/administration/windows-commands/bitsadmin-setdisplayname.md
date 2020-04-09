---
title: bitsadmin setdisplayname
description: Раздел команд Windows для битсадмин сетдисплайнаме, который задает отображаемое имя указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 601c5b406132e70fb7d4facb97329f7456002bb4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849547"
---
# <a name="bitsadmin-setdisplayname"></a>bitsadmin setdisplayname

Задает отображаемое имя указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetDisplayName <Job> <DisplayName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|DisplayName|Текст, используемый для отображаемого имени указанного задания.|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере задается отображаемое имя для задания с именем *мидовнлоаджоб* в *myDownloadJob2*.
```
C:\>bitsadmin /SetDisplayName myDownloadJob Download Music Job
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)