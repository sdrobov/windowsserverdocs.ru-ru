---
title: Включить все виртуальные сетевые адаптеры, настроенные для виртуальной машины
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: fcd350b7-4240-4359-aadd-93e7ac4d314e
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: bdca25be4af41d0f6ddfafe885f8c2b1301b71fb
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393646"
---
# <a name="enable-all-virtual-network-adapters-configured-for-a-virtual-machine"></a>Включить все виртуальные сетевые адаптеры, настроенные для виртуальной машины

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и сканировании см. в разделе [Анализатор соответствия рекомендациям](https://go.microsoft.com/fwlink/?LinkId=122786).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Предупреждение|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблемы  
  
*На виртуальной машине может быть отключен один или несколько сетевых адаптеров.*  
  
## <a name="impact"></a>Влияние  
  
*Следующие виртуальные машины могут не иметь подключения к сети:*  
  
@no__t 0list имена виртуальных машин >  
  
## <a name="resolution"></a>Разрешение  
  
*Use Device Manager в гостевой операционной системе, чтобы включить все виртуальные сетевые адаптеры. Если адаптер не требуется, удалите его с виртуальной машины с помощью диспетчера Hyper-V.*  
  


