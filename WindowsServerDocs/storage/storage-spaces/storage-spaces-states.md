---
title: Дисковые пространства и Локальные дисковые пространства работоспособности и операционные состояния
description: Узнайте, как найти и оценить различные работоспособность и операционные состояния Локальные дисковые пространства и дисковых пространств (включая физические диски, пулы и виртуальные диски) и что делать с ними.
author: jasongerend
ms.author: jgerend
ms.date: 12/06/2019
ms.topic: article
ms.prod: windows-server
ms.technology: storage-spaces
manager: brianlic
ms.openlocfilehash: d7bbef54d0ec554c6a3cf184dcb0414f7456547c
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182160"
---
# <a name="troubleshoot-storage-spaces-and-storage-spaces-direct-health-and-operational-states"></a>Устранение неполадок дисковых пространств и Локальные дисковые пространства работоспособности и рабочих состояний

> Область применения: Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server (половина ежегодного канала), Windows 10, Windows 8.1

В этом разделе описываются работоспособность и операционные состояния пулов носителей, виртуальные диски (которые находятся под томами в дисковых пространствах) и диски в [Локальные дисковые пространства](storage-spaces-direct-overview.md) и дисковых [пространствах](overview.md). Эти состояния могут оказаться бесполезными при устранении различных проблем, например о том, почему нельзя удалить виртуальный диск из-за конфигурации только для чтения. Здесь также обсуждается, почему не удается добавить диск в пул (Каннотпулреасон).

Дисковые пространства имеют три основных объекта — *физические диски* (жесткие диски, твердотельные накопители и т. д.), которые добавляются в *пул носителей*, что позволяет создавать *Виртуальные диски* на основе свободного пространства в пуле, как показано ниже. Метаданные пула записываются на каждый диск в пуле. Тома создаются поверх виртуальных дисков и сохраняются в файлах, но мы не будем говорить о томах.

![Физические диски добавляются в пул носителей, а затем виртуальные диски, созданные из области пула.](media/storage-spaces-states/storage-spaces-object-model.png)

Вы можете просматривать работоспособность и операционные состояния в диспетчер сервера или с помощью PowerShell. Ниже приведен пример различных (обычно поврежденных) работоспособности и операционных состояний в кластере Локальные дисковые пространства, в котором отсутствует большая часть узлов кластера (щелкните правой кнопкой мыши заголовки столбцов для добавления **оперативного состояния**). Это не самый удачный кластер.

![Диспетчер сервера отображение результатов двух отсутствующих узлов в кластере Локальные дисковые пространства — большое количество отсутствующих физических дисков и виртуальных дисков в неработоспособном состоянии](media/storage-spaces-states/unhealthy-disks-in-server-manager.png)

## <a name="storage-pool-states"></a>Состояния пула носителей

Каждый пул носителей имеет состояние работоспособности — **работоспособное**, **предупреждение**или **неизвестное** / ,**неработоспособное**, а также одно или несколько рабочих состояний.

Чтобы узнать, в каком состоянии находится пул, используйте следующие команды PowerShell:

```PowerShell
Get-StoragePool -IsPrimordial $False | Select-Object HealthStatus, OperationalStatus, ReadOnlyReason
```

Ниже приведен пример выходных данных, демонстрирующих пул носителей в неизвестном состоянии работоспособности с операционным состоянием только для чтения.

```
FriendlyName                OperationalStatus HealthStatus IsPrimordial IsReadOnly
------------                ----------------- ------------ ------------ ----------
S2D on StorageSpacesDirect1 Read-only         Unknown      False        True
```

В следующих разделах перечислены состояния работоспособности и рабочие состояния.

### <a name="pool-health-state-healthy"></a>Состояние работоспособности пула: исправен

| Состояние работы    | Описание |
| ---------            | ---------  |
| OK | Пул носителей находится в работоспособном состоянии. |

### <a name="pool-health-state-warning"></a>Состояние работоспособности пула: предупреждение

