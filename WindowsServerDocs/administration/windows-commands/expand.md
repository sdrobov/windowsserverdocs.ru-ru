---
title: expand
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 66de0488-a0c4-40c2-9b03-e40c107ba343
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5df078af23c77f54ccb2da83b1057c5d7042593a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59825965"
---
# <a name="expand"></a>expand

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Развертывает один или несколько сжатых файлов. Эта команда используется для извлечения сжатых файлов из установочных дисков.  
## <a name="syntax"></a>Синтаксис  
```  
expand [/r] <source> <destination>  
expand /r <source> [<destination>]  
expand /i <source> [<destination>]  
expand /d <source>.cab [/f:<files>]  
expand <source>.cab /f:<files> <destination>  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|/r|Переименовывает извлеченные файлы.|  
|источник|Указывает файлы для развертывания. *Источник* может включать букву диска и двоеточие, имя каталога, имя файла или их сочетание. Можно использовать подстановочные знаки (**\*** или **?**).|  
|назначение|Указывает расположение файлов для расширения.<br /><br />Если *источника* состоит из нескольких файлов и вы не укажете **/r**, *назначения* должен быть каталогом.<br /><br />*Назначение* может включать букву диска и двоеточие, имя каталога, имя файла или их сочетание.<br /><br />Конечный файл &#124; спецификацию пути.|  
|/i|Переименовывает извлеченные файлы, но не учитывает структуру каталогов.<br /><br />Этот параметр применяется к:  Windows Server 2008 R2 и Windows 7.|  
|/d|Отображает список файлов в исходном расположении. Не развернуть или извлечь файлы.|  
|/f:|Указывает файлы в CAB-файл, который требуется расширить. Можно использовать подстановочные знаки (**\*** или **?**).|  
|/?|Отображение справки в командной строке.|  
## <a name="remarks"></a>Примечания  
-   С помощью **разверните** во время восстановления консоли  
    **Разверните** команда, с различными параметрами доступна из консоли восстановления. Дополнительные сведения о консоли восстановления, см. в разделе [статьи 314058](https://support.microsoft.com/kb/314058) в базе знаний Майкрософт.  
## <a name="additional-references"></a>Дополнительные ссылки  
[Ключ синтаксиса командной строки](command-line-syntax-key.md)  
