---
title: verifier
description: Раздел команд Windows для средства Verifier, запускающего диспетчер проверки драйверов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 782173d6-f196-4bc4-a547-76109829453c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f0f4c35e732f520076df9ec89b9417c744d5c44
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830177"
---
# <a name="verifier"></a>verifier

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
#### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|Флаги \<>|Должно быть числом в десятичном или шестнадцатеричном формате, сочетанием битов:<p>-   **значение: описание**<br />-   **бит 0:** проверка особого пула<br />-   **бит 1:** принудительная проверка IRQL<br />-   **бит 2:** Эмуляция нехватки ресурсов<br />-   **бит 3:** отслеживание пула<br />-   **бит 4:** проверка ввода-вывода<br />-   **бит 5:** обнаружение взаимоблокировки<br />-   **бит 6:** не используется<br />-   **бит 7:** проверка DMA<br />-   **бит 8:** проверки безопасности<br />-   **бит 9:** принудительное выполнение ожидающих запросов ввода-вывода<br />-   **бит 10:** ведение журнала IRP<br />-   **бит 11:** прочие проверки<p>Например, **/flags 27** эквивалентно **/flags 0x1B**|  
|/volatile|Используется для динамического изменения параметров средства проверки без перезагрузки системы. При перезапуске системы все новые параметры будут потеряны.|  
|вероятность \<>|Число от 1 до 10 000, указывающее вероятность внедрения сбоя. Например, указание 100 означает вероятность внедрения сбоя 1% (100/10000).<p>Если этот параметр не указан, будет использоваться вероятность по умолчанию, равная 6%.|  
|Теги \<>|Указывает Теги пула, которые будут добавлены с ошибками, разделяя их пробелами. Если этот параметр не указан, можно внедрить любое выделение пула с ошибками.|  
|\<приложения >|Указывает имя файла образа приложений, которые будут добавлены с ошибками, разделенными символами пробела. Если этот параметр не указан, имитация нехватки ресурсов может выполняться в любом приложении.|  
|\<минут >|Положительное число, указывающее продолжительность периода после перезагрузки (в минутах), в течение которого не будет производиться внесение ошибок. Если этот параметр не указан, будет использоваться длина по умолчанию (8 минут).|  
|/?|Отображает справку в командной строке.|  

## <a name="additional-references"></a>Дополнительная справка  
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  