---
title: nslookup server
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 608267f8-f7b4-412a-8dcd-e08b5ffc2085
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 52a846b1084380d0b40d58d81c11d20dacb407bf
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59869155"
---
# <a name="nslookup-server"></a>nslookup server

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменение сервера по умолчанию к указанному домену доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
server <DNSDomain>
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|<DNSDomain>|Обязательный. Указывает новый домен DNS для сервера по умолчанию.|
|{help &#124; ?}|Отображает краткое описание **nslookup** подкоманды.|
## <a name="remarks"></a>Примечания
-   **Server** команда текущий сервер использует для поиска информации о домене DNS. Это отличается от **lserver** команду, которая использует исходным сервером.
## <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[nslookup lserver](nslookup-lserver.md)
