---
title: nslookup set querytype
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5af54ac5-fc1a-4af6-977b-f8e97c8eba90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 496eededd8b0b5eb79cdc1b4a7e35bc017157768
ms.sourcegitcommit: f3b61dcd8aa0aa744db4ea938aac633c19217b0a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746300"
---
# <a name="nslookup-set-querytype"></a>nslookup set querytype

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет тип записи ресурса для запроса.
## <a name="syntax"></a>Синтаксис
```
set querytype=<ResourceRecordtype>
```
## <a name="parameters"></a>Параметры
<ResourceRecordtype>Указывает тип записи ресурса DNS. Тип записи ресурса по умолчанию —. В следующей таблице перечислены допустимые значения для этой команды.

| Значение |                                                   Описание                                                   |
|-------|-----------------------------------------------------------------------------------------------------------------|
|   Объект   |                                      Указывает IP-&#39;адрес компьютера                                      |
|  ВСЕМИ  |                                     Указывает IP-&#39;адрес компьютера.                                      |
| ПСЕВДОНИМ |                                    Задает каноническое имя для псевдонима.                                     |
|  ОПЕРАЦИОННОЙ  |                                  Задает идентификатор группы для имени группы.                                  |
| HINFO |                          Указывает процессор компьютера&#39;и тип операционной системы.                           |
|  МБ   |                                        Указывает доменное имя почтового ящика.                                         |
|  MG   |                                         Указывает члена почтовой группы.                                          |
| СООТВЕТСТВУЮЩУЮ |                                   Указывает сведения о почтовом ящике или списке рассылки.                                   |
|  MR   |                                     Указывает имя домена переименования почты.                                      |
|  MX   |                                          Указывает почтовый обменник.                                          |
|  NS   |                                 Указывает сервер DNS-имен для именованной зоны.                                 |
|  УКАЗАТЕЛЬ  | Указывает имя компьютера, если запрос является IP-адресом; в противном случае указывает указатель на другую информацию. |
|  АРХИТЕКТУРА  |                                Указывает начальную зону для зоны DNS.                                 |
|  TXT  |                                         Задает текстовую информацию.                                         |
|  ТАКОЙ  |                                         Указывает идентификатор пользователя.                                          |
| УИНФО |                                         Указывает сведения о пользователе.                                         |
|  ЕЙ  |                                         Описание хорошо известной службы.                                         |
| {Справка |                                                       ?}                                                        |

Отображает краткую сводку подкоманд <strong>nslookup</strong>
## <a name="remarks"></a>Примечания
- Команда <strong>Set Type</strong> выполняет ту же функцию, что и команда <strong>Set QueryType</strong> .
- Дополнительные сведения о типах записей ресурсов см. в статье запрос комментария (RFC) 1035.
  ## <a name="additional-references"></a>Дополнительные ссылки
  <a href="command-line-syntax-key.md" data-raw-source="[Command-Line Syntax Key](command-line-syntax-key.md)">Ключ синтаксиса командной строки команда</a><a href="nslookup-set-type.md" data-raw-source="[nslookup set type](nslookup-set-type.md)">nslookup set Type</a> 
  
