---
title: pubprn
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0bc7f7e3-84e1-4359-b477-7b1a1a0bd639
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8696a372902f36f703670cf514bddf75cf4cc7e3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837107"
---
# <a name="pubprn"></a>pubprn

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Публикует принтер в доменных службах Active Directory.

## <a name="syntax"></a>Синтаксис
```
cscript pubprn {<ServerName> | <UNCprinterpath>} 
LDAP://CN=<Container>,DC=<Container>
```

### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|\<ServerName >|Указывает имя сервера Windows, на котором размещен принтер, который требуется опубликовать. Если компьютер не указан, используется локальный компьютер.|
|\<Ункпринтерпас >|UNC-путь к общему принтеру, который требуется опубликовать.|
|LDAP://CN =<Container>, DC =<Container>|Указывает путь к контейнеру в доменных службах Active Directory, в котором требуется опубликовать принтер.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания
-   Команда **Pubprn** — это Visual Basic сценарий, расположенный в каталоге%windir%\system32\ printing_Admin_Scripts\\<language>. Чтобы использовать эту команду, в командной строке введите **cscript** , а затем полный путь к файлу Pubprn или измените каталоги на соответствующую папку. Например:
    ```
    cscript %WINdir%\System32\printing_Admin_Scripts\en-US\pubprn
    ```
-   Если предоставленные сведения содержат пробелы, заключите текст в кавычки (например, `computer Name`).

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
Чтобы опубликовать все принтеры на компьютере \\\Server1 в контейнере MyContainer в домене MyDomain.company.Com, введите:
```
cscript Ppubprn Server1 LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com
```
Чтобы опубликовать принтер Laserprinter1 на сервере \\\Server1 в контейнер MyContainer в домене MyDomain.company.Com, введите:
```
cscript Ppubprn \\Server1\Laserprinter1 LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com
```

## <a name="additional-references"></a>Дополнительные материалы
- [Ключ синтаксиса командной строки](command-line-syntax-key.md)
[Печать справочника по командам](print-command-reference.md)
