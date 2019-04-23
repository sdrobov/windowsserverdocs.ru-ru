---
title: nfsstat
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da7a9768-44bd-404b-97ee-c388d00dc395
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9db8b903d4c3681b2b3bae3424f8af83696ae2c7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59853295"
---
# <a name="nfsstat"></a>nfsstat



Можно использовать **nfsstat** для отображения или сбросить количество вызовов на сервер для NFS.

## <a name="syntax"></a>Синтаксис

```
nfsstat [-z]
```

## <a name="description"></a>Описание

При использовании без **- z** параметр, **nfsstat** командной строки служебная программа отображает количество NFS версии 2, NFS V3 и вызовы V3 подключения, выполненный к серверу, так как счетчики было присвоено значение 0, либо если службы к работе или сброса счетчиков с помощью **nfsstat - z**.