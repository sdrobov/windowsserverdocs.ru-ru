---
title: разблокировать готов
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7852bf7d-9102-40be-adcb-71e8f4dfde72
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a86267890449be2048221940e5955e49f30f99f3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814605"
---
# <a name="manage-bde-unlock"></a>готов: разблокировки



Разблокирует диск, защищенный BitLocker с помощью пароля восстановления или ключа восстановления. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -unlock {-recoverypassword <Password>|-recoverykey <PathToExternalKeyFile>} <Drive> [-certificate {-cf PathToCertificateFile | -ct CertificateThumbprint} {-pin}] [-password] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Значение|Описание|
|---------|-----|-----------|
|-recoverypassword||Указывает, что пароль восстановления будет использоваться для разблокировки диска. Сокращенная форма: - rp|
||\<Пароль >|Представляет пароль восстановления, который можно использовать для разблокировки диска.|
|-recoverykey||Указывает, что файл ключа внешних восстановления будет использоваться для разблокировки диска. Сокращенная форма: - ринтерах|
||\<PathToExternalKeyFile >|Представляет файл ключа внешних восстановления, который может использоваться для разблокировки диска.|
||\<Диск >|Представляет букву диска, за которым следует двоеточие.|
|-сертификата||Сертификат локального пользователя для сертификата BitLocker, unclock том находится в хранилище сертификатов пользователя дении журнала. Сокращенная форма:-cert|
||<-cf PathToCertificateFile >|Путь к файлу cerficate|
||<-ct CertificateThumbprint >|Отпечаток сертификата, который может включать ПИН-код (-ПИН-код).|
|-пароль||Представляет запрос пароля для разблокировки тома. Сокращенная форма: - pw|
|-computername||Указывает, что Manage-bde.exe будет использоваться для изменения защиты BitLocker на другом компьютере. Сокращенная форма: - cn|
||\<Имя >|Представляет имя компьютера, на которой требуется изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или /?||Отображение кратких справки в командной строке.|
|-help или -h||Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеры

В следующем примере демонстрируется использование **-разблокировать** команду, чтобы разблокировать диск E с файлом ключа восстановления, который был сохранен в папку резервных копий на другой диск.
```
manage-bde –unlock E: -recoverykey "F:\Backupkeys\recoverykey.bek"
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Готов](manage-bde.md)