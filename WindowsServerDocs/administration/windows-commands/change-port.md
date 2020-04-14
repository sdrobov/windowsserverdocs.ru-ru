---
title: change port
description: Команды Windows для порта Change, который перечисляет или изменяет сопоставления COM-портов для совместимости с приложениями MS-DOS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3d772c90-e849-4e74-b9ec-b6cae1159336 Lizap
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 39273382038edb7709f2d99baea8090d71df3a57
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848077"
---
# <a name="change-port"></a>change port

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

перечисление или изменение сопоставления COM-портов для совместимости с приложениями MS-DOS.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов называются службами удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.

## <a name="syntax"></a>Синтаксис

```
change port [<PortX>=<PortY| /d <PortX| /query]
```

### <a name="parameters"></a>Параметры


|    Параметр    |              Описание               |
|-----------------|----------------------------------------|
| <PortX>=<PortY> | Сопоставляет COM-<*порткс*> с <ным*портом*> |
|   /d <PortX>    | Удаляет сопоставление для COM-<*порткс*> |
|     /Query      | Отображение текущих сопоставлений портов |
|       /?        | Отображение справки в командной строке |

## <a name="remarks"></a>Примечания

- Большинство приложений MS-DOS поддерживают только последовательные порты с COM1 до COM4. Команда **изменить порт** сопоставляет последовательный порт с другим номером порта, что позволяет приложениям, которые не поддерживают порты COM с большим числом номеров, обращаться к последовательному порту. повторное сопоставление работает только для текущего сеанса и не сохраняется при выходе из сеанса и последующем входе в систему.

- Используйте параметр **порт изменений** без параметров для отображения доступных COM-портов и их текущих сопоставлений.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

- Чтобы преобразовать COM12 в порт COM1 для использования приложением на основе MS-DOS, введите:
  ```
  change port com12=com1
  ```
- Чтобы отобразить текущие сопоставления портов, введите:
  ```
  change port /query
  ```

### <a name="additional-references"></a>Дополнительные материалы
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
- [change](change.md)
- [Справочник по командам служб удаленных рабочих столов (служб терминалов)](remote-desktop-services-terminal-services-command-reference.md)
