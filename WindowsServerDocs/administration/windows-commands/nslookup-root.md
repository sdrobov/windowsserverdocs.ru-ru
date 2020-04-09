---
title: nslookup root
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9c29edc3-ec49-43f2-bc49-86bf0612d816
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d11179ff3cd22acd9df67261e7ab752aa159201a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838647"
---
# <a name="nslookup-root"></a>nslookup root

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет сервер по умолчанию на сервер для корня пространства имен домена службы доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
root 
```
### <a name="parameters"></a>Параметры

|    Параметр    |                      Описание                      |
|-----------------|-------------------------------------------------------|
| {Help &#124; ?} | Отображает краткую сводку подкоманд **nslookup** . |

## <a name="remarks"></a>Примечания
- В настоящее время используется сервер имен ns.nic.ddn.mil. Эта команда является синонимом для лсервер ns.nic.ddn.mil. Имя корневого сервера можно изменить с помощью команды **set root** .
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Ключ синтаксиса командной строки
  команду](command-line-syntax-key.md) [nslookup set root](nslookup-set-root.md)
