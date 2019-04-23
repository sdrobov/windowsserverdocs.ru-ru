---
title: Развертывание экранированных виртуальных машин
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 5d1a06c9-24e1-4e14-9c9a-efb2adbfeddd
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: fa6da3f4a98686f83fff3937c2dc44fd4d623fe3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59871015"
---
# <a name="deploy-shielded-vms"></a>Развертывание экранированных виртуальных машин


>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

Следующие разделы описывают, как клиент может работать с экранированных виртуальных машин.

1. (Необязательно) [Создание диска шаблона Windows](guarded-fabric-create-a-shielded-vm-template.md) или [Создание диска шаблона Linux](guarded-fabric-create-a-linux-shielded-vm-template.md). Можно создать диск шаблона клиента или поставщика услуг размещения. 

2. (Необязательно) [Преобразовать существующую виртуальную Машину Windows для экранированной виртуальной Машины](guarded-fabric-vm-shielding-helper-vhd.md). 

3. [Создания данных экранирования для определения экранированной виртуальной Машины](guarded-fabric-tenant-creates-shielding-data.md).

    Описание и схему файл данных экранирования, см. в разделе [что данных экранирования и зачем это необходимо?](guarded-fabric-and-shielded-vms.md#what-is-shielding-data-and-why-is-it-necessary)
    
    Сведения о создании файла ответов, чтобы включить в файл экранированных данных, см. в разделе [экранированных виртуальных машин — Создание файла ответов с помощью функции New-ShieldingDataAnswerFile](guarded-fabric-sample-unattend-xml-file.md).

4. Создание экранированной виртуальной Машины:
 
    - С помощью **Windows Azure Pack**: [Развертывание экранированной виртуальной Машины с помощью Windows Azure Pack](guarded-fabric-shielded-vm-windows-azure-pack.md)

    - С помощью **Virtual Machine Manager**: [Развертывание экранированной виртуальной Машины с помощью Virtual Machine Manager](guarded-fabric-tenant-deploys-shielded-vm-using-vmm.md)

## <a name="next-step"></a>Дальнейшие действия

>[!div class="nextstepaction"]
[Создать шаблон экранированной виртуальной Машины](guarded-fabric-create-a-shielded-vm-template.md)

## <a name="see-also"></a>См. также

- [Защищенная структура и экранированные виртуальные машины](guarded-fabric-and-shielded-vms-top-node.md)
