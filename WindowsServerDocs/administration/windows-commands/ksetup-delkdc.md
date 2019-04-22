---
title: ksetup:delkdc
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7d6ec389-094c-4a7b-a78b-605497ddc289
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6e2fa065ca60338b04cc8718e199805cc494c908
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814565"
---
# <a name="ksetupdelkdc"></a>ksetup:delkdc



Удаляет экземпляры имен центра распространения ключей (KDC) для области Kerberos. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /delkdc <RealmName> <KDCName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<RealmName>|Имя области указывается как верхний регистр DNS-имя, например CORP. CONTOSO.COM и указана как область по умолчанию при **ksetup** выполняется. Это для этой области, из которого вы пытаетесь удалить другие KDC.|
|\<KDCName>|Без учета регистра, полное доменное имя, например mitkdc.contoso.com указанное имя контроллера Kerberos-домена.|

## <a name="remarks"></a>Примечания

Эти сопоставления хранятся в реестре в **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\LSA\Kerberos\Domains**. Чтобы удалить данные конфигурации области с нескольких компьютеров, используйте шаблон конфигурации безопасности оснастки и политики распространения вместо использования **ksetup** явным образом на отдельных компьютерах.

На компьютерах под управлением Windows 2000 Server с пакетом обновления 1 (SP1) и более ранних версий необходимо перезагрузить компьютер, прежде чем будет использована конфигурация параметр измененные сферы.

Для проверки имени области по умолчанию для компьютера или убедитесь, что эта команда работает должным образом, запустите **ksetup** в командной строке и убедитесь, что в списке отсутствует KDC, который был удален.

## <a name="BKMK_Examples"></a>Примеры

Требования безопасности для этого компьютера были изменены, поэтому необходимо удалить связь между сферы Windows и сферой отличных от Windows. Сначала определите, какие связи для удаления и выходной набор данных существующих связей:
```
ksetup
```
Удалите связь с помощью следующей команды:
```
Ksetup /delkdc CORP.CONTOSO.COM mitkdc.contoso.com
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)