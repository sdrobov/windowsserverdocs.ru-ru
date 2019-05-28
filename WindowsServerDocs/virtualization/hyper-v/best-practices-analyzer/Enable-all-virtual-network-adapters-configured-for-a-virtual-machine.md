---
title: Включить все виртуальные сетевые адаптеры, настроенные для виртуальной машины
description: Интернет-версию текст для этого правила анализатора соответствия рекомендациям.
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: fcd350b7-4240-4359-aadd-93e7ac4d314e
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: fbb1ef5283f6ccf8dfa355a09a86040be80f53e9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59844235"
---
# <a name="enable-all-virtual-network-adapters-configured-for-a-virtual-machine"></a>Включить все виртуальные сетевые адаптеры, настроенные для виртуальной машины

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и сканировании см. в разделе [Анализатор соответствия рекомендациям](https://go.microsoft.com/fwlink/?LinkId=122786).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукта или компонента**|Hyper-V|  
|**Уровень серьезности**|Предупреждение|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблемы  
  
*Можно отключить один или несколько сетевых адаптеров в виртуальной машине.*  
  
## <a name="impact"></a>Влияние  
  
*Следующие виртуальные машины не может иметь сетевое подключение:*  
  
\<Список имен виртуальных машин >  
  
## <a name="resolution"></a>Разрешение  
  
*С помощью диспетчера устройств в гостевой операционной системы для включения всех виртуальных сетевых адаптеров. Если адаптер не требуется, используйте диспетчер Hyper-V, удалить его из виртуальной машины.*  
  

