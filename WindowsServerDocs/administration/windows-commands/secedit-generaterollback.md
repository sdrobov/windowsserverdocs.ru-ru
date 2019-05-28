---
title: Secedit:generaterollback
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 385a6799-51a7-4fe3-bd73-10c7998b6680
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3229e6ccb07c925a900b298a8332c5e48cefefe7
ms.sourcegitcommit: 08eba714d3ceb5f2dfb5486d6b990da1aa4dcbdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65564668"
---
# <a name="seceditgeneraterollback"></a>Secedit:generaterollback



Позволяет создать шаблон отката для шаблона указанной конфигурации. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
Secedit /generaterollback /db <database file name> /cfg <configuration file name> /rbk <rollback template file name> [log <log file name>] [/quiet]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|DB|Обязательный.</br>Указывает путь и имя базы данных, которая содержит хранимую конфигурацию, по которой будет выполняться анализ.</br>Если имя файла содержит имя базы данных, для которой не безопасности шаблон (как определено в файле конфигурации), связанный с ним, `/cfg \<configuration file name>` необходимо также указать параметр командной строки.|
|cfg|Обязательный.</br>Указывает путь и имя файла шаблона безопасности, который будет импортирован в базу данных для анализа.</br>Этот параметр/cfg допустим только при использовании с `/db \<database file name>` параметра. Если этот параметр не указан, анализ выполняется по конфигурации, уже хранится в базе данных.|
|rbk|Обязательный.</br>Определяет шаблон безопасности, в который записываются данные отката. Шаблоны безопасности создаются с помощью оснастки Шаблоны параметров безопасности. Файлы отката, могут быть созданы с помощью следующей команды.|
|журнал|Необязательно.</br>Указывает путь и имя файла журнала для процесса.|
|Скрытый|Необязательно.</br>Подавляет вывод на экран и журнала. Вы можете по-прежнему просматривать результаты анализа с помощью анализа и настройки безопасности – – оснастка консоли управления Майкрософт (MMC).|

## <a name="remarks"></a>Примечания

Если путь к файлу журнала не указан, файл журнала по умолчанию (*systemroot*\Users \*UserAccount *\My Documents\Security\Logs\*DatabaseName*.log) используется.

Начиная с Windows Server 2008, `Secedit /refreshpolicy` был заменен `gpupdate`. Сведения о том, как обновить параметры безопасности, см. в разделе [Gpupdate](gpupdate.md).

Успешное выполнение этой команды будет указано «задание выполнено успешно». журналы и только несоответствия между шаблоном заявленным безопасности и конфигурации политики безопасности. В ней перечислены эти несоответствия в шаблоны безопасности создаются.

Если указан существующий шаблон отката, эта команда перезапишет его. С помощью следующей команды можно создать новый шаблон отката. Дополнительные параметры, необходимо хотя бы одно условие.

## <a name="BKMK_Examples"></a>Примеры

После создания шаблона безопасности, с помощью конфигурации безопасности и анализа оснастку, SecTmplContoso.inf, создайте файл конфигурации отката, чтобы сохранить исходные параметры. Запись в файл журнала FY11 действие.
```
Secedit /generaterollback /db C:\Security\FY11\SecDbContoso.sdb /cfg sectmplcontoso.inf /rbk sectmplcontosoRBK.inf /log C:\Security\FY11\SecAnalysisContosoFY11.log
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Secedit](secedit.md)
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)