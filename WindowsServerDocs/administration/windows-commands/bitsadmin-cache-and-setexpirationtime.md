---
title: кэш битсадмин и сетекспиратионтиме
description: Команды Windows для **кэша битсадмин и сетекспиратионтиме**, которые задают время истечения срока действия кэша.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bf283a0a8b94fd55c591609e3dcd1d127a2be81a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850887"
---
>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

# <a name="bitsadmin-cache-and-setexpirationtime"></a>кэш битсадмин и сетекспиратионтиме

Задает срок действия кэша.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /cache /setexpirationtime secs
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| сек | Количество секунд до истечения срока действия кэша. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере срок действия кэша истекает через 60 секунд.

```
C:\>bitsadmin /cache / setexpirationtime 60
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
