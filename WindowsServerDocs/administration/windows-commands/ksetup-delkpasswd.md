---
title: 'ksetup: делкпассвд'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: dce7d9666040ff0c234139932ea60e3589dfecb2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375132"
---
# <a name="ksetupdelkpasswd"></a>ksetup: делкпассвд

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

удаляет сервер паролей Kerberos (Кпассвд) для области. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).
## <a name="syntax"></a>Синтаксис
```
ksetup /delkpasswd <RealmName> <KpasswdName>
```
### <a name="parameters"></a>Параметры

|   Параметр   |                                                                                                   Описание                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <RealmName>  |                                Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM и указывается в качестве области по умолчанию или области = при запуске **ksetup** .                                |
| <KpasswdName> | Имя KDC, используемое в качестве сервера паролей Kerberos, называется без учета регистра, полное доменное имя, например mitkdc.contoso.com. Если имя KDC пропущено, для размещения Кдкс может использоваться DNS. |

## <a name="remarks"></a>Примечания
Выполните команду **ksetup** , чтобы проверить имя KDC. Если **кпассвд =** не отображается в выходных данных, сопоставление не было настроено. Если задано значение, будут перечислены несколько сопоставлений.
## <a name="BKMK_Examples"></a>Примеров
Проверьте КОРПОРАТИВную область. CONTOSO.COM использует в качестве сервера паролей не Windows Server KDC mitkdc.contoso.com:
```
ksetup /delkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```
Чтобы убедиться в том, что команда работала правильно, запустите **ksetup** на компьютере Windows, чтобы убедиться в наличии сферы Corp. CONTOSO.COM не сопоставляется с сервером паролей Kerberos (имя KDC).
## <a name="additional-references"></a>Дополнительные ссылки
-   [ksetup](ksetup.md)
-   [ksetup: делкпассвд](ksetup-delkpasswd.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
