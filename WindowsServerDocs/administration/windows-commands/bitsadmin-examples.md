---
title: Примеры bitsadmin
description: Следующие примеры показывают, как использовать средство bitsadmin для выполнения наиболее распространенных задач.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb8f8374-ba6e-4a68-85a1-9a95b8215354
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/31/2018
ms.openlocfilehash: a98e1a876c972b0f146ff37aff0a77399b684e99
ms.sourcegitcommit: 8eea7aadbe94f5d4635c4ffedc6a831558733cc0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308562"
---
# <a name="bitsadmin-examples"></a>Примеры bitsadmin

Следующие примеры показывают, как использовать `bitsadmin` средство для выполнения наиболее распространенных задач.

## <a name="transfer-a-file"></a>Перенос файла

**Передачу** коммутатор является ярлыком для выполнения перечисленных ниже задач. Этот параметр создает задание, добавляет файлы в задание, активирует задание в очереди передачи и завершает задание. BITSAdmin по-прежнему отображаются сведения о ходе выполнения в окне MS-DOS до завершения передачи или произошла ошибка.

**bitsadmin /transfer myDownloadJob/Download /priority обычный `https://downloadsrv/10mb.zip c:\\10mb.zip`**

## <a name="create-a-download-job"></a>Создание задания скачивания

Используйте **/ create** коммутатора, чтобы создать задание загрузки с именем myDownloadJob.

**bitsadmin / create myDownloadJob**

BITSAdmin Возвращает GUID, который однозначно определяет задание. Используйте имя GUID или задания в последующих вызовах. Ниже приведен пример выходных данных.

``` syntax
Created job {C775D194-090F-431F-B5FB-8334D00D1CB6}.
```

Затем используйте **/AddFile** коммутатора, чтобы добавить один или несколько файлов для задания скачивания.

## <a name="add-files-to-the-download-job"></a>Добавление файлов для задания скачивания

Используйте **/AddFile** коммутатора, чтобы добавить файл к заданию. Повторите этот вызов для каждого файла, который вы хотите добавить. Если несколько заданий используйте myDownloadJob в имени, необходимо заменить myDownloadJob с идентификатором GUID задания для уникальной идентификации задания.

**/ AddFile myDownloadJob bitsadmin https://downloadsrv/10mb.zip c:\\10mb.zip**

Чтобы активировать задание в очереди передачи, используйте **/resume** переключения.

## <a name="activate-the-download-job"></a>Активация задания скачивания

При создании нового задания BITS приостанавливает задание. Чтобы активировать задание в очереди передачи, используйте **/resume** переключения. Если несколько заданий используйте myDownloadJob в имени, необходимо заменить myDownloadJob с идентификатором GUID задания для уникальной идентификации задания.

**bitsadmin /resume myDownloadJob**

Чтобы определить ход выполнения задания, используйте **/list**, **/Info**, или **/мониторинг** переключения.

## <a name="determine-the-progress-of-the-download-job"></a>Определения хода выполнения задания скачивания

Используйте **/Info** параметр, позволяющий определить ход выполнения задания. Если несколько заданий используйте myDownloadJob в имени, необходимо заменить myDownloadJob с идентификатором GUID задания для уникальной идентификации задания.

**myDownloadJob bitsadmin/Info / verbose**

**/Info** switch возвращает состояние задания и количество файлов и байтов, переданных. Если ПЕРЕДАЕТСЯ состояние, BITS успешно передаст все файлы в задание. **/ Verbose** аргумент предоставляет полные сведения о задании. Ниже приведен пример выходных данных.

``` syntax
GUID: {482FCAF0-74BF-469B-8929-5CCD028C9499} DISPLAY: myDownloadJob
TYPE: DOWNLOAD STATE: TRANSIENT_ERROR OWNER: domain\user
PRIORITY: NORMAL FILES: 0 / 1 BYTES: 0 / UNKNOWN
CREATION TIME: 12/17/2002 1:21:17 PM MODIFICATION TIME: 12/17/2002 1:21:30 PM
COMPLETION TIME: UNKNOWN
NOTIFY INTERFACE: UNREGISTERED NOTIFICATION FLAGS: 3
RETRY DELAY: 600 NO PROGRESS TIMEOUT: 1209600 ERROR COUNT: 0
PROXY USAGE: PRECONFIG PROXY LIST: NULL PROXY BYPASS LIST: NULL
ERROR FILE:    https://downloadsrv/10mb.zip -> c:\10mb.zip
ERROR CODE:    0x80072ee7 - The server name or address could not be resolved
ERROR CONTEXT: 0x00000005 - The error occurred while the remote file was being 
processed.
DESCRIPTION:
JOB FILES:
        0 / UNKNOWN WORKING https://downloadsrv/10mb.zip -> c:\10mb.zip
NOTIFICATION COMMAND LINE: none
```

Для получения сведений обо всех заданиях в очереди передачи, используйте **/list** или **/мониторинг** переключения.

## <a name="completing-the-download-job"></a>Завершение задания скачивания

При ПЕРЕДАЧЕ состояние задания BITS успешно передаст все файлы в задание. Тем не менее, файлы не будут доступны только при вызове **/ завершения** переключения. Если несколько заданий используйте myDownloadJob в имени, необходимо заменить myDownloadJob с идентификатором GUID задания для уникальной идентификации задания.

**bitsadmin / complete myDownloadJob**

## <a name="monitoring-jobs-in-the-transfer-queue"></a>Мониторинг заданий в очереди передачи

Используйте **/list**, **/мониторинг**, или **/Info** коммутатора для мониторинга заданий в очереди передачи. **/List** коммутатор предоставляет сведения для всех заданий в очереди.

**/ List bitsadmin**

**/List** switch возвращает состояние задания и количество файлов и байтов, переданных для всех заданий в очереди передачи. Ниже приведен пример выходных данных.

``` syntax
{6AF46E48-41D3-453F-B7AF-A694BBC823F7} job1 SUSPENDED 0 / 0 0 / 0
{482FCAF0-74BF-469B-8929-5CCD028C9499} job2 TRANSIENT_ERROR 0 / 1 0 / UNKNOWN

Listed 2 job(s).
```

Используйте **/мониторинг** коммутатора для отслеживания всех заданий в очереди. **/Мониторинг** коммутатора обновляет данные каждые 5 секунд. Чтобы прекратить обновление, введите CTRL + C.

**bitsadmin /monitor**

**/Мониторинг** switch возвращает состояние задания и количество файлов и байтов, переданных для всех заданий в очереди передачи. Ниже приведен пример выходных данных.

``` syntax
MONITORING BACKGROUND COPY MANAGER(5 second refresh)
{6AF46E48-41D3-453F-B7AF-A694BBC823F7} job1 SUSPENDED 0 / 0 0 / 0
{482FCAF0-74BF-469B-8929-5CCD028C9499} job2 TRANSIENT_ERROR 0 / 1 0 / UNKNOWN
{0B138008-304B-4264-B021-FD04455588FF} job3 TRANSFERRED 1 / 1 100379370 / 100379370
```

## <a name="deleting-jobs-from-the-transfer-queue"></a>Удаление заданий из очереди передачи

Используйте **/reset** удаление всех заданий из очереди передачи.

**/ Reset bitsadmin**

Ниже приведен пример выходных данных.

``` syntax
{DC61A20C-44AB-4768-B175-8000D02545B9} canceled.
{BB6E91F3-6EDA-4BB4-9E01-5C5CBB5411F8} canceled.
2 out of 2 jobs canceled.
```
