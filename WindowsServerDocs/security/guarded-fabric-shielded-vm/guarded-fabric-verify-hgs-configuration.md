---
title: Проверка конфигурации HGS
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 8f01df37-f18e-4386-ae73-ecf84feaa9df
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 8098edd1eea475cea1face5541459b262364a07b
ms.sourcegitcommit: 63926404009f9e1330a4a0aa8cb9821a2dd7187e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2019
ms.locfileid: "67469544"
---
# <a name="verify-the-hgs-configuration"></a>Проверка конфигурации HGS

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016


Далее нам нужно проверить, что все работает должным образом. Чтобы сделать это, выполните следующую команду в консоль Windows PowerShell с повышенными привилегиями:

```powershell
Get-HgsTrace -RunDiagnostics
```

Так как конфигурация HGS еще не содержит сведения об узлах, которые будут в защищенной структуры, диагностика показывает, что нет узлов будут иметь возможность оценить, требуется ли успешно еще. Игнорировать этот результат и просмотреть другие сведения, предоставленные функцией диагностики.

[!INCLUDE [Guarded fabric diagnostics tool](../../../includes/guarded-fabric-diagnostics-tool.md)] 

Выполните диагностику на каждом узле в кластере HGS.

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Развертывание защищенных узлов](guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts.md)

