---
title: 'ksetup: аддкдк'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98bfc23a-14c4-401c-bcb3-9903c5cdde64
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 66efe4e56007aff39b83c92dfea2afaadcfc0210
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375213"
---
# <a name="ksetupaddkdc"></a>ksetup: аддкдк



Добавляет адрес центр распространения ключей (KDC) для данной области Kerberos. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addkdc <RealmName> [<KDCName>] 
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0RealmName >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM, и он указывается в качестве области по умолчанию при запуске **ksetup** . Это область, в которую вы пытаетесь добавить другой KDC.|
|@no__t 0KDCName >|Имя KDC указывается как полное доменное имя без учета регистра, например mitkdc.microsoft.com. Если имя KDC не указано, DNS обнаружит Кдкс.|

## <a name="remarks"></a>Примечания

Эти сопоставления хранятся в реестре в разделе **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\LSA\Kerberos\Domains**. Чтобы развернуть данные конфигурации области Kerberos на нескольких компьютерах, используйте оснастку "шаблон конфигурации безопасности" и распределение политик, а не **ksetup** явным образом на отдельных компьютерах.

Компьютер должен быть перезагружен, прежде чем будет использоваться новый параметр сферы.

Чтобы проверить имя области по умолчанию для компьютера или убедиться, что эта команда работала правильно, запустите **ksetup** из командной строки и проверьте выходные данные для добавленного KDC.

## <a name="BKMK_Examples"></a>Примеров

Настройте сервер KDC, отличный от Windows, и область, которую должна использовать Рабочая станция:
```
ksetup /addkdc CORP.CONTOSO.COM mitkdc.contoso.com
```
Запустите средство Ksetup из командной строки того же компьютера, что и в предыдущей команде, чтобы задать для пароля учетной записи локального компьютера значение "p@sswrd1%". Затем перезагрузите компьютер.
```
Ksetup /setcomputerpassword p@sswrd1%
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [Ksetup:setcomputerpassword](ksetup-setcomputerpassword.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)