Если пул носителей находится в состоянии работоспособности " **предупреждение** ", это означает, что пул доступен, но один или несколько дисков завершились сбоем или отсутствуют. В результате может снизиться устойчивость пула носителей.

|Состояние работы    |Описание|
|---------            |---------  |
|Деградация|В пуле носителей неисправные или отсутствующие диски. Это состояние возникает только с дисками, на которых размещены метаданные пула. <br><br>**Действие**: Проверьте состояние дисков и замените все неисправные диски до появлении дополнительных сбоев.|

### <a name="pool-health-state-unknown-or-unhealthy"></a>Состояние работоспособности пула: неизвестно или неработоспособно

Если пул носителей находится в **неизвестном** или **неработоспособном** состоянии работоспособности, это означает, что пул носителей доступен только для чтения и не может быть изменен до тех пор, пока пул не будет возвращен в состояние работоспособности **предупреждения** или **ОК** .

|Состояние работы    |Причина только для чтения |Описание|
|---------            |---------       |--------   |
|Только для чтения|Неполный|Это может произойти, если пул носителей теряет [кворум](understand-quorum.md), что означает, что большинство дисков в пуле завершились сбоем или находятся в автономном режиме по какой бы то ни было причине. Когда пул теряет кворум, дисковые пространства автоматически устанавливают конфигурацию пула в значение только для чтения до тех пор, пока не освободится достаточное количество дисков.<br><br>**Действие:** <br>1. Подключите недостающие диски и, если вы используете Локальные дисковые пространства, переведите все серверы в режим «в сети». <br>2. снова установите для пула значение "чтение и запись", открыв сеанс PowerShell с разрешениями администратора и введя:<br><br> <code>Get-StoragePool <PoolName> -IsPrimordial $False \| Set-StoragePool -IsReadOnly $false</code>|
||Политика|Администратор задает для пула носителей доступ только для чтения.<br><br>**Действие:** Чтобы задать для кластеризованного пула носителей доступ для чтения и записи в диспетчер отказоустойчивости кластеров, выберите **Пулы**, щелкните пул правой кнопкой мыши и выберите **перевести в режим**«в сети».<br><br>Для других серверов и компьютеров откройте сеанс PowerShell с разрешениями администратора и введите:<br><br><code>Get-StoragePool <PoolName> \| Set-StoragePool -IsReadOnly $false</code><br><br> |
||Запуск|Дисковые пространства запускаются или ожидают подключения дисков в пуле. Это должно быть временное состояние. После полного запуска пул должен перейти в другое рабочее состояние.<br><br>**Действие:** Если пул остается в *начальном* состоянии, убедитесь, что все диски в пуле подключены правильно.|

