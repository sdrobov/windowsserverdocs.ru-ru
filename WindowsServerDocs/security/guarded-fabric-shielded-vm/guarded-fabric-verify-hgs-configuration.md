---
title: Проверка конфигурации HGS
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 8f01df37-f18e-4386-ae73-ecf84feaa9df
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: d219b7aa9ca1e17df3281fd756106a6f07864116
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386347"
---
# <a name="verify-the-hgs-configuration"></a>Проверка конфигурации HGS

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016


Далее необходимо убедиться, что все работает правильно. Для этого выполните следующую команду в консоли Windows PowerShell с повышенными привилегиями:

```powershell
Get-HgsTrace -RunDiagnostics
```

Так как конфигурация HGS еще не содержит сведений об узлах, которые будут находиться в защищенной структуре, диагностика сообщит, что ни один из узлов еще не сможет успешно выполнить аттестацию. Игнорируйте этот результат и ознакомьтесь с другими сведениями, предоставленными системой диагностики.

[!INCLUDE [Guarded fabric diagnostics tool](../../../includes/guarded-fabric-diagnostics-tool.md)] 

Запустите диагностику на каждом узле в кластере HGS.

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Развертывание защищенных узлов](guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts.md)

