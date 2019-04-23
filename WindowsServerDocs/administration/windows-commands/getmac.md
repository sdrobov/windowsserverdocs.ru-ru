---
title: getmac
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a749a348-7cd1-4336-9f33-bb42dd0e31e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e356354e63a057201582db0fb74933e1b3ef8d8c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59851045"
---
# <a name="getmac"></a>getmac

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает аппаратный доступ МАС-адрес и список сетевых протоколов, связанных с каждым адресом для всех сетевых плат в каждом компьютере, либо локально или в сети. 
## <a name="syntax"></a>Синтаксис
```
getmac[.exe][/s <computer> [/u <Domain\<User> [/p <Password>]]][/fo {TABLE | list | CSV}][/nh][/v]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|/s <computer>|Указывает имя или IP-адрес удаленного компьютера (не используйте символы обратной косой черты). По умолчанию используется локальный компьютер.|
|/u <Domain>\\<User>|Выполняет команду с разрешениями учетной записи пользователя, указанного пользователем или "домен\пользователь". По умолчанию используется разрешения текущего, вошедшего в систему пользователя на компьютере, используя следующую команду.|
|/p <Password>|Указывает пароль для учетной записи пользователя, который указан в **/u** параметра.|
|/fo { TABLE &#124; list&#124; CSV}|Указывает используемый формат выходных данных запроса. Допустимые значения: **таблицы**, **списка**, и **CSV**. Формат по умолчанию для выходных данных — **таблицы**.|
|/NH|Подавляет заголовок столбца в выходных данных. Допустим, если **/fo** параметр имеет значение **таблицы** или **CSV**.|
|/v|Отображение подробные сведения о выходных данных.|
|/?||
## <a name="remarks"></a>Примечания
**GETMAC** может быть полезен для введите MAC-адрес в сетевой анализатор или если вам нужно знать, какие протоколы в настоящее время используются на каждом сетевом адаптере на компьютере.
## <a name="BKMK_Examples"></a>Примеры
В следующих примерах показано, как можно использовать **getmac** команды:
```
getmac /fo table /nh /v
```
```
getmac /s srvmain
```
```
getmac /s srvmain /u maindom\hiropln
```
```
getmac /s srvmain /u maindom\hiropln /p p@ssW23
```
```
getmac /s srvmain /u maindom\hiropln /p p@ssW23 /fo list /v
```
```
getmac /s srvmain /u maindom\hiropln /p p@ssW23 /fo table /nh
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
