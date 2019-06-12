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
ms.openlocfilehash: 954393126333bf04d2aa46a01089d88bc91151cb
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66447323"
---
# <a name="verify-the-hgs-configuration"></a>Проверка конфигурации HGS

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016


Далее нам нужно проверить, что все работает должным образом. Чтобы сделать это, выполните следующую команду в консоль Windows PowerShell с повышенными привилегиями:

```powershell
Get-HgsTrace -RunDiagnostics
```

Так как конфигурация HGS еще не содержит сведения об узлах, которые будут в защищенной структуры, диагностика показывает, что нет узлов будут иметь возможность оценить, требуется ли успешно еще. Игнорировать этот результат и просмотреть другие сведения, предоставленные функцией диагностики.

[!INCLUDE [Guarded fabric diagnostics tool](../../../includes/guarded-fabric-diagnostics-tool.md)] 

<!-- When a link is available for an updated troubleshooting guide, add a sentence like the following and create a link to the troubleshooting guide:
If failures did occur, please review the remediation steps provided or see the Troubleshooting Guide.
-->

Выполните диагностику на каждом узле в кластере HGS.

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Развертывание защищенных узлов](guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts.md)

