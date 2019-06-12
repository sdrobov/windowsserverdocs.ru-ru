---
title: nslookup set querytype
description: 'Раздел Windows команды для ***- '
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
ms.openlocfilehash: f0015db716bd8c74bc4366063009bda41d338d19
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436732"
---
# <a name="nslookup-set-querytype"></a>nslookup set querytype

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет тип записи ресурса для запроса.
## <a name="syntax"></a>Синтаксис
```
set querytype=<ResourceRecordtype>
```
## <a name="parameters"></a>Параметры
<ResourceRecordtype> Указывает тип записи ресурса DNS. Тип записи ресурса по умолчанию — A. В следующей таблице перечислены допустимые значения для этой команды.

| Значение |                                                   Описание                                                   |
|-------|-----------------------------------------------------------------------------------------------------------------|
|   Объект   |                                      Указывает компьютер,&#39;IP-адрес                                      |
|  ЛЮБОЙ  |                                     Указывает компьютер,&#39;IP-адрес.                                      |
| ЗАПИСЬ CNAME |                                    Указывает каноническое имя для псевдонима.                                     |
|  GID  |                                  Указывает идентификатор группы для имени.                                  |
| HINFO |                          Указывает компьютер,&#39;s ЦП и тип операционной системы.                           |
|  МБ   |                                        Указывает имя домена почтового ящика.                                         |
|  MG   |                                         Задает член группы электронной почты.                                          |
| MINFO |                                   Указывает сведения о списке почтовых ящиков или почты.                                   |
|  MR   |                                     Указывает имя домена переименования почты.                                      |
|  MX   |                                          Указывает почтовый обменник.                                          |
|  NS   |                                 Указывает имя DNS-сервер для указанной зоны.                                 |
|  PTR  | Указывает компьютер, если запрос является IP-адресом; в противном случае определяет указатель на другие сведения. |
|  SOA  |                                Указывает начало записи зоны для зоны DNS.                                 |
|  TXT  |                                         Задает текстовую информацию.                                         |
|  UID  |                                         Задает идентификатор пользователя.                                          |
| UINFO |                                         Указывает сведения о пользователе.                                         |
|  WKS  |                                         Описывает хорошо известной службы.                                         |
| {справки |                                                       ?}                                                        |

Отображает краткое описание <strong>nslookup</strong> подкоманды
## <a name="remarks"></a>Примечания
- <strong>Задайте тип</strong> команда выполняет ту же функцию, что <strong>задать querytype</strong> команды.
- Дополнительные сведения о типах записей ресурсов см. в разделе Request for Comments (подробнее).
  ## <a name="additional-references"></a>Дополнительные ссылки
  <a href="command-line-syntax-key.md" data-raw-source="[Command-Line Syntax Key](command-line-syntax-key.md)">Ключ синтаксиса команд</a>
  <a href="nslookup-set-type.md" data-raw-source="[nslookup set type](nslookup-set-type.md)">nslookup задайте тип</a>
