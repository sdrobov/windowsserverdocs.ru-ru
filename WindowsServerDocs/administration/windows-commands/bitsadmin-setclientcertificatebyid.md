---
title: bitsadmin setclientcertificatebyid
description: Раздел Windows команды для **bitsadmin setclientcertificatebyid** указывает идентификатор сертификата клиента для проверки подлинности клиента в запросе HTTPS (SSL)
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8585a7a1-7472-437b-b04a-a11925782a3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2424de18ee8aaec73b086207e8ef56d85df862fa
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863935"
---
# <a name="bitsadmin-setclientcertificatebyid"></a>bitsadmin setclientcertificatebyid



Указывает идентификатор сертификата клиента для проверки подлинности клиента в запросе HTTPS (SSL).

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetClientCertificateByID <Job> <store_location> <store_name> hexa-decimal_cert_id>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Store_location|Указывает расположение системного хранилища, используемый для поиска сертификата. Возможные значения:</br>1 (ФУНКЦИЯ CURRENT_USER)</br>2 (LOCAL_MACHINE)</br>3 (CURRENT_SERVICE)</br>4 (СЛУЖБЫ)</br>5 (ПОЛЬЗОВАТЕЛИ)</br>6 (CURRENT_USER_GROUP_POLICY)</br>7 (LOCAL_MACHINE_GROUP_POLICY)</br>8 (LOCAL_MACHINE_ENTERPRISE)|
|Store_name|Имя хранилища сертификатов. Возможные значения:</br>ЦС (сертификаты центра сертификации)</br>(Личные сертификаты)</br>КОРНЕВОЙ (корневые сертификаты)</br>SPC (сертификат издателя программного обеспечения)|
|Hexadecimal_cert_id|Шестнадцатеричное число, представляющее хэш сертификата|

## <a name="BKMK_examples"></a>Примеры

Следующий пример указывает идентификатор сертификата клиента для проверки подлинности клиента в запросе HTTPS (SSL) для задания с именем *myJob*.
```
C:\>bitsadmin Bitsadmin /SetClientCertificateByID myJob BG_CERT_STORE_LOCATION_CURRENT_USER MY A106B52356D3FBCD1853A41B619358BD 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)