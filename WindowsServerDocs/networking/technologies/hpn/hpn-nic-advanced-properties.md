---
title: Дополнительные свойства NIC
description: Управлять сетевыми картами и всеми функциями можно с помощью Windows PowerShell или панели управления сетью.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 0cafb1cc-5798-42f5-89b6-3ffe7ac024ba
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/20/2018
ms.openlocfilehash: 1395cefca5d9ef696eed3f2735334954b9ee02a5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405717"
---
# <a name="nic-advanced-properties"></a>Дополнительные свойства NIC

Управлять сетевыми картами и всеми функциями можно через Windows PowerShell с помощью командлета [NetAdapter](https://docs.microsoft.com/powershell/module/netadapter/?view=win10-ps&viewFallbackFrom=winserverr2-ps) .  Также можно управлять сетевыми картами и всеми функциями с помощью панели управления сетью (ncpa. cpl). 

1. В **Windows PowerShell**выполните командлет `Get‑NetAdapterAdvancedProperties` для двух различных способов создания или модели сетевых карт.

   ![Get-Нетадаптерадванцедпроперти M1](../../media/network-offload-and-optimization/Get-NetAdapterAdvancedProperty-m1.png)

   ![Get-Нетадаптерадванцедпроперти C1](../../media/network-offload-and-optimization/Get-NetAdapterAdvancedProperty-c1.png)

   В этих двух списках дополнительных свойств сетевого адаптера есть сходства и различия.

2. На **панели управления сетью** (ncpa. cpl) выполните следующие действия.

   1\. Щелкните сетевую карту правой кнопкой мыши.

   ![Диалоговое окно "Сетевые подключения"](../../media/network-offload-and-optimization/network-connections-dialog.png)

   2\. В диалоговом окне Свойства нажмите кнопку **настроить**.

    ![Свойства C1](../../media/network-offload-and-optimization/c1-properties.png)

   В. Перейдите на вкладку **Дополнительно** , чтобы просмотреть дополнительные свойства.<p>Элементы в этом списке сопоставляются с элементами в выходных данных `Get-NetAdapterAdvancedProperties`.

   ![Свойства сетевого адаптера Chelsio](../../media/network-offload-and-optimization/chelsio-network-adapter-properties.png)

---
