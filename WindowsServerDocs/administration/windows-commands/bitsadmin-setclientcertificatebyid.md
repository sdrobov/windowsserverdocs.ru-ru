---
title: битсадмин сетклиентцертификатебид
description: Раздел команд Windows для **битсадмин сетклиентцертификатебид** указывает идентификатор сертификата клиента, который будет использоваться для проверки подлинности клиента в запросе HTTPS (SSL).
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 53b6fa4c65397cf710d0497fbae889afd31ec136
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380726"
---
# <a name="bitsadmin-setclientcertificatebyid"></a>битсадмин сетклиентцертификатебид



Указывает идентификатор сертификата клиента, который будет использоваться для проверки подлинности клиента в запросе HTTPS (SSL).

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetClientCertificateByID <Job> <store_location> <store_name> hexa-decimal_cert_id>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Store_location|Определяет расположение системного хранилища, используемого для поиска сертификата. Возможные значения:</br>1 (CURRENT_USER)</br>2 (LOCAL_MACHINE)</br>3 (CURRENT_SERVICE)</br>4 (СЛУЖБЫ)</br>5 (ПОЛЬЗОВАТЕЛИ)</br>6 (CURRENT_USER_GROUP_POLICY)</br>7 (LOCAL_MACHINE_GROUP_POLICY)</br>8 (LOCAL_MACHINE_ENTERPRISE)|
|Store_name|Имя хранилища сертификатов. Возможные значения:</br>ЦЕНТР сертификации (сертификаты центра сертификации)</br>MY (личные сертификаты)</br>Корневой каталог (корневые сертификаты)</br>SPC (сертификат издателя программного обеспечения)|
|Hexadecimal_cert_id|Шестнадцатеричное число, представляющее хэш сертификата|

## <a name="BKMK_examples"></a>Примеров

В следующем примере указывается идентификатор сертификата клиента, который будет использоваться для проверки подлинности клиента в запросе HTTPS (SSL) для задания с именем *myJob*.
```
C:\>bitsadmin Bitsadmin /SetClientCertificateByID myJob BG_CERT_STORE_LOCATION_CURRENT_USER MY A106B52356D3FBCD1853A41B619358BD 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)