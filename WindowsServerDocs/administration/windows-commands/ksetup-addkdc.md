---
title: 'ksetup: аддкдк'
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 98bfc23a-14c4-401c-bcb3-9903c5cdde64
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 76d592e4f1c32305d6f939a66a6ad42cd582b032
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724768"
---
# <a name="ksetupaddkdc"></a>ksetup: аддкдк



Добавляет адрес центр распространения ключей (KDC) для данной области Kerberos.

## <a name="syntax"></a>Синтаксис

```
ksetup /addkdc <RealmName> [<KDCName>] 
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Реалмнаме>|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM, и он указывается в качестве области по умолчанию при запуске **ksetup** . Это область, в которую вы пытаетесь добавить другой KDC.|
|\<Кдкнаме>|Имя KDC указывается как полное доменное имя без учета регистра, например mitkdc.microsoft.com. Если имя KDC не указано, DNS обнаружит Кдкс.|

## <a name="remarks"></a>Примечания

Эти сопоставления хранятся в реестре в разделе **HKEY_LOCAL_MACHINE \систем\куррентконтролсет\контрол\лса\керберос\домаинс**. Чтобы развернуть данные конфигурации области Kerberos на нескольких компьютерах, используйте оснастку "шаблон конфигурации безопасности" и распределение политик, а не **ksetup** явным образом на отдельных компьютерах.

Компьютер должен быть перезагружен, прежде чем будет использоваться новый параметр сферы.

Чтобы проверить имя области по умолчанию для компьютера или убедиться, что эта команда работала правильно, запустите **ksetup** из командной строки и проверьте выходные данные для добавленного KDC.

## <a name="examples"></a>Примеры

Настройте сервер KDC, отличный от Windows, и область, которую должна использовать Рабочая станция:
```
ksetup /addkdc CORP.CONTOSO.COM mitkdc.contoso.com
```
Запустите средство Ksetup из командной строки того же компьютера, что и в предыдущей команде, чтобы задать для пароля учетной записи локального компьютера p@sswrd1значение%. Затем перезагрузите компьютер.
```
Ksetup /setcomputerpassword p@sswrd1%
```

## <a name="additional-references"></a>Дополнительные ссылки

-   [Ksetup](ksetup.md)
-   [Ksetup:setcomputerpassword](ksetup-setcomputerpassword.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)