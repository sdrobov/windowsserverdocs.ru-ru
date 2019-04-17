---
title: "Управление архивацией клиентского компьютера в Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b4776e8-9504-4b98-ae80-11da797d9819
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: d184c97e47f04b9d7434aaeb0d328761bcfac1c0
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="manage-client-computer-backup-in-windows-server-essentials"></a>Управление архивацией клиентского компьютера в Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
 
 Этот раздел содержит сведения об общих задачах архивации для клиентских компьютеров можно выполнить с помощью панели мониторинга Windows Server Essentials и содержит следующие разделы:  
  
-   [Как работает мастер исправления архивации базы данных](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_1)  
  
-   [Общие сведения о параметрах архивации компьютера](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_2)  
  
-   [Настройка архивации для клиентского компьютера](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_3)  
  
-   [Изменение времени, архивации по расписанию](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_4)  
  
-   [Изменение политики хранения архива компьютера](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_5)  
  
-   [Сброс параметров по умолчанию архивации в](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_6)  
  
-   [Использование средств исправления и восстановления](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_7)  
  
-   [Восстановление резервной копии базы данных](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_8)  
  
-   [Отключение архивации для компьютера](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_9)  
  
-   [Выполнение задания очистки архивации](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_10)  
  
-   [Просмотр оповещений на панели задач на клиентском компьютере](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_11)  
  
-   [Просмотр состояния архивации из панели запуска](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_12)  
  
-   [Остановка выполняемой архивации из панели запуска](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_13)  
  
-   [Запуск архивации из панели запуска](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_14)  
  
-   [Принцип работы архивации компьютера](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_15)  
  
-   [Советы по предотвращению потери данных из-за повреждения базы данных клиентской архивации](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_16)  
  
-   [Восстановить файлы и папки из архива клиентского компьютера](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_17)  
  
-   [Общие сведения об истории файлов](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_FileHistory)  
  
##  <a name="BKMK_1"></a>Как работает мастер исправления архивации базы данных  
 Если Windows Server Essentials обнаруживает ошибки в базе данных архивации, она отправляет уведомление о работоспособности и состояние оповещения изменяется на красное, указывающее на критическую ситуацию.  
  
 Для мониторинга Windows Server Essentials щелкните значок состояния оповещения, чтобы просмотреть уведомление об ошибке резервной копии базы данных. Уведомление содержит **восстановления** кнопку, которая запускает мастер исправления архивации базы данных. Мастер может занять несколько часов.  
  
 Мастер проверяет базу данных архивации для выбранного компьютера и пытается восстановить базу данных при обнаружении ошибок. В некоторых случаях мастер не может исправить всю базу данных архивации. Перед запуском мастера убедитесь, что все внешние жесткие диски, используемые на сервере подключены к серверу, включены и функционируют должным образом. Ошибка резервного копирования базы данных может быть устранена автоматически посредством повторного подключения отсутствующего жесткого диска.  
  
> [!CAUTION]
>  Перед попытки восстановления следует создать резервную копию базы данных. В зависимости от типа ошибок, обнаруженных в базе данных архивации мастер не может иметь возможность восстановить некоторые архивы. Некоторые или все архивы могут быть полностью утеряны.  
  
##  <a name="BKMK_2"></a>Общие сведения о параметрах архивации компьютера  
 После настройки архивации для клиентских компьютеров можно указать другой временной промежуток для проведения архивации. Аналогичным образом можно указать хранения резервной копии больше или меньше времени, чем значение по умолчанию.  
  
 **Восстановить значения по умолчанию** позволяет сбросить окно архивации и хранения политику по умолчанию, указанные во время начальной настройки архивации.  
  
 По умолчанию используются следующие:  
  
|Параметр архивации|По умолчанию|Описание|  
|--------------------|-------------|-----------------|  
|Время начала|6:00 PM|Указывает время начала ежедневной архивации. Рекомендуется установить здесь время, когда сотрудники не пользуются свои компьютеры.|  
|Время окончания|09:00:00|Указывает время, которое необходимо завершить архивацию. Если для резервного копирования в течение заданного не требуется, она использует только время, необходимое для успешной архивации компьютера.|  
|Хранить ежедневные архивы|5 дней|Указывает количество дней, в которых хранятся ежедневные архивы. Например при значении по умолчанию сохраняются 5 ежедневных архивов. На шестой день и каждый следующий день удаляется самый старый файл ежедневной архивации удаляется.|  
|Хранить еженедельные архивы|4 недель|Указывает число недель, в течение которых хранится последний архив за неделю. Например используя параметры по умолчанию, сохраняются 4 еженедельных архива. На пятой неделе и каждой следующей неделе удаляется самый старый еженедельный архив удаляется.|  
|Хранить ежемесячные архивы|6 месяцев|Указывает число месяцев, в течение которых хранится последний архив за месяц. Например при значении по умолчанию сохраняются 6 ежемесячных архивов. На седьмой месяц и каждый следующий месяц удаляется самый старый ежемесячный архив удаляется.|  
  
