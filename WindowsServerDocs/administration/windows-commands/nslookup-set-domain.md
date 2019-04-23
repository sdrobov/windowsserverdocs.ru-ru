---
title: nslookup set domain
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d4d28e8-6e88-42cc-801f-94e9d8e051f4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9019893d92201079fb60b820a14dda3763bafd6b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886645"
---
# <a name="nslookup-set-domain"></a>nslookup set domain

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет имя домена доменных имен (DNS) по умолчанию к имени, указанному.
## <a name="syntax"></a>Синтаксис
```
set domain=<DomainName>
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|<DomainName>|Указывает новое имя для DNS-имя домена по умолчанию. Имя домена по умолчанию — имя узла.|
|{help &#124; ?}|Отображает краткое описание **nslookup** подкоманды.|
## <a name="remarks"></a>Примечания
-   DNS-имя домена по умолчанию добавляется к запросу поиска в зависимости от состояния **defname** и **поиска** параметры. Список поиска DNS домена содержит родительские для домена DNS, если он имеет по крайней мере два компонента в его имени. Например если DNS-домена по умолчанию — mfg.widgets.com, список поиска называется mfg.widgets.com и widgets.com. Используйте **set srchlist используется** команду, чтобы указать другой список и **установить все** команду, чтобы отобразить в списке.
## <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[nslookup set srchlist используется](nslookup-set-srchlist.md)
[nslookup задать все](nslookup-set-all.md)
