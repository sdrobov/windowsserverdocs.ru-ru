---
title: bitsadmin nowrap
description: Справочная статья по команде битсадмин "без переноса", которая усекает любую строку выходного текста, выходящего за пределы крайнего правого края окна командной строки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 85a47b90-783a-41e4-96f2-81f26ae8ca93
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f8f55faeea79e5f2cf02fde0732ed82ae13e902f
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923025"
---
# <a name="bitsadmin-nowrap"></a>bitsadmin nowrap

Усекает любую строку выходного текста, выходящую за пределы крайнего правого края окна командной строки. По умолчанию все параметры, кроме коммутатора **монитора** , заключают выходные данные в оболочку. Укажите параметр "не **переносить** " перед другими параметрами.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /nowrap
```

## <a name="examples"></a>Примеры

Чтобы получить состояние для задания с именем *мидовнлоаджоб* , не заключив в оболочку выходные данные:

```
bitsadmin /nowrap /getstate myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
