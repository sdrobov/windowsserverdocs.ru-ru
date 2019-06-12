---
title: termserver запроса
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b89d3b4-236f-4376-90b6-939a0ec4b288
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 14270092949baf37588059d592e6f92e694a1739
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66442090"
---
# <a name="query-termserver"></a>termserver запроса

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображение списка всех серверов узла сеансов удаленных рабочих столов (rd узла сеансов) в сети.
Примеры для использования этой команды, см. в разделе [примеры](#BKMK_examples).
> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы найти новые возможности в последней версии, см. в разделе [какие возможности служб удаленных рабочих столов в Windows Server 2012](https://technet.microsoft.com/library/hh831527) в технической библиотеке Windows Server.
> ## <a name="syntax"></a>Синтаксис
> ```
> query termserver [<ServerName>] [/domain:<Domain>] [/address] [/continue]
> ```
> ## <a name="parameters"></a>Параметры
> 
> |    Параметр     |                                                                        Описание                                                                         |
> |------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
> |   <ServerName>   |                                               Указывает имя, определяющее сервер узла сеансов удаленных рабочих столов.                                               |
> | / domain:<Domain> | Указывает домен, для запросов для служб терминалов. Необходимо указать домен, при выполнении запроса домена, в котором вы сейчас работаете. |
> |     / Address     |                                                  Отображает адреса сети и узлов для каждого сервера.                                                  |
> |    / continue     |                                              Предотвращает остановку после отображения каждого экрана со сведениями.                                               |
> |        /?        |                                                            Отображение справки в командной строке.                                                            |
> 
> ## <a name="remarks"></a>Примечания
> - **запрос termserver** ищет в сети, все подключенные серверы узла сеансов удаленных рабочих столов, и возвращает следующую информацию:
>   - Имя сервера
>   - Сеть (и адрес узла, если используется параметр/address)
>     ## <a name="BKMK_examples"></a>Примеры
> - Чтобы отобразить сведения обо всех серверах узла сеансов удаленных рабочих столов в сети, введите следующую команду:
>   ```
>   query termserver
>   ```
> - Чтобы отобразить сведения о сервере узла сеансов удаленных рабочих столов с именем Server3, введите следующую команду:
>   ```
>   query termserver Server3
>   ```
> - Чтобы просмотреть сведения обо всех серверах узла сеансов удаленных рабочих столов в домене CONTOSO, введите:
>   ```
>   query termserver /domain:CONTOSO
>   ```
> - Для отображения адреса сети и узла для сервера узла сеансов удаленных рабочих столов, с именем Server3, введите:
>   ```
>   query termserver Server3 /address
>   ```
>   #### <a name="additional-references"></a>Дополнительные ссылки
>   [Ключ синтаксиса команд](command-line-syntax-key.md)
>   [запроса](query.md)
>   [служб удаленных рабочих столов &#40;служб терминалов&#41; Справочник по командам](remote-desktop-services-terminal-services-command-reference.md)
