---
title: Дополнительные свойства NIC
description: Вы можете управлять сетевыми картами и все функции с помощью Windows PowerShell или панели управления.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 0cafb1cc-5798-42f5-89b6-3ffe7ac024ba
manager: dougkim
ms.author: pashort
author: shortpatti
ms.date: 09/20/2018
ms.openlocfilehash: d1a5fb57bf71fd981e001cfd9ac595ab5bc3cfc5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59819905"
---
# <a name="nic-advanced-properties"></a>Дополнительные свойства NIC

Вы можете управлять сетевыми картами и все функции с помощью Windows PowerShell, используя [NetAdapter](https://docs.microsoft.com/powershell/module/netadapter/?view=win10-ps&viewFallbackFrom=winserverr2-ps) командлета.  Можно также управлять сетевыми картами и все функции, с помощью панели управления сетью (ncpa.cpl). 

1. В **Windows PowerShell**, запустите `Get‑NetAdapterAdvancedProperties` командлета для двух разных изготовитель/модель сетевых адаптеров.

   ![Get-NetAdapterAdvancedProperty m1](../../media/network-offload-and-optimization/Get-NetAdapterAdvancedProperty-m1.png)

   ![Get-NetAdapterAdvancedProperty c1](../../media/network-offload-and-optimization/Get-NetAdapterAdvancedProperty-c1.png)

   Существуют сходства и различия в этих двух Сетевых дополнительные свойства перечислены.

2. В **панели управления** (ncpa.cpl), выполните следующие действия:

   1. и щелкните правой кнопкой мыши сетевой карты.

   ![Диалоговое окно подключения к сети](../../media/network-offload-and-optimization/network-connections-dialog.png)

   2. В диалоговом окне свойств щелкните **Настройка**.

    ![Свойства C1](../../media/network-offload-and-optimization/c1-properties.png)

   В. Нажмите кнопку **Дополнительно** вкладку для просмотра дополнительных свойств.<p>Сопоставляет элементы в этом списке элементов в `Get-NetAdapterAdvancedProperties` выходных данных.

   ![Свойства Chelsio сетевого адаптера](../../media/network-offload-and-optimization/chelsio-network-adapter-properties.png)

---