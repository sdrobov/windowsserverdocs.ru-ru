---
title: verifier
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 782173d6-f196-4bc4-a547-76109829453c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2ab0833d4fdb11c4962d4916ec2e32097e08ca04
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59865875"
---
# <a name="verifier"></a>verifier

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Диспетчер проверки драйверов.  

## <a name="syntax"></a>Синтаксис  
```  
verifier /standard /driver <name> [<name> ...]  
verifier /standard /all  
verifier [/flags <flags>] [/faults [<probability> [<tags> [<applications> [<minutes>]]]] /driver <name> [<name>...]  
verifier [/flags FLAGS] [/faults [<probability> [<tags> [<applications> [<minutes>]]]] /all  
verifier /querysettings  
verifier /volatile /flags <flags>  
verifier /volatile /adddriver <name> [<name>...]  
verifier /volatile /removedriver <name> [<name>...]  
verifier /volatile /faults [<probability> [<tags> [<applications>]]  
verifier /reset  
verifier /query  
verifier /log <LogFileName> [/interval <seconds>]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|\<Флаги >|Должно быть числом в сочетании десятичного или шестнадцатеричного битов:<br /><br />-   **Значение: описание**<br />-   **бит 0:** особый пул<br />-   **бит 1:** Обяз.<br />-   **бит 2:** недостаточно ресурсов<br />-   **бит 3:** отслеживание пула<br />-   **бит 4:** Проверку ввода-вывода<br />-   **бит 5:** обнаружения взаимоблокировки<br />-   **бит 6:** неиспользуемые<br />-   **7-разрядных систем:** Проверка DMA<br />-   **бит 8:** проверок безопасности<br />-   **бит 9:** принудительно ожидающих запросов ввода-вывода<br />-   **10-разрядная версия:** Ведение журнала IRP<br />-   **бит 11:** прочие проверки<br /><br />например **/flags 27** эквивалента   **/flags 0x1B**|  
|/ volatile|Используется для изменения параметров проверки драйверов динамически, без перезапуска системы. Все новые параметры будут потеряны при перезапуске системы.|  
|\<вероятность >|Число от 1 до 10 000, указав вероятность сбоя. Например указав 100 означает, что вероятность сбоя 1% (100/10 000).<br /><br />Если этот параметр не указан, то будет использоваться вероятность по умолчанию % 6.|  
|\<теги >|Задает теги, которые внедряются ошибки, разделяются пробелами. Если этот параметр не задан любой распределения пула можно внедрить ошибки.|  
|\<приложения >|Указывает имя файла изображения приложений, которые будут внесены ошибки, разделяются пробелами. Если этот параметр не указан затем нехватка ресурсов могут выполняться в любом приложении.|  
|\<минут >|Положительное число, указывающее длину периода после перезагрузки, в минутах, во время неисправность не будет выполняться путем внедрения кода. Если этот параметр не указан, то будет использоваться длину 8 минут, по умолчанию.|  
|/?|Отображение справки в командной строке.|  

## <a name="additional-references"></a>Дополнительная справка  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  