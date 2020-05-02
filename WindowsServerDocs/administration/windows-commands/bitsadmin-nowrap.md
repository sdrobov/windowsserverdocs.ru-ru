---
title: bitsadmin nowrap
description: Справочный раздел для команды битсадмин, которая усекает любую строку выходного текста, выходящего за пределы крайнего правого края окна командной строки.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 85a47b90-783a-41e4-96f2-81f26ae8ca93
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2aac604ec3e13026e322d7cb7a9364df46266a0c
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717335"
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
