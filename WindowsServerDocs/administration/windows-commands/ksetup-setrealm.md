---
title: 'ksetup: сетреалм'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab268c40-276b-46ef-ab16-d5ce7667fbed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1bbe5c000b7e84066c19511639fe3d92d7e4b558
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374897"
---
# <a name="ksetupsetrealm"></a>ksetup: сетреалм



Задает имя области Kerberos. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /setrealm <DNSDomainName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0DNSDomainName >|Доменное имя DNS может иметь форму полного доменного имени или простого доменного имени.|

## <a name="remarks"></a>Примечания

Параметр доменного имени DNS следует вводить прописными буквами. В противном случае команда **ksetup** запросит подтверждение для продолжения.

Установка области Kerberos на контроллере домена не поддерживается. Попытка сделать это вызовет предупреждение и сбой команды.

## <a name="BKMK_Examples"></a>Примеров

Задайте для области этого компьютера определенное доменное имя, чтобы ограничить доступ неконтроллером домена только с областью Kerberos CONTOSO:
```
ksetup /setrealm CONTOSO
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Ksetup](ksetup.md)
-   [Ksetup:removerealm](ksetup-removerealm.md)