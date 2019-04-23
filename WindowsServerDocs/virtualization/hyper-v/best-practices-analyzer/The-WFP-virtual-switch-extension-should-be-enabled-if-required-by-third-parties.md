---
title: Должно быть включено расширение виртуального переключения WFP, если он необходим для сторонних расширений
description: Интернет-версию текст для этого правила анализатора соответствия рекомендациям.
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 8aa8a9a5-e3fa-4c9b-8331-ba5a3de22429
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 5afe706c246276597b32400109370ba3129e5a24
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59850625"
---
# <a name="the-wfp-virtual-switch-extension-should-be-enabled-if-it-is-required-by-third-party-extensions"></a>Должно быть включено расширение виртуального переключения WFP, если он необходим для сторонних расширений

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукта или компонента**|Hyper-V|  
|**Уровень серьезности**|Предупреждение|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>**Проблема**  
*При отключении расширения виртуального коммутатора платформы фильтрации Windows (WFP).*  
  
## <a name="impact"></a>**Влияние**  
*Некоторые сторонние расширения виртуального коммутатора может завершаться ошибкой для следующих виртуальных коммутаторов:*  
  
\<Список виртуальных машин >  
  
## <a name="resolution"></a>**Решение**  
*Используйте командлет Windows PowerShell, Enable-VMSwitchExtension, чтобы включить платформы фильтрации Windows, если он требуется для сторонних расширений.*  
  
### <a name="enable-the-windows-filtering-platform-using-windows-powershell"></a>Включить с помощью Windows PowerShell платформы фильтрации Windows  
  
1.  Откройте Windows PowerShell. (На рабочем столе щелкните **запустить** и начните вводить **Windows PowerShell**.)  
  
2.  Щелкните правой кнопкой мыши **Windows PowerShell** и нажмите кнопку **Запуск от имени администратора**.  
  
3.  После замены внешним именем внешний коммутатор, выполните следующую команду:  
  
```  
Enable-VMSwitchExtension -VMSwitchName External -Name "Microsoft Windows Filtering Platform"  
```  
  
## <a name="see-also"></a>См. также  
[Enable-VMSwitchExtension](https://technet.microsoft.com/library/hh848541.aspx)  
  