##  <a name="BKMK_3"></a>Настройка архивации для клиентского компьютера  
 Если архивации отключена, архивацию компьютера можно настроить с помощью панели мониторинга. При настройке архивации для компьютера, вы можете архивировать все данные на компьютере или выбрать те тома и папки, которые вы хотите архивировать.  
  
> [!NOTE]
>  Компьютер должен быть подключен к сети для настройки архивации.  
  
> [!IMPORTANT]
>   Windows Server Essentials не поддерживает резервное копирование и восстановление динамических дисков на клиентских компьютерах.  
  
#### <a name="to-set-up-backup-for-a-client-computer"></a>Порядок настройки архивации для клиентского компьютера  
  
1.  Откройте **панели мониторинга**, а затем нажмите кнопку **устройств** вкладку.  
  
2.  Щелкните имя клиентского компьютера, который вы хотите настроить архивацию, а затем в **задачи** панели, щелкните **Настройка резервного копирования для компьютера**.  
  
    > [!NOTE]
    >  Если архивация уже настроена для клиентского компьютера, **настроить архивацию этого компьютера** указан в **задачи** области вместо **Настройка резервного копирования для компьютера**.  
  
3.  Мастер настройки архивации вы можете архивировать все папки или выбрать только определенные папки, которые вы хотите архивировать. Следуйте инструкциям мастера.  
  
4.  Нажмите кнопку **закрыть** после настройки архивации для компьютера.  
  
### <a name="critical-system-files"></a>Критически важные системные файлы  
 При установке операционной системы Windows, программа установки создает папки на жестком диске, куда помещает файлы, необходимые для запуска и выполнения системы. Критическим системным файлам относятся файлы с расширениями файл .sys, .ocx, .dll и .exe. Некоторые из этих файлов являются шрифтами True Type. Кроме того файлы состояния системы, такие как системный реестр s, необходимы для правильной работы операционной системы.  
  
### <a name="find-the-file-you-are-looking-for"></a>Найдите файл, который вы ищете.  
 С помощью существующего архива можно восстановить все папки для компьютера, несколько файлов и папок, или отдельный файл или папку.  
  
 После выбора архива, который вы хотите использовать для восстановления из файла резервной копии доступен для чтения и отображаются все файлы и папки. Вы можете выполнить детализацию до определенного файла или папки, дважды щелкнув папку верхнего уровня и опускаясь по иерархии папок до нужного файла, который вы ищете.  
  
### <a name="why-am-i-unable-to-select-some-items"></a>Почему не удается выбрать некоторые элементы?  
 Флажок в меню выбора **выбрать, какие элементы для резервного копирования страницы** может иметь разное состояние для каждой папки. Если флажок отображается как:  
  
-   **Выбранный**, соответствующая папка и ее содержимое выбраны для архивации.  
  
-   **Не выбрано**, соответствующая папка и ее содержимое исключены из архивации.  
  
-   **Сплошной**, соответствующая папка выбрана для архивации, но один или несколько элементов в этой папке исключены из архивации.  
  
 Если не удается выбрать конкретную папку:  
  
-   Возможно, том настроен для архивации, но отключен. Это характерно для съемный USB-накопителей. Отключенные тома отображаются шрифтом серого цвета.  
  
-   Резервное копирование данных можно только с локального диска, который отформатирован в файловой системе NTFS. Диски в формате FAT (включая FAT32) или файловые системы ReFS не отображаются в списке диски для архивации.  
  
