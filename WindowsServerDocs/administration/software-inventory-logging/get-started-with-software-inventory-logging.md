---
title: Приступая к работе с журналом инвентаризации программного обеспечения
description: Описание процесса установки и начала использования ведения журнала инвентаризации программного обеспечения
ms.prod: windows-server
ms.technology: manage-software-inventory-logging
ms.topic: article
ms.assetid: ed51c13c-7cbf-4144-a675-011fd29379d4
author: brentfor
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e54e8f96863280263f7afee2e32bfd41ec712110
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851447"
---
# <a name="get-started-with-software-inventory-logging"></a>Приступая к работе с журналом инвентаризации программного обеспечения

>Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

 Ведение журнала инвентаризации программного обеспечения собирает данные инвентаризации программного обеспечения Майкрософт на уровне каждого сервера. Прежде чем использовать ведение журнала инвентаризации программного обеспечения с Windows Server 2012 R2, убедитесь, что Центр обновления Windows [kb 3000850](https://support.microsoft.com/kb/3000850) и [KB 3060681](https://support.microsoft.com/kb/3060681) установлены в каждой системе, которая будет включена в опись. Для Windows Server 2016 не требуется никаких Центр обновления Windows. Кроме того, если вы хотите использовать возможность SIL для пересылки данных на сервер агрегирования, убедитесь, что для вашей сети используются SSL-сертификаты.

## <a name="feature-description"></a><a name="BKMK_OVER"></a> Описание функции
Журнал инвентаризации программного обеспечения в Windows Server — это компонент с простым набором командлетов PowerShell, который помогает администраторам получить список программ Майкрософт, установленных на их серверах. Он также предоставляет возможность периодически собирать и перенаправлять эти данные по сети с помощью протокола HTTPS для статистической обработки. Управление этим компонентом, главным образом для ежечасного сбора и перенаправления, также выполняется с помощью команд PowerShell.

> [!NOTE]
> Сервер статистической обработки, запущенный в веб-службе, можно настроить отдельно. См. дополнительные сведения о [средстве инвентаризации программного обеспечения](software-inventory-logging-aggregator.md).

> [!IMPORTANT]
> Ни один из данных, собираемых функцией ведения журнала инвентаризации программного обеспечения, не отправляется в корпорацию Майкрософт в рамках функциональности функции.

## <a name="practical-applications"></a><a name="BKMK_APP"></a>Практические приложения
Интерфейсы инвентаризации программного обеспечения предназначены для сокращения эксплуатационных расходов на получение точной информации о программном обеспечении Майкрософт, локально развернутом на сервере, особенно на множестве серверов в ИТ-среде (при условии, что компонент развернут и работает в ИТ-среде). Возможность перенаправлять эти данные на сервер агрегации (если это задано ИТ-администратором) позволяет собрать данные в одном месте с помощью универсальной автоматической процедуры. Несмотря на то, что аналогичный результат можно получить при опросе интерфейсов напрямую, инвентаризация программного обеспечения при использовании архитектуры перенаправления (по сети), запускаемой на каждом сервере, позволяет устранить множество проблем с обнаружением компьютеров, типичных для многих сценариев инвентаризации программного обеспечения и управления активами. Протокол SSL используется для защиты данных, пересылаемых по протоколу HTTPS, на сервер агрегирования администратора. Если все данные находятся в одном месте (на одном сервере), их проще анализировать, с ними проще работать, на их основе проще создавать отчеты. Важно отметить, что ни один фрагмент этих данных не передается в Майкрософт в процессе работы компонента. Данные и функции ведения журнала инвентаризации программного обеспечения предназначены исключительно для использования лицензированного владельца и администраторов серверного программного обеспечения.

Журнал инвентаризации программного обеспечения может помочь администраторам серверов в осуществлении следующих задач.

-   Удаленное получение информации о перечне программного обеспечения и серверов по запросу от Windows Server.

-   Статистическая обработка данных инвентаризации программного обеспечения и сервера для широкого спектра сценариев управления ресурсами программного обеспечения путем включения функции ведения журнала инвентаризации программного обеспечения для каждого сервера и выбора целевого URI веб-сервера и отпечатка сертификата для проверки подлинности.

## <a name="see-also"></a>См. также
[Агрегатор инвентаризации программного обеспечения](https://technet.microsoft.com/library/mt572043.aspx)<br>
[Управление журналом инвентаризации программного обеспечения](manage-software-inventory-logging.md)<br>
[Командлеты ведения журнала инвентаризации программного обеспечения в Windows PowerShell](https://technet.microsoft.com/library/dn283390.aspx)<br>
[Набор средств оценки и планирования Microsoft](https://www.microsoft.com/download/en/details.aspx?id=7826)
[средство управления многопользовательской активацией](https://blogs.technet.com/b/volume-licensing/)

