---
title: jetpack
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82a2b7ef-0db5-4575-a028-8acb0bf6c7ba
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a3bffc29519df139921bdb1de53e67acd558b306
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858015"
---
# <a name="jetpack"></a>jetpack

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

сжимает базу данных службы имя Windows Internet (WINS) или протокол динамической конфигурации узла (DHCP). Корпорация Майкрософт рекомендует сжатие базы данных WINS, каждый раз, когда он достигает 30 МБ. 

## <a name="syntax"></a>Синтаксис
```
jetpack.EXE <database name> <temp database name>
```

### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|<database name>|Указывает исходный файл базы данных.|
|<temp database name>|Указывает файл временной базы данных.|
|/?|Отображение справки в командной строке.|

## <a name="BKMK_Examples"></a>Примеры
Для сжатия базы данных WINS:
```
cd %SYSTEMROOT%\SYSTEM32\WINS
NET STOP WINS
jetpack WINS.MDB TMP.MDB
NET start WINS
```
Для сжатия базы данных DHCP:
```
cd %SYSTEMROOT%\SYSTEM32\DHCP
NET STOP DHCPSERver
jetpack DHCP.MDB TMP.MDB
NET start DHCPSERver
```
В приведенных выше примеров **Tmp.mdb** является временной базы данных, который используется программой jetpack.exe. **WINS.mdb** является базы данных WINS. **DHCP.mdb** — база данных DHCP.
сжимает Jetpack.exe WINS или базы данных DHCP, выполнив указанные ниже:
1.  Сведения в файл временной базы данных с именем базы данных копируются **Tmp.mdb**.
2.  Удаляет исходный файл базы данных, **Wins.mdb** или **Dhcp.mdb**.
3.  Переименовывает файлы временной базы данных исходного файла.

> [!NOTE]
> В процессе сжатия jetpack.exe создает временный файл с именем, который задается параметром *имя временной базы данных* параметра. Временный файл удаляется при завершении процесса compact. Убедитесь, что у вас нет файла, уже находящихся в WINS или DHCP папку с тем же именем, что и указанный в *имя временной базы данных* параметра.

## <a name="additional-references"></a>Дополнительные ссылки
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
