---
title: Команда Progress
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ce5e77b-e13f-4ac3-948d-31770a6c7e25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 841d9103354e3162489492ba7dd97e726b37d37d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370178"
---
# <a name="the-progress-command"></a>Команда Progress



Показывает ход выполнения команды. **/Прогресс** можно использовать с любыми другими выполняемыми командами WDSUTIL. Обратите внимание, что необходимо указать **/verbose** и **/прогресс** непосредственно после **WDSUTIL**.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /progress <commands>
```

## <a name="examples"></a>Примеры

Чтобы инициализировать сервер и отобразить ход выполнения, введите:
```
WDSUTIL /Verbose /Progress /Initialize-Server /Server:MyWDSServer /RemInst:"C:\RemoteInstall"
```