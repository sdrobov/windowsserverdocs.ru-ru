---
title: Использование всех виртуальных функций для сети, если они доступны
description: Интернет-версию текст для этого правила анализатора соответствия рекомендациям.
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: bf895484-6a0d-4aa4-9a42-9fac739e875d
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 3ad120ffa689f1f7dcae832432e216ebda57e62f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59877795"
---
# <a name="use-all-virtual-functions-for-networking-when-they-are-available"></a>Использование всех виртуальных функций для сети, если они доступны

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукта или компонента**|Hyper-V|  
|**Уровень серьезности**|Предупреждение|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблемы  
*Не используются некоторые возможностей аппаратного ускорения*  
  
## <a name="impact"></a>Влияние  
*Эта конфигурация может привести к общего использования ЦП, будет больше, чем необходимо. Производительность сети может не подходить виртуальных машинах:*  
  
\<Список виртуальных машин >  
  
## <a name="resolution"></a>Разрешение  
*Рекомендуется настроить виртуальный сетевой адаптер для SR-IOV, если физическое оборудование поддерживает SR-IOV и если эта конфигурация не конфликтует с сетевыми компонентами, требуемых для виртуальной машины.*  
  

