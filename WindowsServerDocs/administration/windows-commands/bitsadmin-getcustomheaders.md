---
title: битсадмин жеткустомхеадерс
description: Раздел команд Windows для **битсадмин жеткустомхеадерс**, который извлекает из задания пользовательские заголовки HTTP.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1f0d38d3-e865-4474-81e8-773d65c3d1cc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 80a3d1230fd541f0b986434ce373da4c8bb0c761
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850737"
---
# <a name="bitsadmin-getcustomheaders"></a>битсадмин жеткустомхеадерс

Извлекает из задания пользовательские заголовки HTTP.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getcustomheaders <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере показано получение пользовательских заголовков для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getcustomheaders myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)