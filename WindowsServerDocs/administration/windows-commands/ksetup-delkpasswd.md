---
title: 'ksetup: делкпассвд'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2db0bfcd-bc08-48e3-9f30-65b6411839c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b849265e6036f338413b75fe1da2067e4cdb4cd8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841657"
---
# <a name="ksetupdelkpasswd"></a>ksetup: делкпассвд

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

удаляет сервер паролей Kerberos (Кпассвд) для области. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).
## <a name="syntax"></a>Синтаксис
```
ksetup /delkpasswd <RealmName> <KpasswdName>
```
#### <a name="parameters"></a>Параметры

|   Параметр   |                                                                                                   Описание                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <RealmName>  |                                Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM и указывается в качестве области по умолчанию или области = при запуске **ksetup** .                                |
| <KpasswdName> | Имя KDC, используемое в качестве сервера паролей Kerberos, называется без учета регистра, полное доменное имя, например mitkdc.contoso.com. Если имя KDC пропущено, для размещения Кдкс может использоваться DNS. |

## <a name="remarks"></a>Примечания
Выполните команду **ksetup** , чтобы проверить имя KDC. Если **кпассвд =** не отображается в выходных данных, сопоставление не было настроено. Если задано значение, будут перечислены несколько сопоставлений.
## <a name="examples"></a><a name=BKMK_Examples></a>Примеров
Проверьте КОРПОРАТИВную область. CONTOSO.COM использует в качестве сервера паролей не Windows Server KDC mitkdc.contoso.com:
```
ksetup /delkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```
Чтобы убедиться в том, что команда работала правильно, запустите **ksetup** на компьютере Windows, чтобы убедиться в наличии сферы Corp. CONTOSO.COM не сопоставляется с сервером паролей Kerberos (имя KDC).
## <a name="additional-references"></a>Дополнительные материалы
-   [ksetup](ksetup.md)
-   [ksetup: делкпассвд](ksetup-delkpasswd.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
