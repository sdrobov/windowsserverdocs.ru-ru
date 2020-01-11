---
title: Устранение ошибки с кодом события 50
description: Описание устранения неполадок с сообщением об ошибке с кодом 50
author: Deland-Han
manager: dcscontentpm
audience: ITPro
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: 202e0604fc492ff72cd1794bc8197a12c1ab9163
ms.sourcegitcommit: 8cf04db0bc44fd98f4321dca334e38c6573fae6c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654385"
---
# <a name="troubleshoot-the-event-id-50-error-message"></a>Устранение ошибки с кодом события 50

##  <a name="symptoms"></a>Симптомы

При записи данных на физический диск в журнал системных событий могут регистрироваться следующие два сообщения о событиях: 

```
Event ID: 50 
Event Type: Warning 
Event Source: Ftdisk 
Description: {Lost Delayed-Write Data} The system was attempting to transfer file data from buffers to \Device\HarddiskVolume4. The write operation failed, and only some of the data may have been written to the file.
Data: 
0000: 00 00 04 00 02 00 56 00 
0008: 00 00 00 00 32 00 04 80 
0010: 00 00 00 00 00 00 00 00 
0018: 00 00 00 00 00 00 00 00 
0020: 00 00 00 00 00 00 00 00 
0028: 11 00 00 80 
```

```
Event ID: 26 
Event Type: Information
Event Source: Application Popup
Description: Windows - Delayed Write Failed : Windows was unable to save all the data for the file \Device\HarddiskVolume4\Program Files\Microsoft SQL Server\MSSQL$INSTANCETWO\LOG\ERRORLOG. The data has been lost. This error may be caused by a failure of your computer hardware or network connection.

Please try to save this file elsewhere.
```

Эти сообщения с ИДЕНТИФИКАТОРами событий означают то же самое и генерируются по тем же причинам. В рамках этой статьи описывается только сообщение с кодом события 50.

> [!NOTE] 
> Устройство и путь в описании и конкретные шестнадцатеричные данные будут различаться. 

##  <a name="more-information"></a>Дополнительные сведения

Сообщение об ошибке с ИДЕНТИФИКАТОРом 50 регистрируется в журнале, если при попытке Windows записать данные на диск возникает общая ошибка. Эта ошибка возникает, когда Windows пытается зафиксировать данные из диспетчера кэша файловой системы (не из кэша на уровне оборудования) на физическом диске. Это поведение является частью управления памятью Windows. Например, если программа отправляет запрос на запись, запрос записи кэшируется диспетчером кэша, и программа сообщает о том, что запись выполнена успешно. На более позднем этапе диспетчер кэша пытается выполнить отложенную запись данных на физический диск. Когда диспетчер кэша пытается зафиксировать данные на диске, происходит ошибка записи данных, а данные удаляются из кэша и удаляются. Кэширование обратной записи повышает производительность системы, но в результате потери отложенных ошибок записи могут возникать потери данных и потеря целостности тома.

Важно помнить, что не все операции ввода-вывода буферизованы диспетчером кэша. Программы могут устанавливать флаг FILE_FLAG_NO_BUFFERING, который обходит диспетчер кэша. Когда SQL выполняет критически важные операции записи в базу данных, этот флаг устанавливается, чтобы гарантировать завершение транзакции непосредственно на диск. Например, некритическая запись в файлы журнала выполняет буферизованный ввод-вывод для повышения общей производительности. Сообщение о событии с кодом 50 никогда не происходит из-за небуферизованного ввода-вывода.

Существует несколько различных источников для сообщения о событии с ИДЕНТИФИКАТОРом 50. Например, сообщение о событии с ИДЕНТИФИКАТОРом 50, зарегистрированное в источнике MRxSmb, возникает в случае проблемы с сетевым подключением с перенаправителя. Чтобы избежать неправильного выполнения действий по устранению неполадок, ознакомьтесь с сообщением о событии с кодом 50, чтобы убедиться в том, что оно относится к неполадке дискового ввода-вывода и что эта статья применима.

