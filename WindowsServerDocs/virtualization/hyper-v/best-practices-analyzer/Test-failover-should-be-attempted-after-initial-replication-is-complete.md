---
title: После завершения начальной репликации должна быть предпринята тестовая отработка отказа
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: cea7eeaa-c1a7-4f87-89be-d4e1208c546f
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 41d96b33c686631f57cd35e76b64ee3dde206655
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80858947"
---
# <a name="test-failover-should-be-attempted-after-initial-replication-is-complete"></a>После завершения начальной репликации должна быть предпринята тестовая отработка отказа

>Область применения: Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Предупреждение|  
|**Категория**|Операции|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="problem"></a>Проблема  
*Тестовая отработка отказа не пройдена хотя бы в течение одного месяца.*  
  
## <a name="impact"></a>Влияние  
*Нет подтверждения о том, что запланированная или незапланированная отработка отказа будет успешно выполнена, а операции рабочей нагрузки будут выполняться правильно после отработки отказа. Это влияет на следующие виртуальные машины:*  
  
\<список виртуальных машин >  
  
## <a name="resolution"></a>Разрешение  
*Используйте диспетчер Hyper-V для проведения тестовой отработки отказа.*  
  


