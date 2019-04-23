---
title: Система аналитики часто задаваемые вопросы
description: Система аналитики часто задаваемые вопросы
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: system-insights
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ''
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 5/23/2018
ms.openlocfilehash: 13767e1336d1ff729d1fbbe6cae3ed57d68cefc4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59851065"
---
# <a name="system-insights-faq"></a>Система аналитики часто задаваемые вопросы

>Область применения. Windows Server 2019

## <a name="how-can-you-use-system-insights-with-azure-monitor-or-system-center-operations-manager"></a>Как использовать систему аналитики с помощью Azure Monitor или System Center Operations Manager?

[Azure Monitor](https://azure.microsoft.com/services/monitor/) и [System Center Operations Manager](https://docs.microsoft.com/system-center/scom/welcome?view=sc-om-1807) предоставляют сведения о функционировании во всех ваших развертываниях, которые помогут управлять инфраструктурой. Аналитика системы, напротив, — это компонент Windows Server, который представляет возможности локального прогнозной аналитики. Вместе системы Insights и Azure Monitor и SCOM может помочь surface прогнозы заполнения устройств:

 Azure Monitor или SCOM можно ключа отключение событий, созданные компонентом системы аналитики, как система Insights выводит результат каждого прогноза, в журнале событий. Они могут возникать эти прогнозы конкретного компьютера в группе серверов Windows, что обеспечивает единое представление этих прогнозов для группы экземпляров сервера. 
 
 См. в разделе channel и ИД событий для каждого прогноза [здесь](https://docs.microsoft.com/windows-server/manage/system-insights/managing-capabilities#retrieving-capability-results).

## <a name="how-does-system-insights-relate-to-windows-ml"></a>Как соотносятся системы аналитики для машинного Обучения Windows?

[Машинное Обучение Windows](https://docs.microsoft.com/windows/uwp/machine-learning/) — это платформа, которая позволяет разработчикам импортировать и оценка моделей предварительно обученной машинного обучения на устройствах Windows. Эти модели использовать преимущества аппаратного ускорения, и они могут быть рассчитаны локально. 

Системы аналитики — это функция в Windows Server 2019, предлагающий локального возможности прогнозирования, а также все возможности управления, включая интеграцию с Windows Admin Center и PowerShell. 

## <a name="can-i-use-system-insights-for-my-cluster"></a>Можно ли использовать Insights системы для моего кластера? 

Да. Аналитику системы независимо друг от друга можно выполнить на каждом узле отдельных отказоустойчивого кластера и использования прогнозов Insights системы по умолчанию в локальном хранилище, тома, ЦП и сети. **Можно также включить прогнозирования для кластерных хранилищ,**, поэтому возможности прогнозирования хранения прогнозирования использования для тома кластера и хранилища. 

Вы можете управлять этими параметрами в Windows Admin Center или PowerShell, а также более подробные сведения об этих возможностях [здесь](https://blogs.technet.microsoft.com/filecab/2018/10/03/using-system-insights-to-forecast-clustered-storage-usage/).
 

## <a name="how-expensive-is-it-to-run-the-default-capabilities"></a>Сколько ресурсов требуется его запуск возможности по умолчанию?

Каждая возможность по умолчанию является недорогим для запуска. Каждая возможность займет больше времени, как собрать больше данных, но они обычно должен быть выполнен через несколько секунд. 

## <a name="see-also"></a>См. также
Дополнительные сведения о системе аналитики, используйте следующие ресурсы:

- [Обзор системы аналитики](overview.md)
- [Основные сведения о возможностях](understanding-capabilities.md)
- [Управление возможностями](managing-capabilities.md)
- [Добавления и возможности разработки](adding-and-developing-capabilities.md)
