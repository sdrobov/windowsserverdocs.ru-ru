---
title: Набор подкоманд-Дриверпаккаже
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11804bb6-ca29-4461-8c63-5131748cd742
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 65751cf6e03baa87c7734b318a26111652bee0a1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370818"
---
# <a name="subcommand-set-driverpackage"></a>Подкоманда: Set-Дриверпаккаже



Переименовывает и (или) включает или отключает пакет драйверов на сервере.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Set-DriverPackage [/Server:<Server name>] {/DriverPackage:<Name> | /PackageId:<ID>} [/Name:<New Name>] [/Enabled:{Yes | No}
```

## <a name="parameters"></a>Параметры

|        Параметр         |                                                                                                                                                                                                               Описание                                                                                                                                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server: \<Server имя >] |                                                                                                                                                 Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.                                                                                                                                                 |
| [/Дриверпаккаже: @no__t — 0Name >] |                                                                                                                                                                                       Указывает текущее имя пакета драйверов для изменения.                                                                                                                                                                                        |
|    [/Паккажеид: @no__t — 0ID >]    | Указывает идентификатор служб развертывания Windows для пакета драйверов. Этот параметр необходимо указать, если пакет драйверов не может быть однозначно идентифицирован по имени. Чтобы найти этот идентификатор для пакета, щелкните группу драйверов, в которой находится пакет (или узел **все пакеты** ), щелкните пакет правой кнопкой мыши и выберите пункт **свойства**. Идентификатор пакета указан на вкладке **Общие** . Например: {DD098D20-1850-4FC8-8E35-EA24A1BEFF5E}. |
|   [/Name: \<New имя >]    |                                                                                                                                                                                              Указывает новое имя для пакета драйверов.                                                                                                                                                                                              |
|      [/Enabled: {Yes      |                                                                                                                                                                                                                   Не                                                                                                                                                                                                                    |

## <a name="BKMK_examples"></a>Примеров

Чтобы изменить параметры пакета, введите одно из следующих значений:
```
WDSUTIL /Set-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318} /Name:MyDriverPackage
```
```
WDSUTIL /Set-DriverPackage /DriverPackage:MyDriverPackage /Name:NewName /Enabled:Yes
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)