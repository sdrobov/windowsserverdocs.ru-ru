---
title: pubprn
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0bc7f7e3-84e1-4359-b477-7b1a1a0bd639
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 499ff2ade7ffc6c608791ba3da0ede0c3282c13d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59831705"
---
# <a name="pubprn"></a>pubprn

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Публикация принтера в доменных службах active directory.

## <a name="syntax"></a>Синтаксис
```
cscript pubprn {<ServerName> | <UNCprinterpath>} 
"LDAP://CN=<Container>,DC=<Container>"
```

## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|\<Имя_сервера >|Указывает имя сервера Windows, на котором размещена принтера, которое вы хотите опубликовать. Если компьютер не указан, используется локальный компьютер.|
|\<UNCprinterpath >|Соглашения об универсальных именах (UNC) путь к общему принтеру, который вы хотите опубликовать.|
|"LDAP://CN=<Container>,DC=<Container>"|Указывает путь к контейнеру в доменных службах active directory, где вы хотите опубликовать принтер.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания
-   **Pubprn** команда — это сценарий Visual Basic, расположенный в %WINdir%\System32\printing_Admin_Scripts\\ <language> каталога. Чтобы использовать эту команду в командной строке, введите **cscript** следуют полный путь к файлу pubprn, или изменить каталоги в соответствующую папку. Пример:
    ```
    cscript %WINdir%\System32\printing_Admin_Scripts\en-US\pubprn
    ```
-   Если сведения, которые вы предоставляете содержит пробелы, используйте кавычки вокруг текста (например, `"computer Name"`).

## <a name="BKMK_examples"></a>Примеры
Чтобы опубликовать все принтеры на \\\Server1 компьютера в контейнер MyContainer в домене MyDomain.company.Com, введите:
```
cscript Ppubprn Server1 "LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com"
```
Чтобы опубликовать принтер Laserprinter1 на \\\Server1 сервера в MyContainer контейнер в домене MyDomain.company.Com, тип:
```
cscript Ppubprn \\Server1\Laserprinter1 "LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com"
```

#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[команды печати](print-command-reference.md)
