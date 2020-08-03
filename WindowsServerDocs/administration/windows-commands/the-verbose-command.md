---
title: Использование команды verbose
description: Справочная статья для verbose, которая отображает подробные выходные данные для указанной команды.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fcf30ae7-818f-4e7e-a083-a1812682032b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b53defe143ab9a5c068d5012ed60b66e29398004
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2020
ms.locfileid: "87519613"
---
# <a name="using-the-verbose-command"></a>Использование команды verbose

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