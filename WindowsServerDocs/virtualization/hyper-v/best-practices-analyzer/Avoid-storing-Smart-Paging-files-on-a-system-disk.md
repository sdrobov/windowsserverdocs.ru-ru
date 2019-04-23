---
title: Не храните файлы Smart Paging на системном диске
description: Интернет-версию текст для этого правила анализатора соответствия рекомендациям.
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 9b57c9b8-76c5-43c7-bfa6-2c95b3cb6510
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 6abc84b406de7e7c33628ccee4e3af706efe5c70
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886175"
---
# <a name="avoid-storing-smart-paging-files-on-a-system-disk"></a>Не храните файлы Smart Paging на системном диске

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукта или компонента**|Hyper-V|  
|**Уровень серьезности**|Предупреждение|  
|**Категория**|Операции|  
  
В следующих разделах курсив указывает текст, отображаемый в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблемы  
*Конфигурацию памяти для одного или нескольких виртуальных машин может потребоваться использование Smart Paging, при перезагрузке виртуальной машины, а указанное расположение файла Smart Paging является системного диска сервера, выполняющего Hyper-V.*  
  
## <a name="impact"></a>Влияние  
*Использование системного диска для Smart Paging может привести к Hyper-V, проблемы с сервером. Это влияет на следующие виртуальные машины:*  
  
\<Список виртуальных машин >  
  
## <a name="resolution"></a>Разрешение  
*Перенастройте виртуальных машин, чтобы хранить файлы Smart Paging на несистемном диске.*  
  


