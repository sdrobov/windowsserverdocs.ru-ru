---
title: Развертывание экранированных виртуальных машин
ms.prod: windows-server
ms.topic: article
ms.assetid: 5d1a06c9-24e1-4e14-9c9a-efb2adbfeddd
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: f4550f8a92330c8f483e332ab9e4b36fda853b0a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856867"
---
# <a name="deploy-shielded-vms"></a>Развертывание экранированных виртуальных машин


>Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

В следующих разделах описывается, как клиент может работать с экранированными виртуальными машинами.

1. Используемых [Создайте диск шаблона Windows](guarded-fabric-create-a-shielded-vm-template.md) или [Создайте диск шаблона Linux](guarded-fabric-create-a-linux-shielded-vm-template.md). Диск шаблона может быть создан либо клиентом, либо поставщиком услуг размещения. 

2. Используемых [Преобразование существующей виртуальной машины Windows в экранированную](guarded-fabric-vm-shielding-helper-vhd.md). 

3. [Создание данных экранирования для определения экранированной виртуальной машины](guarded-fabric-tenant-creates-shielding-data.md).

    Описание и схема файла данных экранирования см. в разделе [что такое данные экранирования и почему это необходимо?](guarded-fabric-and-shielded-vms.md#what-is-shielding-data-and-why-is-it-necessary)
    
    Сведения о создании файла ответов для включения в экранированный файл данных см. в статье [экранированные виртуальные машины. Создайте файл ответов с помощью функции New-шиелдингдатаансверфиле](guarded-fabric-sample-unattend-xml-file.md).

4. Создайте экранированную виртуальную машину.
 
    - Использование **Windows Azure Pack**: [развертывание экранированной виртуальной машины с помощью Windows Azure Pack](guarded-fabric-shielded-vm-windows-azure-pack.md)

    - Использование **Virtual Machine Manager**: [развертывание экранированной виртуальной машины с помощью Virtual Machine Manager](guarded-fabric-tenant-deploys-shielded-vm-using-vmm.md)

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Создание шаблона экранированной виртуальной машины](guarded-fabric-create-a-shielded-vm-template.md)

## <a name="see-also"></a>См. также:

- [Защищенная структура и экранированные виртуальные машины](guarded-fabric-and-shielded-vms-top-node.md)
