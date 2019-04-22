---
title: Secedit:Export
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49a8b241-aa8c-45b7-844d-67a29fab708e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f9d6268777d0791dbc0cdca2d4318399378698b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813495"
---
# <a name="seceditexport"></a>Secedit:Export



Экспортирует параметры безопасности, хранящиеся в базе данных, настроенной с помощью шаблонов безопасности. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
Secedit /export /db <database file name> [/mergedpolicy] /cfg <configuration file name> [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]

```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|DB|Обязательный.</br>Указывает путь и имя базы данных, которая содержит хранимую конфигурацию, по которой будет выполняться анализ.</br>Если имя файла содержит имя базы данных, для которой не безопасности шаблон (как определено в файле конфигурации), связанный с ним, `/cfg \<configuration file name>` необходимо также указать параметр командной строки.|
|mergedpolicy|Необязательно.</br>Объединяет и экспортирует параметры локальной политики безопасности домена и.|
|cfg|Обязательный.</br>Указывает путь и имя файла шаблона безопасности, который будет импортирован в базу данных для анализа.</br>Этот параметр/cfg допустим только при использовании с `/db \<database file name>` параметра. Если этот параметр не указан, анализ выполняется по конфигурации, уже хранится в базе данных.|
|Области|Необязательно.</br>Определяет области безопасности, применяемые к системе. Если этот параметр не указан, все параметры безопасности, определенные в базе данных применяются к системе. Чтобы настроить несколько областей, разделите каждой области следует пробел. Поддерживаются следующие области безопасности:</br>-SecurityPolicy</br>    Локальная политика и политика домена для системы, включая политики учетных записей аудита политики, параметры безопасности и т. д.</br>-Group_Mgmt</br>    Настройка ограничений для всех групп, указанных в шаблоне безопасности.</br>-User_Rights</br>    Права пользователя на вход и предоставление привилегий.</br>-Помощью</br>    Обеспечение безопасности на локального реестра.</br>-Хранилище файлов</br>    Безопасность хранения локальных файлов.</br>-Services</br>    Безопасность для всех определенных служб.|
|журнал|Необязательно.</br>Указывает путь и имя файла журнала для процесса.|
|Скрытый|Необязательный.</br>Подавляет вывод на экран и журнала. Вы можете по-прежнему просматривать результаты анализа с помощью анализа и настройки безопасности – – оснастка консоли управления Майкрософт (MMC).|

## <a name="remarks"></a>Примечания

Эта команда используется для резервного копирования ваши политики безопасности на локальном компьютере в дополнение к импорта параметров на другой компьютер.

Если путь к файлу журнала не указан, файл журнала по умолчанию (*systemroot*\Documents and Settings\*UserAccount*\My Documents\Security\Logs\*DatabaseName*. повторно используется журнал).

В Windows Server 2008 `Secedit /refreshpolicy` был заменен `gpupdate`. Сведения о том, как обновить параметры безопасности, см. в разделе [Gpupdate](gpupdate.md).

## <a name="BKMK_Examples"></a>Примеры

Экспорт базы данных безопасности и политики безопасности домена в inf-файл и импортировать этот файл в другую базу данных на реплицируемой параметры политики безопасности на другом компьютере.
```
Secedit /export /db C:\Security\FY11\SecDbContoso.sdb /mergedpolicy /cfg SecContoso.inf /log C:\Security\FY11\SecAnalysisContosoFY11.log /quiet
```
Импортируйте его в другую базу данных на другом компьютере.
```
Secedit /import /db C:\Security\FY12\SecDbContoso.sdb /cfg SecContoso.inf /log C:\Security\FY11\SecAnalysisContosoFY12.log /quiet
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Secedit:import](secedit-import.md)
-   [Secedit](secedit.md)
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)