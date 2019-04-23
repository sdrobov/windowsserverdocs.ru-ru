---
author: shortpatti
ms.author: pashort
ms.date: 10/02/2018
ms.prod: windows-server-threshold
ms:topic: include
ms.openlocfilehash: 761deb136ebd4ec22dfeebc47b4eeb7650594d89
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863715"
---
Порт Hyper-V группы сетевых Адаптеров, настроенных на узлах Hyper-V предоставляют независимые MAC-адреса виртуальных машин.  Виртуальные машины MAC-адрес или виртуальная машина перенесена, подключенный к коммутатору Hyper-V, может использоваться для разделения сетевого трафика между членами группы сетевых КАРТ. Невозможно настроить группы сетевых Адаптеров, создаваемого в виртуальных машинах с помощью режим балансировки нагрузки портов Hyper-V. Вместо этого используйте режим хэш адреса. 