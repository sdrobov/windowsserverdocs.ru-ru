---
Title: bitsadmin кэша и setexpirationtime Описание: «Раздел Windows команды для **bitsadmin кэша и setexpirationtime** -задает время истечения срока действия кэша.»
ms.custom: na ms.prod: windows-server-threshold ms.reviewer: na ms.suite: na ms.technology: manage-windows-commands ms.tgt_pltfrm: na ms.topic: article ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d author: coreyp-at-msft ms.author: coreyp manager: dongill ms.date: 10/16/2017 --

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

# <a name="bitsadmin-cache-and-setexpirationtime"></a>кэш bitsadmin и setexpirationtime
Задает время истечения срока действия кэша.
## <a name="syntax"></a>Синтаксис
```
bitsadmin /Cache /SetExpirationtime secs
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|сек|Количество секунд до истечения срока действия кэша.|
## <a name="BKMK_examples"></a>Примеры
Следующий пример кэша истекает через 60 секунд.
```
C:\>bitsadmin /Cache / SetExpirationtime 60
```
## <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
