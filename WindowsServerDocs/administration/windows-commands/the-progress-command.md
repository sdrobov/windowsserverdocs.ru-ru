---
title: progress
description: Справочная статья о ходе выполнения, которая отображает ход выполнения команды.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8ce5e77b-e13f-4ac3-948d-31770a6c7e25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9e9650a980d74f15bc0ec5c88d8df2dc93a3d8b0
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85934589"
---
# <a name="progress"></a>progress

Отображает ход выполнения команды. **/Прогресс** можно использовать с любыми другими выполняемыми командами WDSUTIL. Обратите внимание, что необходимо указать **/verbose** и **/прогресс** непосредственно после **WDSUTIL**.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /progress <commands>
```

## <a name="examples"></a>Примеры

Чтобы инициализировать сервер и отобразить ход выполнения, введите:
```
WDSUTIL /Verbose /Progress /Initialize-Server /Server:MyWDSServer /RemInst:C:\RemoteInstall
```