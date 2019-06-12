---
title: Net print
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f59b2015-4698-415d-9a74-09566c466f40
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4018ec3779a9735916136fa54f532ad5767c960e
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66437098"
---
# <a name="net-print"></a>Net print

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения об указанной очереди печати или задания печати, или управляет задания печати.
Примеры для использования этой команды, см. в разделе [примеры](#BKMK_examples) настоящего документа.
> [!NOTE]
> Эта команда является устаревшим в Windows 7 и Windows Server 2008 R2. Тем не менее можно выполнить множество задач с помощью prnjobs, инструментария управления Windows (WMI) или командлетов Windows PowerShell. Дополнительные сведения см. в разделе [prnjobs](prnjobs.md), [инструментария управления Windows](https://go.microsoft.com/fwlink/?LinkID=29991) (https://go.microsoft.com/fwlink/?LinkID=29991), [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=128426) (https://go.microsoft.com/fwlink/?LinkID=128426)и [Галерея центра сценариев TechNet](https://go.microsoft.com/fwlink/?LinkId=164635) (https://go.microsoft.com/fwlink/?LinkId=164635).
> ## <a name="syntax"></a>Синтаксис
> ```
> Net print {\\<computerName>\<Sharename> | 
> \\<computerName> <JobNumber> [/hold | /release | /delete]} [help]
> ```
> ## <a name="parameters"></a>Параметры
> 
> |               Параметры               |                                                                                                                                                                                                                     Описание                                                                                                                                                                                                                      |
> |----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
> |    \\\\<computerName>\\<Sharename>     |                                                                                                                                                                            Указывает очередь компьютера и печати, о котором требуется отобразить сведения (по имени).                                                                                                                                                                             |
> |           \\\\<computerName>           |                                                                                                                                 Компьютер (по имени), на котором размещается задание печати, которое вы хотите управлять. Если компьютер не указан, подразумевается локальный компьютер. Требует <JobNumber> параметра.                                                                                                                                  |
> |              <JobNumber>               |                                             Указывает количество задание печати, которое вы хотите управлять. Этот номер назначается на компьютере, на котором размещается очередь печати, куда отправлять задания печати. После того как компьютер назначает номер задания печати, что номер не назначается никаких других заданий печати в любую очередь, размещенную на этом же компьютере. Требуется при использовании \\ \\ <computerName> параметра.                                             |
> | [/ хранения &#124; /release &#124; /delete] | Указывает действие, выполняемое с заданием печати.<br /><br />- **/Хранения** параметр откладывает задание, позволяя другие задания печати пропустить ее до освобождения.<br />- **/Release** параметр освобождает приостановленного задания печати.<br />- **/Delete** параметр удаляет задание печати из очереди печати.<br /><br />Если указать номер задания, но не указывайте никаких действий, отображаются сведения о задании печати. |
> |                  справка                  |                                                                                                                                                                                                     Отображает справку по **Net print** команды.                                                                                                                                                                                                     |
> 
> ## <a name="remarks"></a>Примечания
> - **NET print** \\ \\ <computerName> отображаются сведения о заданий печати в очередь общего принтера. Ниже приведен пример отчета для всех заданий печати в очередь для общего принтера LASER:
>   ```
>   printers at \\PRODUCTION
>   Name              Job #      Size      Status
>   -----------------------------
>   LASER Queue       3 jobs               *printer active*
>      USER1          84        93844      printing
>      USER2          85        12555      Waiting
>      USER3          86        10222      Waiting
>   ```
> - Ниже приведен пример отчета для задания печати:
>   ```
>   Job #            35
>   Status           Waiting
>   Size             3096
>   remark
>   Submitting user  USER2
>   Notify           USER2
>   Job data type
>   Job parameters
>   additional info
>   ```
>   ## <a name="BKMK_examples"></a>Примеры
>   В этом примере показано, как вывести список содержимого очереди печати Dotmatrix на \\\Production компьютера:
>   ```
>   Net print \\Production\Dotmatrix 
>   ```
>   В этом примере показано, как отобразить сведения о задании номер 35 на \\\Production компьютера:
>   ```
>   Net print \\Production 35 
>   ```
>   В этом примере показано, как задержка задания 263 на \\\Production компьютера:
>   ```
>   Net print \\Production 263 /hold 
>   ```
>   В этом примере показано, как выпустить задания 263 \\\Production компьютера:
>   ```
>   Net print \\Production 263 /release 
>   ```
>   #### <a name="additional-references"></a>Дополнительные ссылки
>   [Ключ синтаксиса команд](command-line-syntax-key.md)
>   [команды печати](print-command-reference.md)
