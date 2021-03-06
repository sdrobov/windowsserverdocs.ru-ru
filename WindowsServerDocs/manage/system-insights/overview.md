---
title: Обзор системной аналитики
description: System Insights — это новая функция прогнозной аналитики в Windows Server 2019. Прогнозные возможности System Insights — каждый, основанный на модели машинного обучения, выполняет локальное анализ системных данных Windows Server, таких как счетчики производительности и события, позволяя понять работу серверов и сократить эксплуатационные расходы, связанные с устранением неполадок в развертываниях.
ms.prod: windows-server
ms.technology: system-insights
ms.topic: article
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 5/23/2018
ms.openlocfilehash: b1f0fc5343c5228a02369a64bff2de50ab3f863e
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85471769"
---
# <a name="system-insights-overview"></a>Обзор системной аналитики

>Область применения: Windows Server 2019

System Insights — это новая функция прогнозной аналитики в Windows Server 2019. Прогнозные возможности System Insights — каждый, основанный на модели машинного обучения, выполняет локальное анализ системных данных Windows Server, таких как счетчики производительности и события, позволяя понять работу серверов и сократить эксплуатационные расходы, связанные с устранением неполадок в развертываниях.

В Windows Server 2019 System Insights поставляется с четырьмя возможностями по умолчанию, которые зависят от прогнозирования емкости, прогнозирования будущего ресурса для вычислений, сети и хранилища на основе предыдущих моделей использования. System Insights также поставляется с [расширяемой инфраструктурой](adding-and-developing-capabilities.md), поэтому корпорация Майкрософт и сторонние компании могут добавлять новые прогнозные возможности в System Insights без обновления операционной системы.

Вы можете управлять System Insights с помощью интуитивно понятного расширения [центра администрирования Windows](https://docs.microsoft.com/windows-server/manage/windows-admin-center/overview) или [напрямую с помощью PowerShell](https://aka.ms/SystemInsightsPowerShell), а System Insights позволяет настраивать каждую прогнозную возможность отдельно в соответствии с потребностями вашего развертывания. Все результаты прогноза публикуются в журнале событий, что позволяет использовать [Azure Monitor](https://azure.microsoft.com/services/monitor/) или [System Center Operations Manager](https://docs.microsoft.com/system-center/scom/welcome?view=sc-om-1807) для простого агрегирования и просмотра прогнозов в группе компьютеров.

![Расширение System Insights в центре администрирования Windows, в котором показана возможность прогнозирования ресурсов ЦП с помощью графика для прогнозирования прогноза](media/cpu-forecast-2.png)

## <a name="local-functionality"></a>Локальная функциональность
System Insights выполняется полностью локально на Windows Server. С помощью новых функций, появившихся в Windows Server 2019, все ваши данные собираются, сохраняются и анализируются непосредственно на компьютере, что позволяет реализовать возможности прогнозной аналитики без подключения к облаку.

Системные данные хранятся на компьютере, и эти данные анализируются прогнозными возможностями, которые не нуждаются в повторном обучении в облаке. С помощью System Insights можно сохранить данные на компьютере и по-прежнему использовать возможности прогнозной аналитики.

## <a name="get-started"></a>Приступая к работе

<iframe src=https://www.youtube-nocookie.com/embed/AJxQkx5WSaA width=560 height=315 allowfullscreen></iframe>

>[!TIP]
>Просмотрите эти короткие видеоматериалы, чтобы узнать, как приступить к работе и уверенно управлять System Insights. [Приступая к работе с System Insights за 10 минут](https://blogs.technet.microsoft.com/filecab/2018/07/24/getting-started-with-system-insights-in-10-minutes/)

### <a name="requirements"></a>Требования
System Insights доступен на любом экземпляре Windows Server 2019. Она выполняется на узле и на гостевых компьютерах, в любой низкоуровневой оболочке и в любом облаке.

### <a name="install-system-insights"></a>Установка System Insights
>[!IMPORTANT]
>System Insights собирает и сохраняет данные в течение года локально. Если вы хотите хранить данные при обновлении операционной системы, **Убедитесь, что используется обновление на месте**.

#### <a name="install-the-feature"></a>Установка компонента
Вы можете установить System Insights с помощью расширения в центре администрирования Windows:

![День 0 опыт работы с расширением System Insights.](media/day-0-2.png)

Вы также можете установить System Insights напрямую с помощью диспетчер сервера, добавив функцию **System-Insights** или используя PowerShell:

```PowerShell
Add-WindowsFeature System-Insights -IncludeManagementTools
```

## <a name="provide-feedback"></a>Отзывы
Мы будем рады получить ваши отзывы, чтобы помочь нам улучшить эту функцию. Для отправки отзывов можно использовать следующие каналы:
- **Центр обратной связи**: используйте средство "центр обратной связи" в Windows 10, чтобы отправить сообщение об ошибке или отзыв. При этом необходимо указать:
    - **Категория**: сервер
    - **Подкатегория**: System Insights
- **UserVoice**: Отправка запросов на функции через нашу [страницу UserVoice](https://windowsserver.uservoice.com/forums/295071-management-tools). Поделитесь с коллегами, чтобы получить важные для вас элементы.
- **Электронная почта**. Если вы хотите отправить отзыв закрытой группе функций, отправьте сообщение по адресу system-insights-feed@microsoft.com . Имейте в виду, что мы по-прежнему можем попросить вас использовать центр обратной связи или UserVoice.

## <a name="additional-references"></a>Дополнительные ссылки
Дополнительные сведения о System Insights см. в следующих ресурсах:

- [Общие сведения о возможностях](understanding-capabilities.md)
- [Управление возможностями](managing-capabilities.md)
- [Добавление и разработка возможностей](adding-and-developing-capabilities.md)
- [Вопросы и ответы по System Insights](faq.md)