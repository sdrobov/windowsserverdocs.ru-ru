---
title: 'ksetup: сетреалм'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ab268c40-276b-46ef-ab16-d5ce7667fbed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: acdbfaabe341c8efb19c6e9d183022375f679de7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841317"
---
# <a name="ksetupsetrealm"></a>ksetup: сетреалм



Задает имя области Kerberos. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /setrealm <DNSDomainName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Днсдомаиннаме >|Доменное имя DNS может иметь форму полного доменного имени или простого доменного имени.|

## <a name="remarks"></a>Примечания

Параметр доменного имени DNS следует вводить прописными буквами. В противном случае команда **ksetup** запросит подтверждение для продолжения.

Установка области Kerberos на контроллере домена не поддерживается. Попытка сделать это вызовет предупреждение и сбой команды.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Задайте для области этого компьютера определенное доменное имя, чтобы ограничить доступ неконтроллером домена только с областью Kerberos CONTOSO:
```
ksetup /setrealm CONTOSO
```

## <a name="additional-references"></a>Дополнительные материалы

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Ksetup](ksetup.md)
-   [Ksetup:removerealm](ksetup-removerealm.md)