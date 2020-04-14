---
title: 'ksetup: аддкдк'
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 98bfc23a-14c4-401c-bcb3-9903c5cdde64
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3bb31cbc8ba7920c4ba609f86202e2e62a705078
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841837"
---
# <a name="ksetupaddkdc"></a>ksetup: аддкдк



Добавляет адрес центр распространения ключей (KDC) для данной области Kerberos. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /addkdc <RealmName> [<KDCName>] 
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Реалмнаме >|Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM, и он указывается в качестве области по умолчанию при запуске **ksetup** . Это область, в которую вы пытаетесь добавить другой KDC.|
|\<Кдкнаме >|Имя KDC указывается как полное доменное имя без учета регистра, например mitkdc.microsoft.com. Если имя KDC не указано, DNS обнаружит Кдкс.|

## <a name="remarks"></a>Примечания

Эти сопоставления хранятся в реестре в разделе **HKEY_LOCAL_MACHINE \систем\куррентконтролсет\контрол\лса\керберос\домаинс**. Чтобы развернуть данные конфигурации области Kerberos на нескольких компьютерах, используйте оснастку "шаблон конфигурации безопасности" и распределение политик, а не **ksetup** явным образом на отдельных компьютерах.

Компьютер должен быть перезагружен, прежде чем будет использоваться новый параметр сферы.

Чтобы проверить имя области по умолчанию для компьютера или убедиться, что эта команда работала правильно, запустите **ksetup** из командной строки и проверьте выходные данные для добавленного KDC.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Настройте сервер KDC, отличный от Windows, и область, которую должна использовать Рабочая станция:
```
ksetup /addkdc CORP.CONTOSO.COM mitkdc.contoso.com
```
Запустите средство Ksetup из командной строки того же компьютера, что и в предыдущей команде, чтобы задать для пароля учетной записи локального компьютера значение p@sswrd1%. Затем перезагрузите компьютер.
```
Ksetup /setcomputerpassword p@sswrd1%
```

## <a name="additional-references"></a>Дополнительные материалы

-   [Ksetup](ksetup.md)
-   [Ksetup:setcomputerpassword](ksetup-setcomputerpassword.md)
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)