---
title: 'Secedit: анализ'
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3430cf9d-1411-48b1-b5a9-2e47701dc87f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 324da8de153a5487c9d71872cd154928cc24c285
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59848825"
---
# <a name="seceditanalyze"></a>Secedit: анализ



Позволяет анализировать текущие параметры системы, от базовых показателей конфигурации, которые хранятся в базе данных. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
Secedit /analyze /db <database file name> [/cfg <configuration file name>] [/overwrite] [/log <log file name>] [/quiet}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|DB|Обязательный.</br>Указывает путь и имя базы данных, которая содержит хранимую конфигурацию, по которой будет выполняться анализ.</br>Если имя файла содержит имя базы данных, для которой не безопасности шаблон (как определено в файле конфигурации), связанный с ним, `/cfg \<configuration file name>` необходимо также указать параметр командной строки.|
|cfg|Необязательный.</br>Указывает путь и имя файла шаблона безопасности, который будет импортирован в базу данных для анализа.</br>Этот параметр/cfg допустим только при использовании с `/db \<database file name>` параметра. Если этот параметр не указан, анализ выполняется по конфигурации, уже хранится в базе данных.|
|перезапись|Необязательно.</br>Указывает, должен ли шаблон безопасности, в параметре/cfg перезаписывать любой шаблон или составной шаблон, который хранится в базе данных вместо шаблон.</br>Этот параметр допустим только тогда, когда `/cfg \<configuration file name>` также используется параметр. Если этот параметр не указан, шаблон в параметре/cfg добавляется шаблон.|
|журнал|Необязательный.</br>Указывает путь и имя файла журнала для использования в процессе.|
|Скрытый|Необязательно.</br>Подавляет вывод на экран. Вы можете по-прежнему просматривать результаты анализа с помощью анализа и настройки безопасности – – оснастка консоли управления Майкрософт (MMC).|

## <a name="remarks"></a>Примечания

Результаты анализа, хранятся в отдельной области базы данных и можно просмотреть в конфигурации безопасности и анализа оснастки консоли MMC.

Если путь к файлу журнала не указан, файл журнала по умолчанию (*systemroot*\Documents and Settings\*UserAccount*\My Documents\Security\Logs\*DatabaseName*. повторно используется журнал).

В Windows Server 2008 `Secedit /refreshpolicy` был заменен `gpupdate`. Сведения о том, как обновить параметры безопасности, см. в разделе [Gpupdate](gpupdate.md).

## <a name="BKMK_Examples"></a>Примеры

Выполнения анализа для параметров безопасности в базе данных безопасности, SecDbContoso.sdb, созданные с помощью оснастки анализа и конфигурации безопасности. Направления выходных данных к файлу, который SecAnalysisContosoFY11 с запросом, поэтому проверку можно выполнить команду выполнено правильно.
```
Secedit /analyze /db C:\Security\FY11\SecDbContoso.sdb /log C:\Security\FY11\SecAnalysisContosoFY11.log
```
Предположим, что анализ показал некоторые inadequacies, поэтому шаблона безопасности, SecContoso.inf, был изменен. Выполните команду еще раз, чтобы внести изменения, запись в выходных данных в существующий файл SecAnalysisContosoFY11 без запроса.
```
Secedit /analyze /db C:\Security\FY11\SecDbContoso.sdb /cfg SecContoso.inf /overwrite /log C:\Security\FY11\SecAnalysisContosoFY11.xml /quiet
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Secedit](secedit.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)