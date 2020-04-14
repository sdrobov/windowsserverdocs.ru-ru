---
title: битсадмин сетклиентцертификатебид
description: Раздел команд Windows для **битсадмин сетклиентцертификатебид**, который указывает идентификатор сертификата клиента, используемого для проверки подлинности клиента в запросе HTTPS (SSL)
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8585a7a1-7472-437b-b04a-a11925782a3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 376bb850664a5ed569488634029cb7384856f158
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123045"
---
# <a name="bitsadmin-setclientcertificatebyid"></a>битсадмин сетклиентцертификатебид

Указывает идентификатор сертификата клиента, который будет использоваться для проверки подлинности клиента в запросе HTTPS (SSL).

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setclientcertificatebyid <job> <store_location> <store_name> <hexadecimal_cert_id>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| store_location | Определяет расположение системного хранилища, используемого для поиска сертификата, в том числе:<ul><li>CURRENT_USER</li><li>LOCAL_MACHINE</li><li>CURRENT_SERVICE</li><li>Обслуживание</li><li>ПОЛЬЗОВАТЕЛИ</li><li>CURRENT_USER_GROUP_POLICY</li><li>LOCAL_MACHINE_GROUP_POLICY</li><li>LOCAL_MACHINE_ENTERPRISE.</li></ul> |
| store_name | Имя хранилища сертификатов, включая:<ul><li>ЦЕНТР сертификации (сертификаты центра сертификации)</li><li>MY (личные сертификаты)</li><li>Корневой каталог (корневые сертификаты)</li><li>SPC (сертификат издателя программного обеспечения).</li></ul> |
| hexadecimal_cert_id | Шестнадцатеричное число, представляющее хэш сертификата. |

## <a name="examples"></a>Примеры

В следующем примере указывается идентификатор сертификата клиента, который будет использоваться для проверки подлинности клиента в запросе HTTPS (SSL) для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /setclientcertificatebyid myDownloadJob BG_CERT_STORE_LOCATION_CURRENT_USER MY A106B52356D3FBCD1853A41B619358BD
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)