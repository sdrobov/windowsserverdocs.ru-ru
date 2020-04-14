---
title: Преобразование команду scwcmd
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 640dd892-0bb9-416d-8318-60a26605bcf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1fed9ff6369e6c966d9d1f5295db7db6648a1ab1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835127"
---
# <a name="scwcmd-transform"></a>Scwcmd: transform

> Область применения: Windows Server 2012 R2, Windows Server 2012

Преобразует файл политики безопасности, созданный с помощью мастера настройки безопасности (SCW), в новый объект групповая политика (GPO) в службах домен Active Directory Services. Операция преобразования не изменяет никаких параметров на сервере, на котором он выполняется. После завершения операции преобразования администратор должен связать объект GPO с нужными подразделениями, чтобы развернуть политику на серверах.

Для завершения операции преобразования требуются учетные данные администратора домена.

> [!IMPORTANT]
> Параметры политики безопасности службы IIS (IIS) не могут быть развернуты с помощью групповая политика.</br>> Политики брандмауэра, в которых список утвержденных приложений не следует развертывать на серверах, если служба брандмауэра Windows не запускается автоматически при последнем запуске сервера.

Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
scwcmd transform /p:<Policyfile.xml> /g:<GPODisplayName>
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/p:\<Полицифиле. XML >|Указывает путь и имя файла политики XML, который следует применить. Этот параметр должен быть указан.|
|/g:\<Гподисплайнаме >|Указывает отображаемое имя объекта групповой политики. Этот параметр должен быть указан.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

Команду scwcmd. exe доступен только на компьютерах под управлением Windows Server 2008 R2, Windows Server 2008 или Windows Server 2003.

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

Чтобы создать объект групповой политики с именем Филесерверсекурити из файла с именем Филесерверполици. XML, введите:
```
scwcmd transform /p:FileServerPolicy.xml /g:FileServerSecurity
```

## <a name="additional-references"></a>Дополнительные материалы

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)