Сообщение с кодом события 50 аналогично событию с идентификатором 9 и сообщением Event с кодом 11. Несмотря на то, что ошибка не так серьезна, как ошибка, обозначенная событием с ИДЕНТИФИКАТОРом 9, и сообщением Event с кодом 11, можно использовать те же методы устранения неполадок для сообщения с кодом события 50, что и для события с идентификатором 9, и сообщения события с кодом 11. Однако следует помнить, что все в стеке может вызвать потерю, отложенные операции записи, такие как драйверы фильтров и драйверы мини-портов. 

Вы можете использовать двоичные данные, связанные с любыми сопутствующими ошибками (обозначенными в сообщении об ошибке с кодом 9, 11, 51 или другими сообщениями), чтобы помочь вам в определении проблемы.

###  <a name="how-to-decode-the-data-section-of-an-event-id-50-event-message"></a>Декодирование раздела данных сообщения о событии с ИДЕНТИФИКАТОРом 50 

При декодировании раздела данных в примере сообщения о событии с ИДЕНТИФИКАТОРом 50, включенном в раздел "Summary", вы увидите, что попытка выполнить операцию записи завершилась неудачей, так как устройство занято и данные потеряны. В этом разделе описано, как декодировать это событие с кодом 50. 

В следующей таблице показано, что представляет каждое смещение этого сообщения: 

|оффсетленгсвалуес|Продолжительность|Значения|
|-----------|------------|---------|
|0x00|2|Не используемые|
|0x02|2|Размер данных дампа = 0x0004|
|0x04|2|Число строк = 0x0002|
|0x06|2|Смещение строк|
|0x08|2|Категория события|
|0x0c|추가를 클릭합니다.|Код ошибки NTSTATUS = 0x80040032 = IO_LOST_DELAYED_WRITE|
|0x10|8|Не используемые|
|0x18|8|Не используемые|
|0x20|8|Не используемые|
|0x28|추가를 클릭합니다.|Код ошибки состояния NT|

#### <a name="key-sections-to-decode"></a>Основные разделы для декодирования

**Код ошибки**

В примере в разделе "Сводка" код ошибки указан во второй строке. Эта строка начинается с "0008:" и включает последние четыре байта в этой строке: 0008:00 00 00 00 32 00 04 80 в этом случае код ошибки — 0x80040032. Следующий код является кодом ошибки 50 и одинаковым для всех сообщений Event ID 50: IO_LOST_DELAYED_WRITEWARNINGNote при преобразовании шестнадцатеричных данных в сообщение с ИДЕНТИФИКАТОРом события в код состояния Помните, что значения представлены в формат с прямым порядком байтов.

**Целевой диск**

Диск, на который была предпринята попытка записи, можно найти с помощью символьной ссылки, указанной в разделе "Описание" сообщения Event ID, например: \Device\HarddiskVolume4. Чтобы получить дополнительные сведения о том, как определить диск, щелкните следующий номер статьи базы знаний Майкрософт: [159865](/EN-US/help/159865) . как отличить физическое дисковое устройство от сообщения о событии

**Конечный код состояния**

Последний код состояния — это наиболее важный фрагмент информации в сообщении с кодом события 50. Это код ошибки, который возвращается при выполнении запроса ввода-вывода и является основным источником информации. В примере в разделе "Аннотация" окончательный код состояния указан в соответствии с 0x28, шестой строки, начинающейся с "0028:", и включает в эту строку только четыре октета: 

```
0028: 11 00 00 80 
```

В этом случае конечное состояние равно 0x80000011. Этот код состояния сопоставляется STATUS_DEVICE_BUSY и означает, что устройство в данный момент занято.

>[!NOTE] 
> При преобразовании шестнадцатеричных данных в сообщении с ИДЕНТИФИКАТОРом события 50 в код состояния Помните, что значения представлены в формате с прямым порядком байтов. Поскольку код состояния является единственным интересующим вас сведениями, может быть проще просмотреть данные в формате "слова", а не в БАЙТах. В этом случае байты будут иметь правильный формат, и данные могут быть легко интерпретированы.

Для этого щелкните **слова** в окне **Свойства события** . В представлении «слова данных» пример в разделе «симптомы» будет считаться следующим образом: данные: 

```
() Bytes (.) 
Words 0000: 00040000 00560002 00000000 80040032 0010: 00000000 00000000 00000000 00000000 0020: 00000000 00000000 80000011
```

Список кодов состояния Windows NT см. в разделе NTSTATUS. H в пакете разработчиков программного обеспечения для Windows (SDK).