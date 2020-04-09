---
title: битсадмин сеткустомхеадерс
description: Раздел команд Windows для битсадмин сеткустомхеадерс, который добавляет пользовательский заголовок HTTP к запросу GET.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ed926410-80d0-46ed-9a90-f752c164bb9a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e5d97fae5f84637c80c3d1ef00aa36f09049bb17
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849617"
---
# <a name="bitsadmin-setcustomheaders"></a>битсадмин сеткустомхеадерс

Добавьте настраиваемый заголовок HTTP в запрос GET.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetCustomHeaders <Job> <Header1> <Header2> <. . .>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Header1 Header2 . . .|Пользовательские заголовки для задания|

## <a name="remarks"></a>Примечания

-   Этот параметр используется для добавления пользовательского заголовка HTTP к запросу GET, отправляемому на HTTP-сервер.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере добавляется пользовательский заголовок HTTP для задания с именем *мидовнлоаджоб*.
```
C:\>bitsadmin / SetCustomHeaders myDownloadJob Accept-encoding:deflate/gzip
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)