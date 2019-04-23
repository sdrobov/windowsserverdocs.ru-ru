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
ms.openlocfilehash: 43b2a90eaa987e96b716e10259f75ffaf9f136a4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59832575"
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

>[!div class="nextstepaction"]
[Развертывание защищенных узлов](guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts.md)

