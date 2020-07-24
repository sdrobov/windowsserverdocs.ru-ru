---
title: change port
description: Справочная статья по команде изменения порта, которая перечисляет или изменяет сопоставления COM-портов для совместимости с приложениями MS-DOS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3d772c90-e849-4e74-b9ec-b6cae1159336 Lizap
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1ee3305ff1b8e9ecf82126bd16e6c2c15bb27b26
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86955316"
---
# <a name="change-port"></a>change port

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Перечисление или изменение сопоставления COM-портов для совместимости с приложениями MS-DOS.

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows Server](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11)).

## <a name="syntax"></a>Синтаксис

```
change port [<portX>=<portY| /d <portX | /query]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|-----------------|----------------------------------------|
| <portX>=<portY> | Сопоставляет COM `<*portX*>` с`<*portY*>` |
| /d<portX> | Удаляет сопоставление для COM`<*portX*>` |
| /Query | Отображает текущие сопоставления портов. |
| /? | Отображение справки в командной строке. |

#### <a name="remarks"></a>Комментарии

- Большинство приложений MS-DOS поддерживают только последовательные порты с COM1 до COM4. Команда **изменить порт** сопоставляет последовательный порт с другим номером порта, что позволяет приложениям, которые не поддерживают порты COM с большим числом номеров, обращаться к последовательному порту. Повторное сопоставление работает только для текущего сеанса и не сохраняется при выходе из сеанса и последующем входе в систему.

- Используйте параметр **порт изменений** без параметров для отображения доступных COM-портов и их текущих сопоставлений.

## <a name="examples"></a>Примеры

- Чтобы преобразовать COM12 в порт COM1 для использования приложением на основе MS-DOS, введите:

  ```
  change port com12=com1
  ```

- Чтобы отобразить текущие сопоставления портов, введите:

  ```
  change port /query
  ```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [изменить команду](change.md)

- [Справочник по командам служб удаленных рабочих столов (служб терминалов)](remote-desktop-services-terminal-services-command-reference.md)
