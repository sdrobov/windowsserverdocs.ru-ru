---
title: Примеры битсадмин
description: В следующих примерах показано, как использовать средство битсадмин для выполнения наиболее распространенных задач.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: cb8f8374-ba6e-4a68-85a1-9a95b8215354
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 05/31/2018
ms.openlocfilehash: 96447410f76e4402c456b5ec402cc730480aedaf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850807"
---
# <a name="bitsadmin-examples"></a>Примеры битсадмин

В следующих примерах показано, как использовать средство `bitsadmin` для выполнения наиболее распространенных задач.

## <a name="transfer-a-file"></a>Перенос файла

Параметр **/Трансфер** является ярлыком для выполнения перечисленных ниже задач. Этот параметр создает задание, добавляет файлы в задание, активирует задание в очереди на перемещение и завершает задание. Битсадмин сохраняет сведения о ходе выполнения в окне MS-DOS до тех пор, пока не завершится перемещение или не произойдет ошибка.

`bitsadmin /transfer myDownloadJob /download /priority normal https://downloadsrv/10mb.zip c:\\10mb.zip`

## <a name="create-a-download-job"></a>Создание задания скачивания

Используйте параметр **/CREATE** , чтобы создать задание скачивания с именем мидовнлоаджоб.

### <a name="syntax"></a>Синтаксис

```
bitsadmin /create myDownloadJob
```

Битсадмин возвращает идентификатор GUID, однозначно определяющий задание. Используйте идентификатор GUID или имя задания в последующих вызовах. Следующий текст — пример выходных данных.

#### <a name="sample-output"></a>Образец полученных результатов

`created job {C775D194-090F-431F-B5FB-8334D00D1CB6}`

## <a name="add-files-to-the-download-job"></a>Добавление файлов в задание скачивания

Используйте параметр **/AddFile** , чтобы добавить файл в задание. Повторите этот вызов для каждого файла, который нужно добавить.

Если несколько заданий используют Мидовнлоаджоб в качестве имени, необходимо заменить Мидовнлоаджоб на GUID задания для уникальной идентификации задания.

### <a name="syntax"></a>Синтаксис

```
bitsadmin /addfile myDownloadJob https://downloadsrv/10mb.zip c:\\10mb.zip
```

## <a name="activate-the-download-job"></a>Активация задания скачивания

При создании нового задания служба BITS приостанавливает задание. Чтобы активировать задание в очереди на перемещение, используйте параметр **/Resume** .

Если несколько заданий используют Мидовнлоаджоб в качестве имени, необходимо заменить Мидовнлоаджоб на GUID задания для уникальной идентификации задания.

### <a name="syntax"></a>Синтаксис

`bitsadmin /resume myDownloadJob`

## <a name="determine-the-progress-of-the-download-job"></a>Определение хода выполнения задания загрузки

Используйте параметр **/info** , чтобы вернуть состояние задания и число переданных файлов и байтов. При передаче состояния служба BITS успешно передала все файлы в задании.

- Используйте аргумент **/verbose** , чтобы получить полные сведения о задании.

- Используйте параметр **/List** или **/монитор** , чтобы получить все задания в очереди на перемещение.

Если несколько заданий используют Мидовнлоаджоб в качестве имени, необходимо заменить Мидовнлоаджоб на GUID задания для уникальной идентификации задания.

### <a name="syntax"></a>Синтаксис

`bitsadmin /info myDownloadJob /verbose`

#### <a name="sample-output"></a>Образец полученных результатов

```
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

## <a name="completing-the-download-job"></a>Завершение задания скачивания

При передаче состояния задания служба BITS успешно передала все файлы в задании. Однако файлы недоступны до тех пор, пока не будет использован параметр **/комплете** .

Если несколько заданий используют Мидовнлоаджоб в качестве имени, необходимо заменить Мидовнлоаджоб на GUID задания для уникальной идентификации задания.

### <a name="syntax"></a>Синтаксис

`bitsadmin /complete myDownloadJob`

## <a name="monitoring-jobs-in-the-transfer-queue"></a>Наблюдение за заданиями в очереди на перемещение

Используйте параметр **/List**, **/монитор**или **/info** для отслеживания заданий в очереди на перемещение. Параметр **/List** предоставляет сведения обо всех заданиях в очереди.

## <a name="list-switch"></a>параметр/List

Параметр **/List** возвращает состояние задания и число файлов и байт, переданных для всех заданий в очереди передачи.

### <a name="syntax"></a>Синтаксис

`bitsadmin /list`

#### <a name="sample-output-for-the-list-switch"></a>Пример выходных данных для параметра/List

```
{6AF46E48-41D3-453F-B7AF-A694BBC823F7} job1 SUSPENDED 0 / 0 0 / 0
{482FCAF0-74BF-469B-8929-5CCD028C9499} job2 TRANSIENT_ERROR 0 / 1 0 / UNKNOWN

Listed 2 job(s).
```

## <a name="monitor-switch"></a>/монитор, параметр

Параметр **/монитор** возвращает состояние задания и число файлов и байтов, переданных для всех заданий в очереди передачи, обновляя данные каждые 5 секунд. Чтобы прервать обновление, нажмите клавиши CTRL + C.

### <a name="syntax"></a>Синтаксис

`bitsadmin /monitor`

#### <a name="sample-output"></a>Образец полученных результатов

```
MONITORING BACKGROUND COPY MANAGER(5 second refresh)
{6AF46E48-41D3-453F-B7AF-A694BBC823F7} job1 SUSPENDED 0 / 0 0 / 0
{482FCAF0-74BF-469B-8929-5CCD028C9499} job2 TRANSIENT_ERROR 0 / 1 0 / UNKNOWN
{0B138008-304B-4264-B021-FD04455588FF} job3 TRANSFERRED 1 / 1 100379370 / 100379370
```

## <a name="deleting-jobs-from-the-transfer-queue"></a>Удаление заданий из очереди на перемещение

Используйте параметр **/Reset** , чтобы удалить все задания из очереди на перемещение.

### <a name="syntax"></a>Синтаксис

`bitsadmin /reset`

#### <a name="sample-output"></a>Образец полученных результатов

```
{DC61A20C-44AB-4768-B175-8000D02545B9} canceled.
{BB6E91F3-6EDA-4BB4-9E01-5C5CBB5411F8} canceled.
2 out of 2 jobs canceled.
```
