---
title: nslookup set root
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8ad5393c-d4fd-4594-8187-576b1dcde60a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ea2c34bbf7c9323c948d57ac2a838c22aea1008e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838317"
---
# <a name="nslookup-set-root"></a>nslookup set root

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет имя корневого сервера, используемого для запросов.
## <a name="syntax"></a>Синтаксис
```
set root=<RootServer>
```
### <a name="parameters"></a>Параметры

|    Параметр    |                                   Описание                                    |
|-----------------|----------------------------------------------------------------------------------|
|  <RootServer>   | Указывает новое имя для корневого сервера. Значение по умолчанию — ns.nic.ddn.mil. |
| {Help &#124; ?} |              Отображает краткую сводку подкоманд **nslookup** .               |

## <a name="remarks"></a>Примечания
- Подкоманда **set root** влияет на **корневую** подкоманду.
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [корневой элемент nslookup](nslookup-root.md)
