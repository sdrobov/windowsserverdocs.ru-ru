---
title: ksetup:delkpasswd
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2db0bfcd-bc08-48e3-9f30-65b6411839c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e487389e0f27f58aacaea2b81d573dc9a965e42f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889085"
---
# <a name="ksetupdelkpasswd"></a>ksetup:delkpasswd

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаляет сервер пароль Kerberos (Kpasswd) для области. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).
## <a name="syntax"></a>Синтаксис
```
ksetup /delkpasswd <RealmName> <KpasswdName>
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|<RealmName>|Имя области указывается как верхний регистр DNS-имя, например CORP. CONTOSO.COM и для них значение по умолчанию области или области = при **ksetup** выполняется.|
|<KpasswdName>|Без учета регистра, полное доменное имя, например mitkdc.contoso.com указанное имя контроллера Kerberos-домена для использования в качестве сервера пароль Kerberos. Если отсутствует имя KDC, DNS может использоваться для поиска KDC.|
## <a name="remarks"></a>Примечания
Выполните команду **ksetup** для проверки имени контроллера Kerberos-домена. Если **kpasswd =** не отображается в выходных данных, то сопоставление не настроен. Будут перечислены несколько сопоставлений, если задать.
## <a name="BKMK_Examples"></a>Примеры
Проверьте область CORP. CONTOSO.COM использует mitkdc.contoso.com сервер KDC, отличных от Windows, что и сервер пароль:
```
ksetup /delkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```
Чтобы проверить, команда работал должным образом, запустите **ksetup** на компьютере Windows для проверки области CORP. CONTOSO.COM не сопоставлен с сервера пароль Kerberos (KDC имя).
## <a name="additional-references"></a>Дополнительные ссылки
-   [Ksetup](ksetup.md)
-   [ksetup:delkpasswd](ksetup-delkpasswd.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
