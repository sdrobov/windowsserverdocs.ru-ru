---
title: Количество логических процессоров используется не должна превышать максимально допустимого значения
description: Содержит инструкции по устранению проблемы, о которой сообщило это правило анализатор соответствия рекомендациям.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 66df8b02-91d1-424b-8934-a39c214d530e
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: b6cd948c47e58dec919cd946ad701f70403d6af3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859297"
---
# <a name="the-number-of-logical-processors-in-use-must-not-exceed-the-supported-maximum"></a>Количество логических процессоров используется не должна превышать максимально допустимого значения

>Область применения: Windows Server 2016

Дополнительные сведения о рекомендациях и сканировании см. в разделе [Анализатор соответствия рекомендациям](https://go.microsoft.com/fwlink/?LinkId=122786).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Ошибка|  
|**Категория**|Политика|  
  
В следующих разделах курсив указывает текст, отображаемый в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблема  
  
*На сервере настроено слишком много логических процессоров.*  
  
## <a name="impact"></a>Влияние  
  
*Корпорация Майкрософт не поддерживает выполнение Hyper-V на этом компьютере.*  
  
## <a name="resolution"></a>Разрешение  
  
*Удалите некоторые процессоры с этого компьютера или используйте MSCONFIG, чтобы ограничить количество доступных процессоров.*  
  
В приведенных ниже инструкциях использование средства Msconfig. Дополнительные сведения об удалении процессоров см. инструкции, поставляемой вместе с компьютером, или обратитесь к изготовителю оборудования. Дополнительные сведения о максимальные поддерживаемые конфигурации для Hyper-V см [Планирование масштабируемость Hyper-V в Windows Server 2016](../plan/Plan-for-Hyper-V-scalability-in-Windows-Server-2016.md).  
  
### <a name="to-limit-the-number-of-available-processors"></a>Чтобы ограничить число доступных процессоров  
  
1.  Открыть систему конфигурации приложения (Msconfig.exe). Чтобы сделать это, нажмите кнопку **запустить**, тип **msconfig**, щелкните правой кнопкой мыши **конфигурации системы** настольных приложений и нажмите кнопку **Запуск от имени администратора**.  
  
2.  Из **загрузки** щелкните **Дополнительные параметры**.  
  
3.  Выберите **число процессоров** и затем выберите номер в списке. Нажмите кнопку **ОК**.  
  
4.  Перезагрузите компьютер, чтобы запустить его, используя новое количество процессоров.  
  


