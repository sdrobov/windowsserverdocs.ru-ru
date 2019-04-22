---
title: dcgpofix
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81d5fa65-2aea-49d3-b353-357441846c00
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 91fceb429ca00b1b3d9d36d01f5e97cfd464ccb9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825165"
---
# <a name="dcgpofix"></a>dcgpofix



Повторно создает по умолчанию объекты групповой политики (GPO) для домена. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
DCGPOFix [/ignoreschema] [/target: {Domain | DC | Both}] [/?]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/ignoreschema|Не учитывает версию mc схемы Active Directory®</br>При выполнении этой команды. В противном случае команда работает только на ту же версию схемы, что версия Windows, в котором поставляется команды.|
|/ target {домена | DC | Оба}|Указывает, какие объекты групповой Политики для восстановления. Можно восстановить GPO политики домена по умолчанию и GPO контроллеров домена по умолчанию.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

-   **Dcgpofix** команда доступна в Windows Server 2008 R2 и Windows Server 2008, за исключением установки основных серверных компонентов.
-   Несмотря на то, что консоль управления групповыми политиками (GPMC) входит в состав Windows Server 2008 R2 и Windows Server 2008, необходимо установить управление групповой политикой как функцию с помощью диспетчера серверов.

## <a name="BKMK_Examples"></a>Примеры

Восстановите GPO политики домена по умолчанию в исходное состояние. Вы потеряете все изменения, внесенные в этот объект групповой Политики. Рекомендуется следует настроить GPO политики домена по умолчанию только для управления параметрами политики учетных записей по умолчанию, политики паролей, политики блокировки учетных записей и политика Kerberos. В этом примере игнорировать версию схемы Active Directory, чтобы **dcgpofix** команды не ограничивается же схему, что версия Windows, в котором поставляется команды.
```
dcgpofix /ignoreschema /target:Domain
```
По умолчанию Групповой политики восстановите в исходное состояние. Вы потеряете все изменения, внесенные в этот объект групповой Политики. Рекомендуется необходимо настроить по умолчанию Групповой политики только к задать права пользователя и политики аудита. В этом примере игнорировать версию схемы Active Directory, чтобы **dcgpofix** команды не ограничивается же схему, что версия Windows, в котором поставляется команды.
```
dcgpofix /ignoreschema /target:DC
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Групповая политика](https://go.microsoft.com/fwlink/?LinkID=145531)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)