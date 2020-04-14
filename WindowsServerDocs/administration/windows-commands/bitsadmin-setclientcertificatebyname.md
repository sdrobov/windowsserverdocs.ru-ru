---
title: битсадмин сетклиентцертификатебинаме
description: Раздел команд Windows для **битсадмин сетклиентцертификатебинаме**, который указывает имя субъекта сертификата клиента, используемого для проверки подлинности клиента в запросе HTTPS (SSL).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f308a6d9-d0da-48be-ae41-eced14b3cccb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f2308bb5331f1555965b278a64bb7ab95e03779b
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123054"
---
# <a name="bitsadmin-setclientcertificatebyname"></a>битсадмин сетклиентцертификатебинаме

Указывает имя субъекта сертификата клиента, используемого для проверки подлинности клиента в запросе HTTPS (SSL).

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setclientcertificatebyname <job> <store_location> <store_name> <subject_name>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| store_location | Определяет расположение системного хранилища, используемого для поиска сертификата. Возможные значения:<ul><li>1 (CURRENT_USER)</li><li>2 (LOCAL_MACHINE)</li><li>3 (CURRENT_SERVICE)</li><li>4 (СЛУЖБЫ)</li><li>5 (ПОЛЬЗОВАТЕЛИ)</li><li>6 (CURRENT_USER_GROUP_POLICY)</li><li>7 (LOCAL_MACHINE_GROUP_POLICY)</li><li>8 (LOCAL_MACHINE_ENTERPRISE)</li></ul> |
| store_name | Имя хранилища сертификатов. Возможные значения:<ul><li>ЦЕНТР сертификации (сертификаты центра сертификации)</li><li>MY (личные сертификаты)</li><li>Корневой каталог (корневые сертификаты)</li><li>SPC (сертификат издателя программного обеспечения)</li></ul> |
| subject_name | Имя сертификата. |

## <a name="examples"></a>Примеры

В следующем примере указывается имя сертификата клиента, *мойсертификат* для использования при проверке подлинности клиента в запросе HTTPS (SSL) для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /setclientcertificatebyname myDownloadJob 1 MY myCertificate
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)