---
title: verifier
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: cc2482fa25d0236991889c3951cb522e27bf520d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71362688"
---
# <a name="verifier"></a>verifier

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
|@no__t 0flags >|Должно быть числом в десятичном или шестнадцатеричном формате, сочетанием битов:<br /><br />Значение -    **: описание**<br />@no__t 0**бит 0:** проверка особого пула<br />-   **бит 1:** принудительная проверка IRQL<br />-   **бит 2:** Эмуляция нехватки ресурсов<br />-   **бит 3:** отслеживание пула<br />-   **бит 4:** Проверка ввода-вывода<br />-   **бит 5:** обнаружение взаимоблокировки<br />-   **бит 6:** не используется<br />-   **бит 7:** Проверка DMA<br />-   **бит 8:** проверки безопасности<br />-   **бит 9:** принудительное выполнение ожидающих запросов ввода-вывода<br />-   **бит 10:** Ведение журнала IRP<br />-   **бит 11:** прочие проверки<br /><br />Например, **/flags 27** эквивалентно **/flags 0x1B**|  
|/volatile|Используется для динамического изменения параметров средства проверки без перезагрузки системы. При перезапуске системы все новые параметры будут потеряны.|  
|@no__t 0probability >|Число от 1 до 10 000, указывающее вероятность внедрения сбоя. Например, указание 100 означает вероятность внедрения сбоя 1% (100/10000).<br /><br />Если этот параметр не указан, будет использоваться вероятность по умолчанию, равная 6%.|  
|@no__t 0tags >|Указывает Теги пула, которые будут добавлены с ошибками, разделяя их пробелами. Если этот параметр не указан, можно внедрить любое выделение пула с ошибками.|  
|@no__t 0applications >|Указывает имя файла образа приложений, которые будут добавлены с ошибками, разделенными символами пробела. Если этот параметр не указан, имитация нехватки ресурсов может выполняться в любом приложении.|  
|@no__t 0minutes >|Положительное число, указывающее продолжительность периода после перезагрузки (в минутах), в течение которого не будет производиться внесение ошибок. Если этот параметр не указан, будет использоваться длина по умолчанию (8 минут).|  
|/?|Отображение справки в командной строке.|  

## <a name="additional-references"></a>Дополнительная справка  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  