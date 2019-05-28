---
title: bootcfg timeout
description: Раздел Windows команды для **время ожидания bootcfg** -изменяет значение времени ожидания операционной системы.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa858eac-2bb7-4a27-a9bc-3e4a6eb8b2c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 47c68ffaad68ff3e29e8060fdb75adf46165c982
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59885525"
---
# <a name="bootcfg-timeout"></a>bootcfg timeout

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет значение времени ожидания операционной системы.

## <a name="syntax"></a>Синтаксис
```
bootcfg /timeout <timeOutValue> [/s <computer> [/u <Domain\User>/p <Password>]]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/ timeout <timeOutValue>|Указывает значение времени ожидания в разделе [загрузчик]. <timeOutValue> Является количество секунд, пользователь должен выбрать операционную систему из экрана начальной загрузки, прежде чем NTLDR загружает значение по умолчанию. Допустимый диапазон значений для <timeOutValue> 0 до 999. Если значение равно 0, затем NTLDR немедленно запускает операционную систему по умолчанию без отображения экрана начальной загрузки.|
|/s <computer>|Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.|
|/u <Domain\User>|Выполняет команду с разрешениями учетной записи пользователя, указанного по <User> или < домен >. По умолчанию используется разрешения текущего, вошедшего в систему пользователя на компьютере, используя следующую команду.|
|/p <Password>|Указывает <Password> учетной записи пользователя, который указан в **/u** параметра.|
|/?|Отображение справки в командной строке.|
## <a name="BKMK_examples"></a>Примеры
В следующих примерах показано, как можно использовать **/timeout bootcfg** команды:
```
bootcfg /timeout 30
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /timeout 50
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)