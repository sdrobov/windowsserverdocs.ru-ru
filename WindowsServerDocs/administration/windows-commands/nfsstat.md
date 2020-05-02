---
title: nfsstat
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: da7a9768-44bd-404b-97ee-c388d00dc395
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4e2c02fdfeb9923993a1d4471862a6c8487c9d86
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723755"
---
# <a name="nfsstat"></a>nfsstat



**Нфсстат** можно использовать для вывода или сброса счетчиков вызовов, сделанных для сервера для NFS.

## <a name="syntax"></a>Синтаксис

```
nfsstat [-z]
```

## <a name="description"></a>Описание

При использовании без параметра **-z** программа командной строки **нфсстат** отображает количество вызовов NFS v2, NFS v3 и Mount v3, выполненных на сервере, так как счетчики были заданы как 0, как при запуске службы, так и при сбросе счетчиков с помощью **нфсстат-z**.