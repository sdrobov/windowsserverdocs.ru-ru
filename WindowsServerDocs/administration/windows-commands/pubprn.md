---
title: pubprn
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0bc7f7e3-84e1-4359-b477-7b1a1a0bd639
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 17ca9e98ef9e3423521b03c5c21be4b3f1538b62
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722780"
---
# <a name="pubprn"></a>pubprn

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Публикует принтер в доменных службах Active Directory.

## <a name="syntax"></a>Синтаксис
```
cscript pubprn {<ServerName> | <UNCprinterpath>} 
LDAP://CN=<Container>,DC=<Container>
```

### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|\<Имя сервера>|Указывает имя сервера Windows, на котором размещен принтер, который требуется опубликовать. Если компьютер не указан, используется локальный компьютер.|
|\<Ункпринтерпас>|UNC-путь к общему принтеру, который требуется опубликовать.|
|LDAP://CN =<Container>, DC =<Container>|Указывает путь к контейнеру в доменных службах Active Directory, в котором требуется опубликовать принтер.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания
-   Команда **Pubprn** является сценарием Visual Basic, расположенным в каталоге%WINDIR%\system32\\\ <language> printing_Admin_Scripts. Чтобы использовать эту команду, в командной строке введите **cscript** , а затем полный путь к файлу Pubprn или измените каталоги на соответствующую папку. Пример:
    ```
    cscript %WINdir%\System32\printing_Admin_Scripts\en-US\pubprn
    ```
-   Если предоставленные сведения содержат пробелы, заключите текст в кавычки (например, `computer Name`).

## <a name="examples"></a>Примеры
Чтобы опубликовать все принтеры на \\компьютере \Server1 в контейнере MyContainer в домене mydomain.Company.com, введите:
```
cscript Ppubprn Server1 LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com
```
Чтобы опубликовать принтер Laserprinter1 на сервере \\\Server1 в контейнер MyContainer в домене mydomain.Company.com, введите:
```
cscript Ppubprn \\Server1\Laserprinter1 LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com
```

## <a name="additional-references"></a>Дополнительные ссылки
- [Справочник по синтаксису](command-line-syntax-key.md)
[командной](print-command-reference.md) строки для команды Print
