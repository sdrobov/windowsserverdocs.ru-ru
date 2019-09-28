---
title: nslookup set type
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5248e314-fac1-413e-81dc-bbe0a0873ba5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e3f41cb6bc5117fdd26bba85c6cfd806414bbab4
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372879"
---
# <a name="nslookup-set-type"></a>nslookup set type

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет тип записи ресурса для запроса.
## <a name="syntax"></a>Синтаксис
```
set type=<ResourceRecordtype>
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

Отображает краткую сводку подкоманд <strong>nslookup</strong> .
## <a name="remarks"></a>Примечания
- Команда <strong>Set Type</strong> выполняет ту же функцию, что и команда <strong>Set QueryType</strong> .
- Дополнительные сведения о типах записей ресурсов см. в статье запрос комментария (RFC) 1035.
  ## <a name="additional-references"></a>Дополнительные ссылки
  <a href="command-line-syntax-key.md" data-raw-source="[Command-Line Syntax Key](command-line-syntax-key.md)">Ключ синтаксиса командной строки</a><a href="nslookup-set-querytype.md" data-raw-source="[nslookup set querytype](nslookup-set-querytype.md)">nslookup set QueryType</a> 
  
