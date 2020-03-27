---
title: Дополнительные свойства NIC
description: Управлять сетевыми картами и всеми функциями можно с помощью Windows PowerShell или панели управления сетью.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 0cafb1cc-5798-42f5-89b6-3ffe7ac024ba
manager: dougkim
ms.author: lizross
author: eross-msft
ms.date: 09/20/2018
ms.openlocfilehash: 78d320f4309d60fa0396cbd723feafa07a65aea1
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80317004"
---
# <a name="nic-advanced-properties"></a>Дополнительные свойства NIC

Управлять сетевыми картами и всеми функциями можно через Windows PowerShell с помощью командлета [NetAdapter](https://docs.microsoft.com/powershell/module/netadapter/?view=win10-ps&viewFallbackFrom=winserverr2-ps) .  Также можно управлять сетевыми картами и всеми функциями с помощью панели управления сетью (ncpa. cpl). 

1. В **Windows PowerShell**выполните командлет `Get‑NetAdapterAdvancedProperties` для двух различных способов создания или модели сетевых карт.

   ![Get-Нетадаптерадванцедпроперти M1](../../media/network-offload-and-optimization/Get-NetAdapterAdvancedProperty-m1.png)

   ![Get-Нетадаптерадванцедпроперти C1](../../media/network-offload-and-optimization/Get-NetAdapterAdvancedProperty-c1.png)

   В этих двух списках дополнительных свойств сетевого адаптера есть сходства и различия.

2. На **панели управления сетью** (ncpa. cpl) выполните следующие действия.

   а) Щелкните сетевую карту правой кнопкой мыши.

   ![Диалоговое окно "Сетевые подключения"](../../media/network-offload-and-optimization/network-connections-dialog.png)

   б. В диалоговом окне Свойства нажмите кнопку **настроить**.

    ![Свойства C1](../../media/network-offload-and-optimization/c1-properties.png)

   в. Перейдите на вкладку **Дополнительно** , чтобы просмотреть дополнительные свойства.<p>Элементы в этом списке сопоставляются с элементами в выходных данных `Get-NetAdapterAdvancedProperties`.

   ![Свойства сетевого адаптера Chelsio](../../media/network-offload-and-optimization/chelsio-network-adapter-properties.png)

---
