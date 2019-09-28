---
title: Преобразование команду scwcmd
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 640dd892-0bb9-416d-8318-60a26605bcf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 36ee3a99828c7fdd9d4fc0ca14cbc0e203b01ea0
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384307"
---
# <a name="scwcmd-transform"></a>Scwcmd: transform

> Область применения. Windows Server 2012 R2, Windows Server 2012

Преобразует файл политики безопасности, созданный с помощью мастера настройки безопасности (SCW), в новый объект групповая политика (GPO) в службах домен Active Directory Services. Операция преобразования не изменяет никаких параметров на сервере, на котором он выполняется. После завершения операции преобразования администратор должен связать объект GPO с нужными подразделениями, чтобы развернуть политику на серверах.

Для завершения операции преобразования требуются учетные данные администратора домена.

> [!IMPORTANT]
> Параметры политики безопасности службы IIS (IIS) не могут быть развернуты с помощью групповая политика.</br>> Политики брандмауэра, в которых список утвержденных приложений не следует развертывать на серверах, если служба брандмауэра Windows не запускается автоматически при последнем запуске сервера.

Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
scwcmd transform /p:<Policyfile.xml> /g:<GPODisplayName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/p: @no__t -0Policyfile. XML >|Указывает путь и имя файла политики XML, который следует применить. Этот параметр должен быть указан.|
|/g: @no__t 0GPODisplayName >|Указывает отображаемое имя объекта групповой политики. Этот параметр должен быть указан.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Команду scwcmd. exe доступен только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="BKMK_Examples"></a>Примеров

Чтобы создать объект групповой политики с именем Филесерверсекурити из файла с именем Филесерверполици. XML, введите:
```
scwcmd transform /p:FileServerPolicy.xml /g:FileServerSecurity
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)