> [!IMPORTANT]
>  Служба теневого копирования томов (VSS) не поддерживает создание теневой копии виртуальных тома и узла-тома в одном наборе моментальных снимков. VSS поддерживает создание моментальных снимков томов на виртуальном жестком диске (VHD), когда требуется архивация виртуального тома. Дополнительные сведения см. в разделе [обслуживание и архивация виртуальных жестких дисков](https://go.microsoft.com/fwlink/p/?LinkId=256577).  
  
##  <a name="BKMK_4"></a>Изменение времени, архивации по расписанию  
 Процесс архивации следует планировать на такое время, когда за компьютерами работает минимальное число пользователей. Это обычно во время поздний вечер или раннее утро. Время по умолчанию для резервного копирования — 6:00 до 9:00 по. Сервер пытается выполнить архивацию клиентских компьютеров только в заданный промежуток времени.  
  
 Тем не менее если эти традиционно нерабочие часы ваш бизнеса активен, может потребоваться изменить эти параметры по умолчанию.  
  
#### <a name="to-change-the-time-that-backup-is-scheduled-to-run"></a>Чтобы изменить время запланировано резервное копирование  
  
1.  Откройте серверную **мониторинга**, а затем нажмите кнопку **устройств**.  
  
2.  В **задачи устройств**, нажмите кнопку **параметры настройки архивации компьютеров и журнала файлов**.  
  
    > [!NOTE]
    >  В Windows Server Essentials, эта задача была переименована **задачи архивации клиентских компьютеров**.  
  
3.  В **параметры архивации клиентских компьютеров и средства**на **резервного копирования компьютера** вкладку, можно изменить время начала и окончания, в соответствии с потребностями.  
  
4.  Нажмите кнопку **применить**, а затем нажмите кнопку **ОК**.  
  
##  <a name="BKMK_5"></a>Изменение политики хранения архива компьютера  
 Со временем на сервере накапливаются ежедневные архивы со всех компьютеров. Позволяет управлять этими архивами, Windows Server Essentials помогает вам управлять базой данных архивации компьютеров. Можно настроить количество сохраняемых архивов для всех компьютеров.  
  
 Политика хранения архивов определяет, сколько времени хранится архив перед удалением в процессе очистки архивации. Очистка архивации выполняется в 23:59 каждую субботу. Она удаляет все архивы, выходящие за рамки политики хранения архивов. По умолчанию для политики хранения архивов используются следующие:  
  
-   **Хранить ежедневные архивы 5 дней.** Первый архив за день сохраняется в качестве ежедневного архива. Через 5 дней самый старый ежедневный архив удаляется во время очистки.  
  
-   **Хранить еженедельные архивы 4 недели.** Первый архив за неделю сохраняется в качестве еженедельного архива. Через 4 недели самый старый еженедельный архив удаляется во время очистки.  
  
-   **Хранить ежемесячные архивы 6 месяцев.** Первый архив за месяц сохраняется в качестве ежемесячного архива. Через 6 месяцев самый старый ежемесячный архив удаляется во время очистки.  
  
#### <a name="to-change-the-computer-backup-retention-policy"></a>Изменение политики хранения архива компьютера  
  
1.  Откройте **мониторинга**.  
  
2.  Нажмите кнопку **устройств**.  
  
3.  В **задачи устройств** панели, щелкните **параметры настройки архивации компьютеров и журнала файлов**.  
  
    > [!NOTE]
    >  В Windows Server Essentials, эта задача была переименована **задачи архивации клиентских компьютеров**.  
  
4.  В **параметры архивации клиентских компьютеров и средства**в **политика хранения архивов клиентских компьютеров** статьи, внесите изменения в политике хранения, которая соответствует вашим потребностям.  
  
5.  Закончив, нажмите кнопку **ОК** применить изменения и закрыть диалоговое окно. Эта обновленная политика хранения будет применяться при выполнении следующей очистки архивации.  
  
    > [!NOTE]
    >  Эта обновленная политика хранения применяется ко всем клиентским компьютерам в сети, настроенным для архивации.  
  
##  <a name="BKMK_6"></a>Сброс параметров по умолчанию архивации в  
 После настройки архивации для клиентских компьютеров, администратор сети мог указать другой период времени. Аналогичным образом администратор может указать хранения резервной копии больше или меньше времени, чем значение по умолчанию. **Восстановить значения по умолчанию** позволяет сбросить окно архивации и хранения политику по умолчанию, указанные во время начальной настройки архивации.  
  
 По умолчанию используются следующие:  
  
-   Время начала архивации: 18:00 по  
  
-   Время окончания: 9:00 AM  
  
-   Количество дней, в которых хранятся ежедневные архивы: 5 дней  
  
-   Число недель, в течение которых хранится последний архив за неделю: 4 недель  
  
-   Число месяцев, в течение которых хранится последний архив за месяц: 6 месяцев  
  
#### <a name="to-reset-computer-backup-to-the-default-settings"></a>Чтобы сбросить архивную копию значения по умолчанию  
  
1.  Откройте **панели мониторинга**, а затем откройте **устройств** страницы.  
  
2.  В **задачи устройств**, нажмите кнопку **параметры настройки архивации компьютеров и журнала файлов**.  
  
    > [!NOTE]
    >  В Windows Server Essentials щелкните **задачи архивации клиентских компьютеров**.  
  
3.  На **резервного копирования компьютера** вкладке **средства и параметры компьютера и резервного копирования клиентских** щелкните **восстановить значения по умолчанию**.  
  
    > [!NOTE]
    >  Может потребоваться записать настроенные и расписание параметры политики хранения, так как они будут потеряны при сбросе в значения по умолчанию.  
  
4.  Нажмите кнопку **применить**, а затем нажмите кнопку **ОК**.  
  
##  <a name="BKMK_7"></a>Использование средств исправления и восстановления  
 **Исправление архивов:** Если база данных архивации компьютеров повреждена или ее использование невозможно по какой-либо причине, можно попытаться восстановить базу данных с помощью мастера резервного копирования базы данных восстановления. Этот мастер анализирует файлы архивов, определяя наличие проблем, которые можно исправить. Мастер пытается исправить все найденные проблемы.  
  
> [!WARNING]
>  Если проблема не устранена, мастер может удалить файл архива компьютера.  
  
 **Восстановление компьютера:** можно создать загрузочный USB-накопитель флэш-памяти для восстановления компьютера с помощью существующей резервной копии. Необходимо использовать USB-накопитель флэш-памяти объемом 1 ГБ или больше. После создания загрузочного USB-накопитель флэш-памяти можно вставить его в компьютер, который вы хотите восстановить, а затем загрузите флэш-накопитель USB, чтобы начать процесс восстановления полной системы.  
  
##  <a name="BKMK_8"></a>Восстановление резервной копии базы данных  
 Если вы получаете оповещение, сообщающее о том, что базы данных архивации компьютера есть проблемы, можно попытаться восстановить его.  
  
#### <a name="to-repair-the-backup-database"></a>Восстановление резервной копии базы данных  
  
1.  Откройте **мониторинга**.  
  
2.  Нажмите кнопку **устройств**.  
  
3.  В **задачи устройств** панели, щелкните **параметры настройки архивации компьютеров и журнала файлов.**  
  
    > [!NOTE]
    >  В Windows Server Essentials щелкните **задачи архивации клиентских компьютеров**.  
  
4.  В **параметры архивации клиентских компьютеров и средства**, нажмите кнопку **средства** вкладку.  
  
5.  В **исправление архивов** щелкните **восстановления теперь**. Откроется мастер резервного копирования базы данных восстановления.  
  
6.  Следуйте инструкциям в мастере архивации базы данных восстановления.  
  
7.  В зависимости от размера является резервной копии базы данных, восстановления базы данных может занять несколько часов. Нажмите кнопку **закрыть**и нажмите кнопку **ОК** закрыть **параметры настройки архивации компьютеров и журнала файлов** страницы.  
  
    > [!NOTE]
    >  В Windows Server Essentials щелкните **параметры архивации клиентских компьютеров и средства**.  
  
#### <a name="to-review-the-results-of-the-backup-database-repair"></a>Просмотр результатов исправления базы данных архивации  
  
1.  Откройте **мониторинга**.  
  
2.  Нажмите кнопку **устройств**.  
  
3.  В **задачи устройств** панели, щелкните **параметры настройки архивации компьютеров и журнала файлов.**  
  
    > [!NOTE]
    >  В Windows Server Essentials щелкните **задачи архивации клиентских компьютеров**.  
  
4.  В **параметры архивации клиентских компьютеров и средства**, нажмите кнопку **средства** вкладку.  
  
5.  Результаты отображаются в **исправление архивов** раздела.  
  
##  <a name="BKMK_9"></a>Отключение архивации для компьютера  
 Используйте информационную панель, чтобы быстро архивацию для компьютеров в сети.  
  
#### <a name="to-disable-backup-for-a-computer"></a>Отключение архивации для компьютера  
  
1.  Откройте **мониторинга**.  
  
2.  Нажмите кнопку **устройств** вкладку.  
  
3.  Щелкните имя компьютера, для которого требуется отключить архивацию.  
  
4.  В области задач щелкните **Настройка архивации для компьютера**. Откроется мастер настройки архивации.  
  
5.  Нажмите кнопку **отключить архивацию этого компьютера**, а затем выберите, хотите ли вы сохранить или удалить существующие файлы архивов.  
  
6.  Нажмите кнопку **сохранить изменения**, а затем нажмите кнопку **закрыть**.  
  
 Сведения о том, как включить архивацию для компьютера, после отключения резервного копирования см. в разделе [настройки архивации для клиентского компьютера](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_3).  
  
##  <a name="BKMK_10"></a>Выполнение задания очистки архивации  
 Задачи очистки архивации клиентских компьютеров запланирован запуск в 23:59 каждую субботу, когда все операции архивации выполнены. Задача очистки удаляет архив из базы данных архивации компьютера клиента в соответствии с политикой хранения архивов. Ниже перечислены параметры по умолчанию для политики хранения архива  
  
-   Количество дней, в которых хранятся ежедневные архивы: 5 дней  
  
-   Число недель, в течение которых хранится последний архив за неделю: 4 недель  
  
-   Число месяцев, в течение которых хранится последний архив за месяц: 6 месяцев  
  
 Сведения об изменении политики хранения архивов см. в разделе [изменение политики хранения архива компьютера](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md#BKMK_5).  
  
#### <a name="to-run-the-client-backup-database-cleanup-task"></a>Порядок запуска задачи очистки базы данных архивации клиента  
  
1.  Войдите на сервер с учетной записью администратора и пароль.  
  
2.  На сервере, откройте **планировщик**. Можно получить доступ к программе планировщика из **Администрирование** консоли.  
  
3.  В планировщике заданий, разверните узел **Библиотека планировщика заданий**, разверните **Microsoft**, разверните **Windows**, а затем нажмите кнопку **Windows Server Essentials**.  
  
4.  Нажмите кнопку **Очистка архивации** задач, а затем нажмите кнопку **запуска** в **действия** области. Состояние меняется на **под управлением** до завершения задачи.  
  
##  <a name="BKMK_11"></a>Просмотр оповещений на панели задач на клиентском компьютере  
 Можно получить уведомление архивации на панели задач на компьютере по следующим причинам:  
  
-   Запущена архивация.  
  
-   Архивация завершена.  
  
-   Не последний успешный архив. Число дней с момента последней успешной архивации включается в уведомлении.  
  
-    Windows Server Essentials: компьютер добавлен новый том. Администратору сети необходимо запустить мастер настройки резервного копирования, чтобы включить или исключить тома в будущих операциях архивации.  
  
##  <a name="BKMK_12"></a>Просмотр состояния архивации из панели запуска  
 Использование панели запуска для просмотра кратких резервного копирования сведений о состоянии компьютера.  
  
> [!TIP]
>  Для быстрого состоянии переместите курсор на значок панели запуска в области уведомлений рабочего стола. Состояние архивации отображается во всплывающей подсказке.  
  
#### <a name="to-view-status-of-a-backup-for-your-computer"></a>Просмотр состояния архивации для компьютера  
  
1.  Войдите **запуска** с помощью имени пользователя и пароля.  
  
2.  Нажмите кнопку **резервного копирования**.  
  
3.  В **свойства архивации** диалогового окна **резервное копирование состояния** состояние архивации отображается.  
  
    -   **Предыдущие архивные копии отсутствуют**: резервного копирования либо еще не выполнялась, или был удален журнал архивации.  
  
    -   **Резервного копирования, ожидающих**: операция архивации ожидает другого процесса для выполнения на сервере.  
  
    -   **Подключение**: процесс архивации подключается к серверу.  
  
    -   **Не удается подключиться**: резервное копирование не удается подключиться к поставщик службы архивации Windows Server клиентского компьютера.  
  
        > [!NOTE]
        >  В Windows Server Essentials, эта служба была переименована в службу управления клиентского компьютера Windows Server Essentials.  
  
    -   **Выполняется архивация**: отображает процент завершения архивации.  
  
    -   **Архивация отменена**: Дата и время запуска архивации, если вами или администратором сети.  
  
    -   **Резервное копирование выполнено успешно**: Дата и время запуска архивации, если резервное копирование выполнено успешно.  
  
    -   **Архивация не была завершена**: Дата и время запуска архивации, если резервная копия не была успешно завершена.  
  
    -   **Архивация завершилась со сбоем**: Дата и время запуска архивации, если резервная копия не была успешно завершена.  
  
4.  Нажмите кнопку **ОК** закрыть **свойства архивации** диалоговое окно.  
  
##  <a name="BKMK_13"></a>Остановка выполняемой архивации из панели запуска  
 Можно легко остановить архивацию, выполняемая в данный момент.  
  
#### <a name="to-stop-a-backup-in-progress"></a>Остановка выполняемой архивации  
  
1.  Откройте **запуска**.  
  
    > [!NOTE]
    >  При получении запроса выполните вход в **запуска** с помощью имени пользователя и пароля.  
  
2.  Нажмите кнопку **резервного копирования**.  
  
3.  В **свойства архивации** диалогового окна **резервное копирование состояния** раздел, **начать архивацию** кнопки изменяется на **резервного копирования Stop** при резервное копирование выполняется. Нажмите кнопку **резервного копирования Stop**, а затем нажмите кнопку **Да** для подтверждения. Резервного копирования будет продолжать выполняться, пока вы выберите **Да**.  
  
4.  При остановке выполняемой архивации ее состояние изменяется на **архивация отменена** с указанием даты и времени запуска архивации. Если вместо этого отображается состояние **успешно**, **неполный**, или **сбой**, последняя архивация уже завершилась.  
  
5.  Нажмите кнопку **ОК** закрыть **свойства архивации** диалоговое окно.  
  
##  <a name="BKMK_14"></a>Запуск архивации из панели запуска  
 Могут возникнуть ситуации, когда требуется создать резервную копию файлов и настройки папки еще до время плановой архивации на сервере. Панель запуска позволяет вручную запустить архивацию компьютеров.  
  
#### <a name="to-start-a-backup"></a>Запуск архивации  
  
1.  Откройте **запуска**.  
  
    > [!NOTE]
    >  При получении запроса выполните вход в **запуска** с помощью имени пользователя и пароля.  
  
2.  Нажмите кнопку **резервного копирования**.  
  
3.  В **свойства архивации** диалогового окна **резервное копирование состояния** статьи, нажмите кнопку **начать архивацию**, а затем нажмите кнопку **ОК**.  
  
4.  Введите описание архива и нажмите кнопку **ОК**. Состояние меняется на **Запуск архивации**, а затем в **резервного копирования, в процессе** с указанием процента выполнения.  
  
5.  После запуска архивации кнопка меняется на **резервного копирования Stop**. Если архивация и необходимо остановить ее, нажмите кнопку **резервного копирования Stop**, а затем нажмите кнопку **Да**. При остановке выполняемой архивации ее состояние изменяется на **архивация отменена** с указанием даты и времени запуска архивации.  
  
6.  При успешном завершении архивации ее состояние изменяется на **резервное копирование выполнено успешно** с указанием даты и времени запуска выполненной архивации.  
  
7.  Нажмите кнопку **ОК** закрыть **свойства архивации** диалоговое окно.  
  
##  <a name="BKMK_15"></a>Принцип работы архивации компьютера  
 Выполняются следующие действия во время резервного копирования в день.  
  
-   Сетевые компьютеры архивируются один за другим.  
  
-   Выполняемая в данный момент завершается, даже если закрыть окно резервного копирования.  
  
-   Устанавливаются обновления Windows, и перезапускается Windows Server Essentials (при необходимости).  
  
-   В воскресенье выполняется очистка архивации.  
  
> [!IMPORTANT]
>  Служба теневого копирования томов (VSS) не поддерживает создание теневой копии виртуальных тома и узла-тома в одном наборе моментальных снимков. VSS поддерживает создание моментальных снимков томов на виртуальном жестком диске (VHD), когда требуется архивация виртуального тома. Дополнительные сведения см. в разделе [обслуживание и архивация виртуальных жестких дисков](https://go.microsoft.com/fwlink/p/?LinkId=256577).  
  
##  <a name="BKMK_16"></a>Советы по предотвращению потери данных из-за повреждения базы данных клиентской архивации  
 Если базы данных клиентской архивации повреждена, вы можете потерять критически важных данных.  
  
 Чтобы предотвратить потерю данных из базы данных клиентской архивации, учитывайте следующее:  
  
-   Предусмотрите дополнительный метод архивации базы данных клиентской архивации. Например в зависимости от версии Windows Server Essentials выполняется, используйте архивации сервера, оперативной резервной копии или архивации Microsoft Azure для резервного копирования базы данных.  
  
    > [!IMPORTANT]
    >  Обязательно выберите резервную копию всех файлов в **архивация клиентских компьютеров** папки.  
  
-   В случае, если необходимо восстановить базу данных, не забудьте восстановить все файлы в **архивация клиентских компьютеров** папки. Если вам не удается восстановить все файлы, может возникнуть несогласованность базы данных.  
  
-   Перед очисткой или восстановлением базы данных клиентской архивации, убедитесь, что остановлены все архивации клиентских компьютеров, которые в данный момент выполняются.  
  
     Если вы используете Windows Server Essentials, следует также остановить службу архивации клиентских компьютеров Windows Server и поставщик службы архивации Windows Server клиентского компьютера.  
  
     Если вы используете Windows Server Essentials, следует также остановить службу архивации компьютеров Windows Server.  
  
     После завершения операции восстановления перезапустите службу.  
  
##  <a name="BKMK_17"></a>Восстановить файлы и папки из архива клиентского компьютера  
 Можно просмотреть и восстановить отдельные файлы и папки из резервной копии.  
  
> [!NOTE]
>  Не удается восстановить файлы и папки на клиентском компьютере с помощью панели мониторинга на сервере. Необходимо открыть панель мониторинга на клиентском компьютере, для завершения задачи.  
  
> [!IMPORTANT]
>  Нельзя восстановить файлы и папки на жестком диске, которая была настроена в качестве динамического диска.  
  
#### <a name="to-restore-files-and-folders"></a>Чтобы восстановить файлы и папки  
  
1.  Откройте **мониторинга** на клиентском компьютере.  
  
2.  Нажмите кнопку **устройств** вкладку.  
  
3.  Выберите компьютер, для которого требуется восстановить файлы и папки, а затем нажмите кнопку **восстановить файлы или папки компьютера** в **задачи** области. Откроется окно мастера восстановления файлов и папок.  
  
4.  Следуйте инструкциям мастера.  
  
##  <a name="BKMK_FileHistory"></a>Общие сведения об истории файлов  
 Компонент истории файлов Windows Server Essentials автоматически выполняет архивацию файлов, которые находятся в папках библиотеки, контакты, рабочего стола и "Избранное" сетевых компьютеров с поддержкой истории файлов. Если оригинал потеряна, поврежден или удален, их можно восстановить. Кроме того, можно найти различные версии файлов на определенный момент времени. Со временем будет полная история ваших файлов.  
  
 В Windows Server Essentials, вы можете настроить параметры истории файлов на **истории файлов** страница **параметры архивации клиентских компьютеров и средства**.  
  
 В Windows Server Essentials, вы можете настроить параметры истории файлов, перейдя в раздел **пользователей** вкладки, а затем выбрав **изменение параметра истории файлов** задач.  
  
 Страница истории файлов содержит следующие параметры:  
  
|Параметр архивации|По умолчанию|Описание|  
|--------------------|-------------|-----------------|  
|Включить / отключить|На|История файлов включена по умолчанию при установке Windows Server Essentials.|  
|Данные архивации|Документы и рабочий стол|Существует три предварительно настроенных параметра, которые позволяют указать различные решения для резервного копирования. Вы можете выбрать один из следующих вариантов:<br /><br /> -Документов и рабочего стола<br /><br /> -Все библиотеки, рабочий стол, контакты и Избранное<br /><br /> -Все данные библиотек, рабочего стола, контактов и избранного, за исключением данных Видеотеки, Фонотеки и галереи|  
|Частота резервного копирования|Каждый час|Указывает, как часто истории файлов архивирует выбранные данные. Можно выбрать из нескольких вариантов диапазоне от каждые 10 минут до ежедневного.|  
|Срок хранения копий|1 год|Указывает количество времени, истории файлов сохраняет копию резервной копии.|  
  
 Сведения о проблемах с историей файлов см. в разделе [Устранение неполадок истории файлов](../support/Troubleshoot-File-History-in-Windows-Server-Essentials.md).  
  
## <a name="see-also"></a>См. также:  
  
-   [Управление архивацией и восстановлением](Manage-Backup-and-Restore-in-Windows-Server-Essentials.md)  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)  
  
-   [Использование Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)