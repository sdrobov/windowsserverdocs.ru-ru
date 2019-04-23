---
title: Инициализация HGS
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: c689a1d5f69731db0cb85a884f5af2ee0230e7be
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59865455"
---
# <a name="initialize-the-host-guardian-service-hgs"></a>Инициализация службы защиты узла (HGS)

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

При инициализации HGS, необходимо указать режим, в котором HGS будет использовать для определения производительности защищенных узлов. Существует два взаимоисключающих вариантов. Справочные сведения о какой режим следует выбрать, см. в разделе [Защищенная структура и экранированных виртуальных Машин руководство по планированию для поставщиков услуг размещения](guarded-fabric-planning-for-hosters.md).

В следующих темах рассмотрены этапы развертывания для каждого режима:

- [Аттестация доверенного платформенного МОДУЛЯ (TPM режим)](guarded-fabric-initialize-hgs-tpm-mode.md)
- [Аттестация ключей узла (ключ режим)](guarded-fabric-initialize-hgs-key-mode.md)
- [Аттестацию с доверием администратора (режим AD)](guarded-fabric-initialize-hgs-ad-mode.md)

Это следует выполнить на физическом сервере.