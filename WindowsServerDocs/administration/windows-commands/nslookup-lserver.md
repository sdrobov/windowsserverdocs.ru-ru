---
title: nslookup lserver
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0c4e1ed4697666062bb90f4a9c65054a3dd73661
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59848055"
---
# <a name="nslookup-lserver"></a>nslookup lserver

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Изменение сервера по умолчанию к указанному домену доменных имен (DNS).
## <a name="syntax"></a>Синтаксис
```
lserver <DNSDomain> 
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|<DNSDomain>|Указывает новый домен DNS для сервера по умолчанию.|
|{help &#124; ?}|Отображает краткое описание **nslookup** подкоманды.|
## <a name="remarks"></a>Примечания
-   **Lserver** команда использует исходным сервером для поиска сведений о домене DNS. Это отличается от **server** команду, которая использует текущий сервер.
## <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[nslookup server](nslookup-server.md)
