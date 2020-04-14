---
title: подробный
description: Раздел команд Windows для получения подробных сведений, в котором отображаются подробные выходные данные для указанной команды.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fcf30ae7-818f-4e7e-a083-a1812682032b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f67a4fe99a5051e8844e6386d87911946a808c1e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832847"
---
# <a name="verbose"></a>подробный

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