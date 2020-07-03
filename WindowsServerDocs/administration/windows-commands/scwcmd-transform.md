---
title: Преобразование команду scwcmd
description: Справочная статья для * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 640dd892-0bb9-416d-8318-60a26605bcf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b70557b64a4cb68a0435bee9db033c893186dc0c
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932629"
---
# <a name="scwcmd-transform"></a>Scwcmd: transform

> Область применения: Windows Server 2012 R2, Windows Server 2012

Преобразует файл политики безопасности, созданный с помощью мастера настройки безопасности (SCW), в новый объект групповая политика (GPO) в службах домен Active Directory Services. Операция преобразования не изменяет никаких параметров на сервере, на котором он выполняется. После завершения операции преобразования администратор должен связать объект GPO с нужными подразделениями, чтобы развернуть политику на серверах.

Для завершения операции преобразования требуются учетные данные администратора домена.

> [!IMPORTANT]
> Параметры политики безопасности службы IIS (IIS) не могут быть развернуты с помощью групповая политика.</br>> политики брандмауэра, в которых список утвержденных приложений не следует развертывать на серверах, если служба брандмауэра Windows не запускается автоматически при последнем запуске сервера.



## <a name="syntax"></a>Синтаксис

```
scwcmd transform /p:<Policyfile.xml> /g:<GPODisplayName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/p\<Policyfile.xml>|Указывает путь и имя файла политики XML, который следует применить. Этот параметр должен быть указан.|
|/g\<GPODisplayName>|Указывает отображаемое имя объекта групповой политики. Этот параметр должен быть указан.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Комментарии

Scwcmd.exe доступны только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="examples"></a>Примеры

Чтобы создать объект групповой политики с именем Филесерверсекурити из файла с именем FileServerPolicy.xml, введите:
```
scwcmd transform /p:FileServerPolicy.xml /g:FileServerSecurity
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)