---
title: nslookup set domain
description: Справочная статья по команде nslookup set domain, которая изменяет доменное имя DNS по умолчанию на указанное имя.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9d4d28e8-6e88-42cc-801f-94e9d8e051f4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: eaa12029beab301f955a4c9bed4595831f6ebf12
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85934413"
---
# <a name="nslookup-set-domain"></a>nslookup set domain

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменяет доменное имя DNS по умолчанию на указанное имя.

## <a name="syntax"></a>Синтаксис

```
set domain=<domainname>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<domainname>` | Указывает новое имя для доменного имени DNS по умолчанию. Значение по умолчанию — имя узла. |
| /? | Отображение справки в командной строке. |
| /help | Отображение справки в командной строке. |

#### <a name="remarks"></a>Комментарии

- Доменное имя DNS по умолчанию добавляется к поисковому запросу в зависимости от состояния параметров **дефнаме** и **поиска** .

- Список поиска доменов DNS содержит родительские домены DNS по умолчанию, если в имени содержится по крайней мере два компонента. Например, если домен DNS по умолчанию — mfg.widgets.com, список поиска будет называться как mfg.widgets.com, так и widgets.com.

- Используйте команду [nslookup set срчлист](nslookup-set-srchlist.md) , чтобы указать другой список, и команда [nslookup set ALL](nslookup-set-all.md) будет отображать список.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [nslookup set srchlist](nslookup-set-srchlist.md)

- [nslookup set all](nslookup-set-all.md)
