---
title: nslookup set querytype
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5af54ac5-fc1a-4af6-977b-f8e97c8eba90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1c066277a22325e5db8383f58cda31038aa656e0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838437"
---
# <a name="nslookup-set-querytype"></a>nslookup set querytype

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет тип записи ресурса для запроса.
## <a name="syntax"></a>Синтаксис
```
set querytype=<ResourceRecordtype>
```
### <a name="parameters"></a>Параметры
<ResourceRecordtype> указывает тип записи ресурса DNS. Тип записи ресурса по умолчанию —. В следующей таблице перечислены допустимые значения для этой команды.

| Значение |                                                   Описание                                                   |
|-------|-----------------------------------------------------------------------------------------------------------------|
|   А   |                                      Указывает IP-&#39;адрес компьютера                                      |
|  ВСЕМИ  |                                     Указывает IP-&#39;адрес компьютера.                                      |
| CNAME |                                    Задает каноническое имя для псевдонима.                                     |
|  ОПЕРАЦИОННОЙ  |                                  Задает идентификатор группы для имени группы.                                  |
| HINFO |                          Указывает процессор компьютера&#39;и тип операционной системы.                           |
|  МБ   |                                        Указывает доменное имя почтового ящика.                                         |
|  MG   |                                         Указывает члена почтовой группы.                                          |
| СООТВЕТСТВУЮЩУЮ |                                   Указывает сведения о почтовом ящике или списке рассылки.                                   |
|  MR   |                                     Указывает имя домена переименования почты.                                      |
|  MX   |                                          Указывает почтовый обменник.                                          |
|  NS   |                                 Указывает сервер DNS-имен для именованной зоны.                                 |
|  УКАЗАТЕЛЬ  | Указывает имя компьютера, если запрос является IP-адресом; в противном случае указывает указатель на другую информацию. |
|  Архитектура  |                                Указывает начальную зону для зоны DNS.                                 |
|  TXT  |                                         Задает текстовую информацию.                                         |
|  ТАКОЙ  |                                         Указывает идентификатор пользователя.                                          |
| уинфо |                                         Указывает сведения о пользователе.                                         |
|  ЕЙ  |                                         Описание хорошо известной службы.                                         |
| {Справка |                                                       ?}                                                        |

Отображает краткую сводку подкоманд <strong>nslookup</strong>
## <a name="remarks"></a>Примечания
- Команда <strong>Set Type</strong> выполняет ту же функцию, что и команда <strong>Set QueryType</strong> .
- Дополнительные сведения о типах записей ресурсов см. в статье запрос комментария (RFC) 1035.
  ## <a name="additional-references"></a>Дополнительные материалы
  < параметр href = Command-Line-синтаксис-key.md Data-RAW-source =- [Командная строка](command-line-syntax-key.md), > синтаксис командной строки</a> < a href = nslookup-set-Type.md Data-RAW-source =[nslookup set](nslookup-set-type.md)Type > тип набора команд nslookup</a>
