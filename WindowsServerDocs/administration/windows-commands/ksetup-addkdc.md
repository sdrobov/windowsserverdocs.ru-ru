---
title: ksetup:addkdc
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: d3e0d38bdec11618561ee4acaa32ffdd06695fab
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59868535"
---
# <a name="ksetupaddkdc"></a>ksetup:addkdc



Добавляет адрес центра распространения ключей (KDC) для данной области Kerberos. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addkdc <RealmName> [<KDCName>] 
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<RealmName>|Имя области указывается как верхний регистр DNS-имя, например CORP. CONTOSO.COM и указана как область по умолчанию при **ksetup** выполняется. Это для этой области, в которой вы пытаетесь добавить другие KDC.|
|\<KDCName>|Без учета регистра полное доменное имя, например mitkdc.microsoft.com указанное имя контроллера Kerberos-домена. Если отсутствует имя KDC, DNS будет находить KDC.|

## <a name="remarks"></a>Примечания

Эти сопоставления хранятся в разделе реестра **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\LSA\Kerberos\Domains**. Чтобы развертывать данные конфигурации сферы Kerberos на нескольких компьютерах, используйте шаблон конфигурации безопасности оснастки и политики распространения вместо использования **ksetup** явным образом на отдельных компьютерах.

Необходимо перезагрузить компьютер, прежде чем будет использоваться новый параметр области.

Для проверки имени области по умолчанию для компьютера или убедитесь, что эта команда работает должным образом, запустите **ksetup** следующую команду и проверьте выходные данные для добавленных KDC.

## <a name="BKMK_Examples"></a>Примеры

Настройте сервер KDC, отличных от Windows и областью, который следует использовать рабочую станцию.
```
ksetup /addkdc CORP.CONTOSO.COM mitkdc.contoso.com
```
Запустите средство Ksetup из командной строки на одном компьютере, как показано выше команду, чтобы задать пароль учетной записи локального компьютера «p@sswrd1%?. Перезагрузите компьютер.
```
Ksetup /setcomputerpassword p@sswrd1%
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ksetup](ksetup.md)
-   [ksetup:setcomputerpassword](ksetup-setcomputerpassword.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)