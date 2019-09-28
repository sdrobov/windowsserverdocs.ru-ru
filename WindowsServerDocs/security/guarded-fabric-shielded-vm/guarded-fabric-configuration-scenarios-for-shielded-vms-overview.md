---
title: Развертывание экранированных виртуальных машин
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 5d1a06c9-24e1-4e14-9c9a-efb2adbfeddd
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: f7892dabb028b99cb4cb1c9045764a8e36aba7dc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386774"
---
# <a name="deploy-shielded-vms"></a>Развертывание экранированных виртуальных машин


>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

В следующих разделах описывается, как клиент может работать с экранированными виртуальными машинами.

1. Используемых [Создайте диск шаблона Windows](guarded-fabric-create-a-shielded-vm-template.md) или [Создайте диск шаблона Linux](guarded-fabric-create-a-linux-shielded-vm-template.md). Диск шаблона может быть создан либо клиентом, либо поставщиком услуг размещения. 

2. Используемых [Преобразование существующей виртуальной машины Windows в экранированную](guarded-fabric-vm-shielding-helper-vhd.md). 

3. [Создание данных экранирования для определения экранированной виртуальной машины](guarded-fabric-tenant-creates-shielding-data.md).

    Описание и схема файла данных экранирования см. в разделе [что такое данные экранирования и почему это необходимо?](guarded-fabric-and-shielded-vms.md#what-is-shielding-data-and-why-is-it-necessary)
    
    Сведения о создании файла ответов для включения в экранированный файл данных см. в статье [экранированные виртуальные машины. Создайте файл ответов с помощью функции New-шиелдингдатаансверфиле](guarded-fabric-sample-unattend-xml-file.md).

4. Создайте экранированную виртуальную машину.
 
    - Использование **Windows Azure Pack**: [Развертывание экранированной виртуальной машины с помощью Windows Azure Pack](guarded-fabric-shielded-vm-windows-azure-pack.md)

    - Использование **Virtual Machine Manager**: [Развертывание экранированной виртуальной машины с помощью Virtual Machine Manager](guarded-fabric-tenant-deploys-shielded-vm-using-vmm.md)

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Создание шаблона экранированной виртуальной машины](guarded-fabric-create-a-shielded-vm-template.md)

## <a name="see-also"></a>См. также

- [Защищенная структура и экранированные виртуальные машины](guarded-fabric-and-shielded-vms-top-node.md)
