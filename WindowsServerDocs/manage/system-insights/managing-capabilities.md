---
title: Управление возможностями
description: Система Insights предоставляет широкий набор параметров, которые можно настроить для каждой возможности, и эти параметры могут быть настроены для конкретных потребностей развертывания адрес. В этом разделе описывается управление различные параметры для каждой возможности через Windows Admin Center или PowerShell, предоставляя простые примеры PowerShell и снимки экрана Windows Admin Center, чтобы продемонстрировать, как эти параметры можно настроить.
ms.custom: na
ms.prod: windows-server
ms.technology: system-insights
ms.topic: article
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 6/05/2018
ms.openlocfilehash: 9081a0b576ab9871b47df38255047b6cbe889419
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868025"
---
# <a name="managing-capabilities"></a>Управление возможностями

>Область применения. Windows Server 2019

В 2019 Windows Server System Insights предоставляет широкий набор параметров, которые можно настроить для каждой возможности, и эти параметры могут быть настроены для конкретных потребностей развертывания адрес. В этом разделе описывается управление различные параметры для каждой возможности через Windows Admin Center или PowerShell, предоставляя простые примеры PowerShell и снимки экрана Windows Admin Center, чтобы продемонстрировать, как эти параметры можно настроить. 

>[!TIP]
>Также можно использовать эти короткие видеоролики помогут вам приступить к работе и уверенно управлять Insights системы: [Начало работы с Insights системы в течение 10 минут](https://blogs.technet.microsoft.com/filecab/2018/07/24/getting-started-with-system-insights-in-10-minutes/)

Хотя в этом разделе содержатся примеры PowerShell, можно использовать [документации PowerShell Insights системы](https://aka.ms/systeminsightspowershell) чтобы увидеть все наборы командлетов, параметров и параметров в пределах системы аналитики. 

## <a name="viewing-capabilities"></a>Возможности просмотра

Чтобы приступить к работе, можно вывести список доступных возможностей с помощью **Get InsightsCapability** командлета: 

```PowerShell
Get-InsightsCapability
``` 
Эти возможности доступны в расширении системы аналитики:

![Общие сведения о странице системы аналитики, список доступные возможности](media/overview-page-contoso.png)

## <a name="enabling-and-disabling-a-capability"></a>Включение и отключение возможности
Каждая возможность можно включить или отключить. Отключение возможности препятствует вызываемого эту возможность, и для возможности не по умолчанию, отключение возможности останавливает сбор всех данных для этой возможности. По умолчанию включены все возможности, и можно проверить состояние возможностей с помощью **Get InsightsCapability** командлета. 

Чтобы включить или отключить функцию, используйте **Enable InsightsCapability** и **Disable InsightsCapability** командлетов:

```PowerShell
Enable-InsightsCapability -Name "CPU capacity forecasting"
Disable-InsightsCapability -Name "Networking capacity forecasting"
``` 
Эти параметры также могут быть переключены с выбранной возможности в Windows Admin Center щелкнув **включить** или **отключить** кнопки.

### <a name="invoking-a-capability"></a>Возможность вызова
Вызов возможность сразу же выполняется возможностью получения прогноза, и Администраторы могут вызвать функцию любое время, выбрав **Invoke** button в Windows Admin Center или с помощью  **Вызвать InsightsCapability** командлета:

```PowerShell
Invoke-InsightsCapability -Name "CPU capacity forecasting"
```

>[!TIP]
>Чтобы убедиться в том, что возможность вызова не противоречит критически важных операций на компьютере, рекомендуется запланировать прогнозов off рабочее время.

## <a name="retrieving-capability-results"></a>Извлечение результатов возможность
После вызова возможность самые новые результаты являются видимыми с помощью **Get-InsightsCapability** или **Get-InsightsCapabilityResult**. Эти командлеты вывода самого последнего **состояние** и **описание состояния** каждой возможности, которые описывает результат каждого прогноза. **Состояние** и **описание состояния** поля более подробно описаны в [основные сведения о возможности документа](understanding-capabilities.md). 

Кроме того, можно использовать **Get InsightsCapabilityResult** командлет просмотреть последние результаты прогнозирования 30 и как извлекать данные, связанные с прогноза: 

```PowerShell
# Specify the History parameter to see the last 30 prediction results.
Get-InsightsCapabilityResult -Name "CPU capacity forecasting" -History

# Use the Output field to locate and then show the results of "CPU capacity forecasting."
# Specify the encoding as UTF8, so that Get-Content correctly parses non-English characters.
$Output = Get-Content (Get-InsightsCapabilityResult -Name "CPU capacity forecasting").Output -Encoding UTF8 | ConvertFrom-Json
$Output.ForecastingResults
```
Расширение Insights системы автоматически показывает журнал прогнозов и анализ результатов результата JSON, позволяя графа интуитивно понятный, высококачественный каждого прогноза:

![Страница одним типом возможностей диаграмму прогнозирования и журнал прогнозов](media/cpu-forecast-2.png)

### <a name="using-the-event-log-to-retrieve-capability-results"></a>Использование журнала событий для получения результатов возможность
Система Insights регистрирует событие каждый раз, функцию завершения прогноз. Эти события являются видимыми в **Microsoft-Windows-System-Insights/Admin** канала и аналитику системы публикует другое событие идентификатор для каждого состояния:   

| Состояние прогноза | Идентификатор события |
| --------------- | --------------- |
| ОК | 151 |
| Предупреждение | 148 |
| Критическое | 150 |
| Ошибка | 149 |
| Нет | 132 |

>[!TIP]
>Используйте [Azure Monitor](https://azure.microsoft.com/services/monitor/) или [System Center Operations Manager](https://docs.microsoft.com/system-center/scom/welcome?view=sc-om-1807) для статистической обработки этих событий и просмотреть результаты прогноза для группы компьютеров.


## <a name="setting-a-capability-schedule"></a>Настройка расписания возможность
В дополнение к прогнозов по требованию периодических прогнозов для каждой возможности можно настроить так, что определенные возможности автоматически на основе предопределенного расписания. Используйте **Get InsightsCapabilitySchedule** командлету см. в разделе возможностей расписания: 

>[!TIP]
>Чтобы получить сведения для всех возможностей, возвращенный используйте оператор конвейера в PowerShell **Get InsightsCapability** командлета.

```PowerShell
Get-InsightsCapability | Get-InsightsCapabilitySchedule
```

Периодических прогнозов включены по умолчанию, хотя их можно отключить в любое время **Enable InsightsCapabilitySchedule** и **Disable InsightsCapabilitySchedule** командлетов:

```PowerShell
Enable-InsightsCapabilitySchedule -Name "Total storage consumption forecasting"
Disable-InsightsCapabilitySchedule -Name "Volume consumption forecasting"
```

Каждая возможность по умолчанию запланировано выполнение каждый день в 03: 00. Тем не менее, можно создать пользовательские расписания для каждой возможности и системы Insights поддерживает различные типы расписания, которые могут быть настроены с помощью **InsightsCapabilitySchedule набора** командлета: 

```PowerShell
Set-InsightsCapabilitySchedule -Name "CPU capacity forecasting" -Daily -DaysInterval 2 -At 4:00PM
Set-InsightsCapabilitySchedule -Name "Networking capacity forecasting" -Daily -DaysOfWeek Saturday, Sunday -At 2:30AM
Set-InsightsCapabilitySchedule -Name "Total storage consumption forecasting" -Hourly -HoursInterval 2 -DaysOfWeek Monday, Wednesday, Friday
Set-InsightsCapabilitySchedule -Name "Volume consumption forecasting" -Minute -MinutesInterval 30 
```
>[!NOTE]
>Так как возможности по умолчанию анализировать ежедневной данные, рекомендуется использовать ежедневных расписания для этих возможностей. Дополнительные сведения о возможностях по умолчанию [здесь](understanding-capabilities.md).

Windows Admin Center также можно использовать для просмотра и установки расписания для каждой возможности, щелкнув **параметры**. Текущее расписание отображается на **расписание** вкладки и можно использовать средства с графическим Интерфейсом для создания нового расписания:

![Параметры страницы, показывающий текущее расписание](media/schedule-page-contoso.png)

## <a name="creating-remediation-actions"></a>Создание действия по исправлению
Insights системы позволяет запускать сценарии пользовательских обновлений, на основе результата возможности. Для каждой возможности можно настроить настраиваемый скрипт PowerShell для состояния каждого прогноза, позволяя администраторам для выполнения корректирующих действий автоматически, а не требуя ручного вмешательства. 

Пример действия по исправлению включают запустите очистку диска, расширение тома, вы запустили дедупликации, перенести виртуальные машины и Настройка синхронизации файлов Azure.

Вы увидите действия для каждой возможности с помощью **Get InsightsCapabilityAction** командлета:

```PowerShell
Get-InsightsCapability | Get-InsightsCapabilityAction
```

Можно создать новые действия или удаления существующего действия, с помощью **набора InsightsCapabilityAction** и **Remove-InsightsCapabilityAction** командлетов. Каждое действие выполняется с использованием учетных данных, которые указаны в **ActionCredential** параметра.

>[!NOTE]
>В первоначальном выпуске системы аналитики необходимо указать скрипты исправления за пределами каталоги пользователей. Это будет исправлено в следующем выпуске.

```PowerShell
$Cred = Get-Credential
Set-InsightsCapabilityAction -Name "CPU capacity forecasting" -Type Warning -Action "C:\Users\Public\WarningScript.ps1" -ActionCredential $Cred
Set-InsightsCapabilityAction -Name "CPU capacity forecasting" -Type Critical -Action "C:\Users\Public\CriticalScript.ps1" -ActionCredential $Cred

Remove-InsightsCapabilityAction -Name "CPU capacity forecasting" -Type Warning
```

Можно также использовать Windows Admin Center задание с помощью действия по исправлению **действия** перехода в пределах **параметры** страницы:

![Параметры страницы, где пользователь может указать действия по исправлению](media/actions-page-contoso.png)


## <a name="see-also"></a>См. также
Дополнительные сведения о системе аналитики, используйте следующие ресурсы:

- [Обзор системы аналитики](overview.md)
- [Основные сведения о возможностях](understanding-capabilities.md)
- [Добавления и возможности разработки](adding-and-developing-capabilities.md)
- [Система аналитики часто задаваемые вопросы](faq.md)