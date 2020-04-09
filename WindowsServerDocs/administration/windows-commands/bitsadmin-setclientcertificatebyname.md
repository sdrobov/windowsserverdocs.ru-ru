---
title: битсадмин сетклиентцертификатебинаме
description: Раздел команд Windows для битсадмин сетклиентцертификатебинаме, который указывает имя субъекта сертификата клиента, используемого для проверки подлинности клиента в запросе HTTPS (SSL).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f308a6d9-d0da-48be-ae41-eced14b3cccb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 08ec6fd8c941234de36f14cd71ffa51c3b428acb
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849657"
---
# <a name="bitsadmin-setclientcertificatebyname"></a>битсадмин сетклиентцертификатебинаме

Указывает имя субъекта сертификата клиента, используемого для проверки подлинности клиента в запросе HTTPS (SSL).

## <a name="syntax"></a>Синтаксис

```
bitsadmin /SetClientCertificateByID <Job> <store_location> <store_name> <subject_name>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Job|Отображаемое имя задания или идентификатор GUID|
|Store_location|Определяет расположение системного хранилища, используемого для поиска сертификата. Возможные значения:</br>1 (CURRENT_USER)</br>2 (LOCAL_MACHINE)</br>3 (CURRENT_SERVICE)</br>4 (СЛУЖБЫ)</br>5 (ПОЛЬЗОВАТЕЛИ)</br>6 (CURRENT_USER_GROUP_POLICY)</br>7 (LOCAL_MACHINE_GROUP_POLICY)</br>8 (LOCAL_MACHINE_ENTERPRISE)|
|Store_name|Имя хранилища сертификатов. Возможные значения:</br>ЦЕНТР сертификации (сертификаты центра сертификации)</br>MY (личные сертификаты)</br>Корневой каталог (корневые сертификаты)</br>SPC (сертификат издателя программного обеспечения)|
|Subject_name|Имя сертификата|

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере указывается имя сертификата клиента, *мойсертификат* для использования при проверке подлинности клиента в запросе HTTPS (SSL) для задания с именем *myJob*.
```
C:\>bitsadmin Bitsadmin /SetClientCertificateByName myJob 1 MY myCertificate 
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)