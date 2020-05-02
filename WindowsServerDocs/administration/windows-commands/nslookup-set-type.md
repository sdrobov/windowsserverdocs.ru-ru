---
title: nslookup set type
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5248e314-fac1-413e-81dc-bbe0a0873ba5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9a9ccc7dde40b93db5f331930bc405c98764483d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723532"
---
# <a name="nslookup-set-type"></a>nslookup set type

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет тип записи ресурса для запроса.
## <a name="syntax"></a>Синтаксис
```
set type=<ResourceRecordtype>
```
### <a name="parameters"></a>Параметры
<ResourceRecordtype>Указывает тип записи ресурса DNS. Тип записи ресурса по умолчанию —. В следующей таблице перечислены допустимые значения для этой команды.

| Значение |                                                   Описание                                                   |
|-------|-----------------------------------------------------------------------------------------------------------------|
|   Объект   |                                      Указывает IP-адрес компьютера&#39;s                                      |
|  ANY  |                                     Указывает IP-адрес компьютера&#39;s.                                      |
| CNAME |                                    Задает каноническое имя для псевдонима.                                     |
|  ОПЕРАЦИОННОЙ  |                                  Задает идентификатор группы для имени группы.                                  |
| HINFO |                          Указывает компьютер&#39;процессора и тип операционной системы.                           |
|  МБ   |                                        Указывает доменное имя почтового ящика.                                         |
|  MG   |                                         Указывает члена почтовой группы.                                          |
| СООТВЕТСТВУЮЩУЮ |                                   Указывает сведения о почтовом ящике или списке рассылки.                                   |
|  MR   |                                     Указывает имя домена переименования почты.                                      |
|  MX   |                                          Указывает почтовый обменник.                                          |
|  NS   |                                 Указывает сервер DNS-имен для именованной зоны.                                 |
|  PTR  | Указывает имя компьютера, если запрос является IP-адресом; в противном случае указывает указатель на другую информацию. |
|  SOA  |                                Указывает начальную зону для зоны DNS.                                 |
|  TXT  |                                         Задает текстовую информацию.                                         |
|  ИД пользователя  |                                         Указывает идентификатор пользователя.                                          |
| уинфо |                                         Указывает сведения о пользователе.                                         |
|  ЕЙ  |                                         Описание хорошо известной службы.                                         |
| {Справка |                                                       ?}                                                        |

Отображает краткую сводку подкоманд <strong>nslookup</strong> .
## <a name="remarks"></a>Примечания
- Команда <strong>Set Type</strong> выполняет ту же функцию, что и команда <strong>Set QueryType</strong> .
- Дополнительные сведения о типах записей ресурсов см. в статье запрос комментария (RFC) 1035.
  ## <a name="additional-references"></a>Дополнительные ссылки
  <параметр href = Command-Line-синтаксис-key.md Data-RAW-source =- [Командная строка](command-line-syntax-key.md) ,>синтаксис командной строки</a> <a href = nslookup-set-QueryType.md Data-RAW-source =[nslookup set QueryType](nslookup-set-querytype.md)>nslookup set QueryType</a>
