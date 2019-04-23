---
title: bitsadmin setclientcertificatebyname
description: Раздел Windows команды для **bitsadmin setclientcertificatebyname** — задает имя субъекта сертификата клиента для проверки подлинности клиента в запросе HTTPS (SSL).
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f308a6d9-d0da-48be-ae41-eced14b3cccb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 76150ccb34693eb692d27efbd6538f5363ba1c26
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59871315"
---
# <a name="bitsadmin-setclientcertificatebyname"></a>bitsadmin setclientcertificatebyname



Задает имя субъекта сертификата клиента для проверки подлинности клиента в запросе HTTPS (SSL).

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetClientCertificateByID <Job> <store_location> <store_name> <subject_name>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя или идентификатор GUID задания|
|Store_location|Указывает расположение системного хранилища, используемый для поиска сертификата. Возможные значения:</br>1 (ФУНКЦИЯ CURRENT_USER)</br>2 (LOCAL_MACHINE)</br>3 (CURRENT_SERVICE)</br>4 (СЛУЖБЫ)</br>5 (ПОЛЬЗОВАТЕЛИ)</br>6 (CURRENT_USER_GROUP_POLICY)</br>7 (LOCAL_MACHINE_GROUP_POLICY)</br>8 (LOCAL_MACHINE_ENTERPRISE)|
|Store_name|Имя хранилища сертификатов. Возможные значения:</br>ЦС (сертификаты центра сертификации)</br>(Личные сертификаты)</br>КОРНЕВОЙ (корневые сертификаты)</br>SPC (сертификат издателя программного обеспечения)|
|Subject_name|Имя сертификата|

## <a name="BKMK_examples"></a>Примеры

Следующий пример задает имя используемого сертификата клиента *Мойсертификат* для проверки подлинности клиента в запросе HTTPS (SSL) для задания с именем *myJob*.
```
C:\>bitsadmin Bitsadmin /SetClientCertificateByName myJob 1 MY myCertificate 
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)