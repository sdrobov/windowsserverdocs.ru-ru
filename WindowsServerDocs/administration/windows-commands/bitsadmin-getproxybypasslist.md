---
title: bitsadmin getproxybypasslist
description: Раздел команд Windows для **битсадмин жетпроксибипасслист**, который извлекает список обхода прокси-сервера для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 50959be3-7014-4bc9-9a7b-68f1ff94a94a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9cd81aaef22c4173f198b765246b78b3d3bae136
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850537"
---
# <a name="bitsadmin-getproxybypasslist"></a>bitsadmin getproxybypasslist

Извлекает список обхода прокси-сервера для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getproxybypasslist <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="remarks"></a>Примечания

Список обхода содержит имена узлов или IP-адреса, которые не направляются через прокси-сервер. Список может содержать `<local>` для ссылки на все серверы в одной локальной сети. Список может быть точкой с запятой (;) или с разделителями-пробелами.

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается список обхода прокси-сервера для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getproxybypasslist myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)