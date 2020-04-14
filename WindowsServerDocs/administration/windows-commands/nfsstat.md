---
title: nfsstat
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: da7a9768-44bd-404b-97ee-c388d00dc395
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 94eb389fdd694c08dcd1d77325f145a81e59ea0f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838887"
---
# <a name="nfsstat"></a>nfsstat



**Нфсстат** можно использовать для вывода или сброса счетчиков вызовов, сделанных для сервера для NFS.

## <a name="syntax"></a>Синтаксис

```
nfsstat [-z]
```

## <a name="description"></a>Описание

При использовании без параметра **-z** программа командной строки **нфсстат** отображает количество вызовов NFS v2, NFS v3 и Mount v3, выполненных на сервере, так как счетчики были заданы как 0, как при запуске службы, так и при сбросе счетчиков с помощью **нфсстат-z**.