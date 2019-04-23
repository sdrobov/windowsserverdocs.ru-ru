---
title: Преобразование Scwcmd
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 8a6a6e37c2c2a362f3aa0aeadef615ff5065713f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59843815"
---
# <a name="scwcmd-transform"></a>Scwcmd: transform

> Область применения. Windows Server 2012 R2, Windows Server 2012

Преобразует файл политики безопасности, созданные с помощью мастера настройки безопасности (SCW) в новый групповой политики объект (GPO) в доменных службах Active Directory. Операция преобразования не меняет все параметры на сервере, где он выполняется. После завершения операции преобразования, администратору необходимо связать объект групповой Политики нужного подразделения для развертывания на серверах политики.

Учетные данные администратора домена необходимы для завершения операции преобразования.

> [!IMPORTANT]
> Параметры политики безопасности Internet Information Services (IIS) не может развертываться с помощью групповой политики.</br>> Политики брандмауэра, что список утверждения приложений не следует развертывать на серверах, если служба брандмауэра Windows не запущена автоматически последнего сервера к работе.

Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
scwcmd transform /p:<Policyfile.xml> /g:<GPODisplayName>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/p:\<Policyfile.xml>|Указывает путь и имя XML-файла политики, который следует применить. Этот параметр должен быть указан.|
|/g:\<GPODisplayName>|Указывает отображаемое имя объекта групповой Политики. Этот параметр должен быть указан.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания

Scwcmd.exe доступна только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="BKMK_Examples"></a>Примеры

Чтобы создать объект групповой Политики с именем FileServerSecurity из файла с именем FileServerPolicy.xml, введите:
```
scwcmd transform /p:FileServerPolicy.xml /g:FileServerSecurity
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)