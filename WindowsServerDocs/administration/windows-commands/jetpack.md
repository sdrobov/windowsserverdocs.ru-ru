---
title: jetpack
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 82a2b7ef-0db5-4575-a028-8acb0bf6c7ba
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 008e9dd4d41fe270d775b1c44d799dd16429046f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841977"
---
# <a name="jetpack"></a>jetpack

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

сжимает службу Windows Internet Name Service (WINS) или базу данных протокола DHCP. Корпорация Майкрософт рекомендует сжимать базу данных WINS при каждом приближении 30 МБ. 

## <a name="syntax"></a>Синтаксис
```
jetpack.EXE <database name> <temp database name>
```

#### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|<database name>|Указывает исходный файл базы данных.|
|<temp database name>|Указывает временный файл базы данных.|
|/?|Отображает справку в командной строке.|

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров
Чтобы сжать базу данных WINS, выполните следующие действия.
```
cd %SYSTEMROOT%\SYSTEM32\WINS
NET STOP WINS
jetpack WINS.MDB TMP.MDB
NET start WINS
```
Чтобы сжать базу данных DHCP, выполните следующие действия.
```
cd %SYSTEMROOT%\SYSTEM32\DHCP
NET STOP DHCPSERver
jetpack DHCP.MDB TMP.MDB
NET start DHCPSERver
```
В приведенных выше примерах файл **tmp. mdb** является временной базой данных, используемой программой Jetpack. exe. **WINS. mdb** — это база данных WINS. **DHCP. mdb** — это база данных DHCP.
Программа Jetpack. exe сжимает базу данных WINS или DHCP, выполняя следующие действия.
1.  Копирует сведения из базы данных во временный файл базы данных с именем **tmp. mdb**.
2.  удаляет исходный файл базы данных, **WINS. mdb** или **DHCP. mdb**.
3.  Переименовывает временные файлы базы данных в исходное имя файла.

> [!NOTE]
> В процессе сжатия программа Jetpack. exe создает временный файл с именем, указанным в параметре *имени временной базы данных* . Временный файл удаляется по завершении сжатия. Убедитесь, что у вас нет файла, существующего в папке WINS или DHCP, имя которой совпадает с именем, указанным в параметре *имени временной базы данных* .

## <a name="additional-references"></a>Дополнительные материалы
-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
