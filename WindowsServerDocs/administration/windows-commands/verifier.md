---
title: verifier
description: Справочный раздел по средству Verifier, запускающему диспетчер проверки драйверов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 782173d6-f196-4bc4-a547-76109829453c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d98ebf3f6de9a5fbac33d983ebda581b0c6c385b
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2020
ms.locfileid: "83437079"
---
# <a name="verifier"></a>verifier

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

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
|\<Флаги>|Должно быть числом в десятичном или шестнадцатеричном формате, сочетанием битов:<p>-   **Значение: описание**<br />-   **бит 0:** проверка особого пула<br />-   **бит 1.** принудительная проверка IRQL<br />-   **бит 2.** имитация нехватки ресурсов<br />-   **бит 3.** отслеживание пула<br />-   **бит 4:** Проверка ввода-вывода<br />-   **бит 5.** обнаружение взаимоблокировок<br />-   **бит 6:** не используется<br />-   **бит 7:** Проверка DMA<br />-   **бит 8.** проверки безопасности<br />-   **бит 9.** принудительное выполнение ожидающих запросов ввода-вывода<br />-   **бит 10:** Ведение журнала IRP<br />-   **бит 11.** прочие проверки<p>Например, **/flags 27** эквивалентно **/flags 0x1B**|
|/volatile|Используется для динамического изменения параметров средства проверки без перезагрузки системы. При перезапуске системы все новые параметры будут потеряны.|
|\<вероятность>|Число от 1 до 10 000, указывающее вероятность внедрения сбоя. Например, указание 100 означает вероятность внедрения сбоя 1% (100/10000).<p>Если этот параметр не указан, будет использоваться вероятность по умолчанию, равная 6%.|
|\<Теги>|Указывает Теги пула, которые будут добавлены с ошибками, разделяя их пробелами. Если этот параметр не указан, можно внедрить любое выделение пула с ошибками.|
|\<приложения>|Указывает имя файла образа приложений, которые будут добавлены с ошибками, разделенными символами пробела. Если этот параметр не указан, имитация нехватки ресурсов может выполняться в любом приложении.|
|\<минут>|Положительное число, указывающее продолжительность периода после перезагрузки (в минутах), в течение которого не будет производиться внесение ошибок. Если этот параметр не указан, будет использоваться длина по умолчанию (8 минут).|
|/?|Отображение справки в командной строке.|

## <a name="additional-references"></a>Дополнительные ссылки
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)