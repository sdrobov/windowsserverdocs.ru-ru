---
title: PVLAN конфигурации в виртуальном коммутаторе должны быть согласованы
description: Интернет-версию текст для этого правила анализатора соответствия рекомендациям.
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 4db63bcc-7a54-4f19-98a6-c274c3956d51
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: b7d6d068027aa9497b00138bd1d889ea86aa3308
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813255"
---
# <a name="pvlan-configuration-on-a-virtual-switch-must-be-consistent"></a>PVLAN конфигурации в виртуальном коммутаторе должны быть согласованы

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016| 
|**Продукта или компонента**|Hyper-V|  
|**Уровень серьезности**|Ошибка|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.
  
## <a name="issue"></a>**Проблема**  
*Частные виртуальной локальной сети (PVLAN) настроен неправильно на один или несколько виртуальных сетевых адаптеров.*  
  
## <a name="impact"></a>**Влияние**  
*PVLAN не может правильно изолировать сетевой трафик между виртуальными машинами.*  
  
## <a name="resolution"></a>**Решение**  
*Используйте командлет Windows PowerShell Set-VMNetworkAdapterVlan, чтобы правильно настроить PVLAN.*  
  