См. также [форум по хранилищу Windows Server](https://docs.microsoft.com/answers/topics/windows-server-storage.html).

## <a name="virtual-disk-states"></a>Состояния виртуальных дисков

В дисковых пространствах тома размещаются на виртуальных дисках (дисковых пространствах), отрезать пространство свободного места в пуле. Каждый виртуальный диск имеет состояние работоспособности — **работоспособное**, **предупреждение**, **неработоспособное**или **неизвестное** , а также одно или несколько рабочих состояний.

Чтобы узнать, в каком состоянии находятся виртуальные диски, используйте следующие команды PowerShell:

```PowerShell
Get-VirtualDisk | Select-Object FriendlyName,HealthStatus, OperationalStatus, DetachedReason
```

Ниже приведен пример выходных данных с отсоединенным виртуальным диском и виртуальным диском с пониженной производительностью или неполным.

```
FriendlyName HealthStatus OperationalStatus      DetachedReason
------------ ------------ -----------------      --------------
Volume1      Unknown      Detached               By Policy
Volume2      Warning      {Degraded, Incomplete} None
```

В следующих разделах перечислены состояния работоспособности и рабочие состояния.

### <a name="virtual-disk-health-state-healthy"></a>Состояние работоспособности виртуального диска: исправен

|Состояние работы    |Описание|
|---------            |---------          |
|OK    |Виртуальный диск исправен.|
|Suboptimal (Неоптимальное)    |Данные не записываются на диски равномерно. <br><br>**Действие**: Оптимизируйте использование дисков в пуле носителей, запустив командлет [optimize-StoragePool](/powershell/module/storage/optimize-storagepool?view=win10-ps) .|

### <a name="virtual-disk-health-state-warning"></a>Состояние работоспособности виртуального диска: предупреждение

Если виртуальный диск находится в состоянии " **предупреждение** ", это означает, что одна или несколько копий данных недоступны, но дисковые пространства по-прежнему могут считывать по крайней мере одну копию данных.

|Состояние работы    |Описание|
|---------            |---------          |
|Обслуживается            |Windows восстанавливает виртуальный диск, например после добавления или удаления диска. После завершения восстановления виртуальный диск должен вернуться в состояние работоспособности ОК.|
|Неполный           |Устойчивость виртуального диска сокращается из-за сбоя или отсутствия одного или нескольких дисков. Однако отсутствующие диски содержат обновленные копии ваших данных.<br><br> **Action** (Действие). <br>1. повторно подключите все отсутствующие диски, замените неисправные диски и, если вы используете Локальные дисковые пространства, переведите в оперативный режим все серверы, находящиеся вне сети. <br>2. Если вы не используете Локальные дисковые пространства, затем выполните восстановление виртуального диска с помощью командлета [Repair-VirtualDisk](/powershell/module/storage/repair-virtualdisk?view=win10-ps) .<br> Локальные дисковые пространства автоматически запускает восстановление, если это необходимо, после повторного подключения или замены диска.|
|Деградация             |Устойчивость виртуального диска сокращается из-за сбоя или отсутствия одного или нескольких дисков и наличия устаревших копий данных на этих дисках. <br><br>**Action** (Действие). <br> 1. повторно подключите все отсутствующие диски, замените неисправные диски и, если вы используете Локальные дисковые пространства, переведите в оперативный режим все серверы, находящиеся вне сети. <br> 2. Если вы не используете Локальные дисковые пространства, затем выполните восстановление виртуального диска с помощью командлета [Repair-VirtualDisk](/powershell/module/storage/repair-virtualdisk?view=win10-ps) . <br>Локальные дисковые пространства автоматически запускает восстановление, если это необходимо, после повторного подключения или замены диска.|

### <a name="virtual-disk-health-state-unhealthy"></a>Состояние работоспособности виртуального диска: неработоспособное

Если виртуальный диск находится в **неработоспособном** состоянии работоспособности, некоторые или все данные на виртуальном диске в данный момент недоступны.

|Состояние работы    |Описание|
|---------            |--------   |
|No redundancy (Нет избыточности)|Данные виртуального диска потеряны из-за сбоя слишком большого числа дисков.<br><br>**Действие**: замените неисправные диски, а затем восстановите данные из резервной копии.|

### <a name="virtual-disk-health-state-informationunknown"></a>Состояние работоспособности виртуального диска: сведения/неизвестно

Виртуальный диск также может находиться в состоянии работоспособности **информации** (как показано в элементе панели управления дисковых пространств) или в **неизвестном** состоянии работоспособности (как показано в PowerShell), если администратор потратил виртуальный диск в автономный режим или отсоединился от виртуального диска.

|Состояние работы    |Причина отсоединения |Описание|
|---------            |---------       |--------   |
|Отсоединен             |По политике            |Администратор затратил виртуальный диск в автономном режиме или устанавливает для виртуального диска необходимость ручного вложения. в этом случае потребуется вручную подключать виртуальный диск при каждом перезапуске Windows.<br><br>**Действие**: Подключите виртуальный диск к сети. Чтобы сделать это, когда виртуальный диск находится в кластерном пуле носителей, в Диспетчер отказоустойчивости кластеров выберите **Storage**  >  **Пулы**носителей  >  **Виртуальные диски**, выберите виртуальный диск, на котором отображается состояние **Автономная работа** , а затем выберите **перевести в режим**«в сети». <br><br>Чтобы вернуть виртуальный диск в оперативный режим, если он не находится в кластере, откройте сеанс PowerShell от имени администратора и попробуйте выполнить следующую команду:<br><br> <code>Get-VirtualDisk \| Where-Object -Filter { $_.OperationalStatus -eq "Detached" } \| Connect-VirtualDisk</code><br><br>Чтобы автоматически присоединить все некластеризованные виртуальные диски после перезагрузки Windows, откройте сеанс PowerShell от имени администратора и выполните следующую команду:<br><br> <code>Get-VirtualDisk \| Set-VirtualDisk -ismanualattach $false</code>|
|            |Большинство дисков неработоспособны |Не удалось найти слишком много дисков, используемых этим виртуальным диском, или они отсутствуют или имеют устаревшие данные.   <br><br>**Action** (Действие). <br> 1. Подключите недостающие диски и, если вы используете Локальные дисковые пространства, подключитесь к сети серверов, которые находятся вне сети. <br> 2. После подключения всех дисков и серверов замените все неисправные диски. Дополнительные сведения см. в разделе [Служба работоспособности](../../failover-clustering/health-service-overview.md) . <br>Локальные дисковые пространства автоматически запускает восстановление, если это необходимо, после повторного подключения или замены диска.<br>3. Если вы не используете Локальные дисковые пространства, затем выполните восстановление виртуального диска с помощью командлета [Repair-VirtualDisk](/powershell/module/storage/repair-virtualdisk?view=win10-ps) .  <br><br>Если произошел сбой нескольких дисков, а виртуальные диски не были восстановлены между сбоями, все данные на виртуальном диске будут безвозвратно утеряны. В этом случае удалите виртуальный диск, создайте новый виртуальный диск, а затем выполните восстановление из резервной копии.|
|                     |Неполный |Недостаточно дисков для чтения виртуального диска.    <br><br>**Action** (Действие). <br> 1. Подключите недостающие диски и, если вы используете Локальные дисковые пространства, подключитесь к сети серверов, которые находятся вне сети. <br> 2. После подключения всех дисков и серверов замените все неисправные диски. Дополнительные сведения см. в разделе [Служба работоспособности](../../failover-clustering/health-service-overview.md) . <br>Локальные дисковые пространства автоматически запускает восстановление, если это необходимо, после повторного подключения или замены диска.<br>3. Если вы не используете Локальные дисковые пространства, затем выполните восстановление виртуального диска с помощью командлета [Repair-VirtualDisk](/powershell/module/storage/repair-virtualdisk?view=win10-ps) .<br><br>Если произошел сбой нескольких дисков, а виртуальные диски не были восстановлены между сбоями, все данные на виртуальном диске будут безвозвратно утеряны. В этом случае удалите виртуальный диск, создайте новый виртуальный диск, а затем выполните восстановление из резервной копии.|
| |Время ожидания|Подключение виртуального диска заняло слишком много времени <br><br> **Действие:** Это не должно происходить часто, так что вы можете попытаться проверить, проходит ли условие вовремя. Кроме того, можно попробовать отключить виртуальный диск с помощью командлета [Disconnect-VirtualDisk](/powershell/module/storage/disconnect-virtualdisk?view=win10-ps) , а затем повторно подключить его с помощью командлета [Connect-VirtualDisk](/powershell/module/storage/connect-virtualdisk?view=win10-ps) . |

## <a name="drive-physical-disk-states"></a>Состояния диска (физического диска)

В следующих разделах описываются состояния работоспособности диска. Диски в пуле представлены в PowerShell как объекты *физического диска* .

### <a name="drive-health-state-healthy"></a>Состояние работоспособности диска: Healthy

|Состояние работы    |Описание|
|---------            |---------          |
|OK|Диск исправен.|
|Обслуживается|Диск выполняет некоторые внутренние действия по обслуживанию. После завершения действия диск должен вернуться в состояние работоспособности *ОК* .|

### <a name="drive-health-state-warning"></a>Состояние работоспособности диска: предупреждение

Диск в состоянии "Предупреждение" может выполнять операции чтения и записи данных, но с ним возникла проблема.

|Состояние работы    |Описание|
|---------            |---------          |
|Связь потеряна|Диск отсутствует. Если вы используете Локальные дисковые пространства, это может быть вызвано тем, что сервер не работает.<br><br>**Действие**. Если вы используете Локальные дисковые пространства, переведите все серверы обратно в режим "в сети". Если это не решает проблему, подключите диск заново, замените или попытайтесь получить подробные диагностические сведения об этом диске, выполнив действия, описанные в разделе Устранение неполадок с использованием отчеты об ошибках Windows > [время ожидания физического диска](../../failover-clustering/troubleshooting-using-wer-reports.md#physical-disk-timed-out).|
|Удаление из пула|Дисковые пространства находятся в процессе удаления диска из пула носителей. <br><br> Это временное состояние. После завершения удаления, если диск все еще подключен к системе, он переходит в другое рабочее состояние (обычно ОК) в исходный пул.|
|Starting maintenance mode (Запуск режима обслуживания)|Дисковые пространства находятся в процессе перевода диска в режим обслуживания после того, как администратор переместит диск в режим обслуживания. Это временное состояние — диск скоро будет находиться в состоянии *обслуживания* .|
|В режиме обслуживания|Администратор поместил диск в режим обслуживания, прервать чтение и запись с диска. Обычно это выполняется перед обновлением встроенного по диска или при сбоях тестирования.<br><br>**Действие**. чтобы перевести диск в режим обслуживания, используйте командлет [Disable-сторажемаинтенанцемоде](/powershell/module/storage/disable-storagemaintenancemode?view=win10-ps) .|
|Stopping maintenance mode (Остановка режима обслуживания)|Администратор потратил диск из режима обслуживания, и дисковые пространства находятся в процессе перевода диска обратно в оперативный режим. Это временное состояние. диск скоро будет находиться в другом состоянии — идеально *работоспособном*.|
|Прогнозируемый сбой|Диск сообщил о том, что он близок к сбою.<br><br>**Действие**. Замените диск.|
|Ошибка ввода-вывода|Произошла временная ошибка при доступе к диску.<br><br>**Action** (Действие). <br>1. Если диск не переходит обратно в состояние " **ОК** ", можно попробовать использовать командлет [Reset-](/powershell/module/storage/reset-physicaldisk) Drive для очистки диска. <br> 2. Используйте [Repair-VirtualDisk](/powershell/module/storage/repair-virtualdisk) для восстановления устойчивости затронутых виртуальных дисков. <br>3. Если это не происходит, замените диск.|
|Временная ошибка|Произошла временная ошибка с диском. Обычно это означает, что диск не отвечает, но это также может означать, что раздел защиты дисковых пространств был ненадлежащим образом удален с диска. <br><br>**Action** (Действие). <br>1. Если диск не переходит обратно в состояние " **ОК** ", можно попробовать использовать командлет [Reset-](/powershell/module/storage/reset-physicaldisk) Drive для очистки диска. <br> 2. Используйте [Repair-VirtualDisk](/powershell/module/storage/repair-virtualdisk) для восстановления устойчивости затронутых виртуальных дисков. <br>3. Если это не происходит, замените диск или попытайтесь получить подробные диагностические сведения об этом диске, выполнив действия, описанные в разделе Устранение неполадок с помощью отчеты об ошибках Windows > [физическом диске не удалось подключиться к сети](../../failover-clustering/troubleshooting-using-wer-reports.md#physical-disk-failed-to-come-online).|
|Abnormal latency (Аномальная задержка)|Диск медленно работает, измеряемый служба работоспособности в Локальные дисковые пространства.<br><br>**Действие**. Если это не происходит, замените диск таким образом, чтобы не снижать производительность дисковых пространств в целом.

### <a name="drive-health-state-unhealthy"></a>Состояние работоспособности диска: Unhealthy;

Диск в неработоспособном состоянии не может выполнять операции записи или чтения.

|Состояние работы    |Описание|
|---------            |---------          |
|Не годен для использования|Этот диск не может использоваться дисковыми пространствами. Дополнительные сведения см. в разделе [Локальные дисковые пространства требования к оборудованию](storage-spaces-direct-hardware-requirements.md). Если вы не используете Локальные дисковые пространства, см. раздел [Общие сведения о дисковых пространствах](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831739(v=ws.11)#Requirements).|
|Split|Диск отделен от пула.<br><br>**Действие**: сбросьте диск, удалив все данные с диска и добавив его обратно в пул в качестве пустого диска. Для этого откройте сеанс PowerShell от имени администратора, запустите командлет [Reset-физический диск](/powershell/module/storage/reset-physicaldisk?view=win10-ps) и выполните команду [Repair-VirtualDisk](/powershell/module/storage/repair-virtualdisk?view=win10-ps). <br><br>Чтобы получить подробные диагностические сведения об этом диске, выполните действия, описанные в статье Устранение неполадок с помощью отчеты об ошибках Windows > [физическом диске не удалось подключиться к сети](../../failover-clustering/troubleshooting-using-wer-reports.md#physical-disk-failed-to-come-online).|
|Устаревшие метаданные|Дисковые пространства обнаружили старые метаданные на диске.<br><br>**Действие**: это временное состояние. Если диск не возвращается в значение "ОК", можно выполнить команду [Repair-VirtualDisk](/powershell/module/storage/repair-virtualdisk?view=win10-ps) , чтобы запустить операцию восстановления на затронутых виртуальных дисках. Если это не решит проблему, можно сбросить диск с помощью командлета [Reset-](/powershell/module/storage/reset-physicaldisk?view=win10-ps) Drive, очистить все данные с диска, а затем выполнить команду [Repair-VirtualDisk](/powershell/module/storage/repair-virtualdisk?view=win10-ps).|
|Нераспознанные метаданные|Дисковые пространства обнаружили нераспознанные метаданные на диске, что обычно означает, что диск имеет метаданные из другого пула.<br><br>**Действие**: чтобы очистить диск и добавить его в текущий пул, сбросьте диск. Чтобы сбросить диск, откройте сеанс PowerShell от имени администратора, запустите командлет [Reset-физический диск](/powershell/module/storage/reset-physicaldisk?view=win10-ps) и выполните команду [Repair-VirtualDisk](/powershell/module/storage/repair-virtualdisk?view=win10-ps).|
|Неисправный носитель|Диск вышел из строя и больше не будет использоваться дисковыми пространствами.<br><br>**Действие**. Замените диск. <br><br>Чтобы получить подробные диагностические сведения об этом диске, выполните действия, описанные в статье Устранение неполадок с помощью отчеты об ошибках Windows > [физическом диске не удалось подключиться к сети](../../failover-clustering/troubleshooting-using-wer-reports.md#physical-disk-failed-to-come-online).|
|Device hardware failure (Сбой оборудования устройства)|На этом диске произошел сбой оборудования. <br><br>**Действие**. Замените диск.|
|Обновление встроенного ПО|Windows обновляет встроенное по на диске. Это временное состояние, которое обычно длится менее минуты и в течение которого другие диски в пуле обрабатывают все операции чтения и записи. Дополнительные сведения см. в [статье обновление встроенного по диска](../update-firmware.md).|
|Запуск|Диск подготавливается к работе. Это должно быть временное состояние. После завершения подготовки диск должен перейти в другое рабочее состояние.|

## <a name="reasons-a-drive-cant-be-pooled"></a>Причины, по которым диски невозможно объединить в пул

Некоторые диски просто не готовы к работе в пуле носителей. Чтобы узнать, почему диск не подходит для объединения в пул, просмотрите `CannotPoolReason` свойство физического диска. Ниже приведен пример скрипта PowerShell для вывода свойства Каннотпулреасон:

```PowerShell
Get-PhysicalDisk | Format-Table FriendlyName,MediaType,Size,CanPool,CannotPoolReason
```

Ниже приведен пример выходных данных:

```
FriendlyName          MediaType          Size CanPool CannotPoolReason
------------          ---------          ---- ------- ----------------
ATA MZ7LM120HCFD00D3  SSD        120034123776   False Insufficient Capacity
Msft Virtual Disk     SSD         10737418240    True
Generic Physical Disk SSD        119990648832   False In a Pool
```

В следующей таблице подробно описаны все причины.

|Причина|Описание|
|---|---|
|В пуле|Диск уже принадлежит пулу носителей. <br><br>Диски могут принадлежать только одному пулу носителей за раз. Чтобы использовать этот диск в другом пуле носителей, сначала удалите его из существующего пула, который указывает дисковые пространства для перемещения данных на диск на другие диски в пуле. Или сбросьте диск, если он был отключен от пула без уведомления дисковых пространств. <br><br>Чтобы безопасно удалить диск из пула носителей, используйте команду [Remove-](/powershell/module/storage/remove-physicaldisk?view=win10-ps)Physical или перейдите к Диспетчер сервера > пулы **хранения файлов и служб хранилища**  >  **Storage Pools**, > **физические диски**, щелкните правой кнопкой мыши диск и выберите пункт **удалить диск**.<br><br>Чтобы сбросить диск, используйте [Reset-физический диск](/powershell/module/storage/reset-physicaldisk?view=win10-ps).|
|Неработоспособен|Диск находится в неработоспособном состоянии, его может потребоваться заменить.|
|Съемные носители|Диск классифицируется как съемный. <br><br>Дисковые пространства не поддерживают носители, распознаваемые Windows как съемные, например диски Blu-Ray. Хотя многие жесткие диски находятся в съемных слотах, в общем случае носители, которые *классифицируются* Windows как съемные, не подходят для использования с дисковыми пространствами.|
|Используется кластером|Диск в настоящее время используется отказоустойчивым кластером.|
|Вне сети|Диск находится в автономном режиме. <br><br>Чтобы перевести все автономные диски в оперативный режим и задать для чтения и записи, откройте сеанс PowerShell от имени администратора и используйте следующие скрипты:<br><br><code>Get-Disk \| Where-Object -Property OperationalStatus -EQ "Offline" \| Set-Disk -IsOffline $false</code><br><br><code>Get-Disk \| Where-Object -Property IsReadOnly -EQ $true \| Set-Disk -IsReadOnly $false</code>|
|Недостаточная емкость|Обычно это происходит, когда секции занимают свободное место на диске. <br><br>**Действие**: удалите все тома на диске, удалив все данные на диске. Одним из способов сделать это является использование командлета PowerShell с [открытым диском](/powershell/module/storage/clear-disk?view=win10-ps) .|
|Выполняется проверка|[Служба работоспособности](../../failover-clustering/health-service-overview.md#supported-components-document) проверяет, утвержден ли диск или встроенное по на диске для использования администратором сервера.|
|Сбой проверки|[Служба работоспособности](../../failover-clustering/health-service-overview.md#supported-components-document) не удалось проверить, утвержден ли диск или встроенное по на диске для использования администратором сервера.|
|Несоответствие встроенного ПО|Встроенное по на физическом диске не входит в список утвержденных версий встроенного по, указанных администратором сервера с помощью [Служба работоспособности](../../failover-clustering/health-service-overview.md#supported-components-document). |
|Несоответствие оборудования|Этот диск не входит в список утвержденных моделей хранения, указанных администратором сервера, с помощью [Служба работоспособности](../../failover-clustering/health-service-overview.md#supported-components-document).|

## <a name="additional-references"></a>Дополнительные ссылки

- [Локальные дисковые пространства](storage-spaces-direct-overview.md)
- [Требования к оборудованию Локальные дисковые пространства](storage-spaces-direct-hardware-requirements.md)
- [Общие сведения о кворуме кластеров и пулов](understand-quorum.md)
