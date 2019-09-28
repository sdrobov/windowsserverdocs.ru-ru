---
title: Управление-BDE Unlock
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 92ed2e00babfad890be83e45827ae8e0080cac40
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373867"
---
# <a name="manage-bde-unlock"></a>Управление — BDE: Unlock



Разблокирует диск, защищенный BitLocker, с помощью пароля восстановления или ключа восстановления. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -unlock {-recoverypassword <Password>|-recoverykey <PathToExternalKeyFile>} <Drive> [-certificate {-cf PathToCertificateFile | -ct CertificateThumbprint} {-pin}] [-password] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Значение|Описание|
|---------|-----|-----------|
|-рековерипассворд||Указывает, что для разблокировки диска будет использоваться пароль восстановления. Аббревиатура:-RP|
||@no__t 0Password >|Представляет пароль восстановления, который можно использовать для разблокировки диска.|
|-рековерикэй||Указывает, что для разблокировки диска будет использоваться внешний файл ключа восстановления. Сокращение:-ать|
||@no__t 0PathToExternalKeyFile >|Представляет файл внешнего ключа восстановления, который можно использовать для разблокировки диска.|
||@no__t 0Drive >|Представляет букву диска, за которой следует двоеточие.|
|— сертификат||Сертификат локального пользователя для сертификата BitLocker для нечасового тома находится в хранилище сертификатов пользователя ве. Сокращение:-CERT|
||<-CF Пастоцертификатефиле >|Путь к файлу церфикате|
||<-CT CertificateThumbprint >|Отпечаток сертификата, который при необходимости может содержать ПИН-код (-PIN).|
|— пароль||Представляет запрос на ввод пароля для разблокировки тома. Сокращение:-пароль|
|-ComputerName||Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Сокращение:-CN|
||\<Имя >|Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или/?||Отображает краткую справку в командной строке.|
|-Help или-h||Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеров

В следующем примере показано использование команды **-Unlock** для разблокировки диска E с помощью файла ключа восстановления, сохраненного в папке резервного копирования на другом диске.
```
manage-bde –unlock E: -recoverykey "F:\Backupkeys\recoverykey.bek"
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Управление — BDE](manage-bde.md)