---
title: lpr
description: Справочная статья по команде lpr, которая отправляет файл на устройство общего доступа к компьютеру или принтеру, на котором выполняется служба LPD, в процессе подготовки к печати.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: afc8790b-8b52-45c4-acdf-be0ffa9da534
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9ea40ef71da7804f01c963049f07e1f6b5395354
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927119"
---
# <a name="lpr"></a>lpr

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отправляет файл на устройство общего доступа к компьютеру или принтеру, работающее со службой LPD, в процессе подготовки к печати.

## <a name="syntax"></a>Синтаксис

```
lpr [-S <servername>] -P <printername> [-C <bannercontent>] [-J <jobname>] [-o | -o l] [-x] [-d] <filename>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| -S`<servername>` | Указывает (по имени или IP-адресу) устройство общего доступа к компьютеру или принтеру, на котором размещена очередь печати LPD, с состоянием, которое необходимо отобразить.  Этот параметр является обязательным и должен быть прописным. |
| -P`<printername> `| Указывает (по имени) принтер для очереди печати с состоянием, которое необходимо отобразить. Чтобы найти имя принтера, откройте папку **принтеры** . Этот параметр является обязательным и должен быть прописным. |
| -C`<bannercontent>` | Указывает содержимое для печати на странице заголовка задания печати. Если этот параметр не указан, имя компьютера, с которого было отправлено задание печати, отображается на странице баннера. Этот параметр должен иметь прописные буквы. |
| -J`<jobname>` | Указывает имя задания печати, которое будет напечатано на странице баннера. Если этот параметр не указан, имя выводимого файла отображается на заголовке страницы. Этот параметр должен иметь прописные буквы. |
| `[-o | -o l]` | Указывает тип файла, который требуется напечатать. Параметр **-o** указывает, что требуется напечатать текстовый файл. Параметр **-o l** указывает, что необходимо напечатать двоичный файл (например, PostScript-файл). |
| -d | Указывает, что файл данных должен быть отправлен перед управляющим файлом. Используйте этот параметр, если для принтера требуется сначала отправить файл данных. Дополнительные сведения см. в документации по принтеру. |
| -X | Указывает, что команда **LPR** должна быть совместима с операционной системой Sun Microsystems (называемой сунос) для выпусков вплоть до 4.1.4_u1. |
| `<filename>` | Задает выводимый файл (по имени). Это обязательный параметр. |
| /? | Отображение справки в командной строке. |

### <a name="examples"></a>Примеры

Чтобы напечатать *Document.txt* текстовый файл в очереди принтера *LASERPRINTER1* на узле LPD в *10.0.0.45*, введите:

```
lpr -S 10.0.0.45 -P Laserprinter1 -o Document.txt
```

Чтобы напечатать файл *PostScript_file. PS* Adobe PostScript в очереди принтера *LASERPRINTER1* на узле LPD в *10.0.0.45*, введите:

```
lpr -S 10.0.0.45 -P Laserprinter1 -o l PostScript_file.ps
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Справочник по командам системы печати](print-command-reference.md)
