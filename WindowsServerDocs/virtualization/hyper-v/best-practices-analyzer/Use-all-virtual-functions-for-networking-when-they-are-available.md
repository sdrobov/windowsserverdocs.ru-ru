---
title: Использовать все виртуальные функции для работы в сети, если они доступны
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: bf895484-6a0d-4aa4-9a42-9fac739e875d
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 0fab06ae21a4632df73b7a4d8b17b12665ffed98
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854217"
---
# <a name="use-all-virtual-functions-for-networking-when-they-are-available"></a>Использовать все виртуальные функции для работы в сети, если они доступны

>Область применения: Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Предупреждение|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблема  
*Некоторые возможности аппаратного ускорения не используются*  
  
## <a name="impact"></a>Влияние  
*Эта конфигурация может привести к тому, что общая загрузка ЦП будет выше, чем требуется. Производительность сети может быть неоптимальной на следующих виртуальных машинах:*  
  
\<список виртуальных машин >  
  
## <a name="resolution"></a>Разрешение  
*Рассмотрите возможность настройки виртуального сетевого адаптера для SR-IOV, если физическое оборудование поддерживает SR-IOV, и если эта конфигурация не конфликтует с сетевыми компонентами, необходимыми для виртуальной машины.*  
  


