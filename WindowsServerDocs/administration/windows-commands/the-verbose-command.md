---
title: verbose
description: Справочный раздел, посвященный Verbose, который отображает подробные выходные данные для указанной команды.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fcf30ae7-818f-4e7e-a083-a1812682032b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3563673d1f80167e469d98a664a6f96ca49815a1
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721375"
---
# <a name="verbose"></a>verbose

Отображает подробные выходные данные для указанной команды. Вы можете использовать **/verbose** с любыми другими выполняемыми командами WDSUTIL. Обратите внимание, что необходимо указать **/verbose** и **/прогресс** непосредственно после **WDSUTIL**.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /verbose <commands>
```

## <a name="examples"></a>Примеры

Чтобы удалить утвержденные компьютеры из базы данных автоматического добавления и отобразить подробные выходные данные, введите:
```
WDSUTIL /Verbose /progress /Delete-AutoAddDevices /Server:MyWDSServer /DeviceType:ApprovedDevices
```