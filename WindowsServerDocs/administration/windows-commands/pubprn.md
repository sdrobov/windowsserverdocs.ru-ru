---
title: pubprn
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 844a13c1a650ebedcc0d5b4fbf65b9de671b2180
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372011"
---
# <a name="pubprn"></a>pubprn

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Публикует принтер в доменных службах Active Directory.

## <a name="syntax"></a>Синтаксис
```
cscript pubprn {<ServerName> | <UNCprinterpath>} 
"LDAP://CN=<Container>,DC=<Container>"
```

## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|\<ServerName >|Указывает имя сервера Windows, на котором размещен принтер, который требуется опубликовать. Если компьютер не указан, используется локальный компьютер.|
|\<Ункпринтерпас >|UNC-путь к общему принтеру, который требуется опубликовать.|
|"LDAP://CN =<Container>, DC =<Container>"|Указывает путь к контейнеру в доменных службах Active Directory, в котором требуется опубликовать принтер.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Замечания
-   Команда **Pubprn** — это Visual Basic сценарий, расположенный в каталоге%windir%\system32\ printing_Admin_Scripts\\<language>. Чтобы использовать эту команду, в командной строке введите **cscript** , а затем полный путь к файлу Pubprn или измените каталоги на соответствующую папку. Например:
    ```
    cscript %WINdir%\System32\printing_Admin_Scripts\en-US\pubprn
    ```
-   Если предоставленные сведения содержат пробелы, заключите текст в кавычки (например, `"computer Name"`).

## <a name="BKMK_examples"></a>Примеров
Чтобы опубликовать все принтеры на компьютере \\\Server1 в контейнере MyContainer в домене MyDomain.company.Com, введите:
```
cscript Ppubprn Server1 "LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com"
```
Чтобы опубликовать принтер Laserprinter1 на сервере \\\Server1 в контейнер MyContainer в домене MyDomain.company.Com, введите:
```
cscript Ppubprn \\Server1\Laserprinter1 "LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com"
```

#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[Печать справочника по командам](print-command-reference.md)
