---
title: Инициализация HGS
ms.custom: na
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 07c40b1da829239dda5210dde0dabe485f659ae0
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403587"
---
# <a name="initialize-the-host-guardian-service-hgs"></a>Инициализация службы защиты узла (HGS)

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

При инициализации HGS необходимо указать режим, который будет использоваться HGS для измерения работоспособности защищенных узлов. Существует два взаимоисключающих варианта. Дополнительные сведения о том, какой режим следует выбрать, см. в разделе [защищенная структура и структура планирования экранированных виртуальных машин для поставщиков услуг размещения](guarded-fabric-planning-for-hosters.md).

В следующих разделах рассматриваются шаги развертывания для каждого режима.

- [Доверенный платформенный модуль аттестации (режим TPM)](guarded-fabric-initialize-hgs-tpm-mode.md)
- [Аттестация ключа узла (режим ключей)](guarded-fabric-initialize-hgs-key-mode.md)
- [Доверенная для администраторов аттестация (режим AD)](guarded-fabric-initialize-hgs-ad-mode.md)

Эти действия следует выполнить на физическом сервере.