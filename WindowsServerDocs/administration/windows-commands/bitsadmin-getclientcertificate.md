---
title: bitsadmin getclientcertificate
description: Справочная статья по команде битсадмин жетклиентцертификате, которая получает сертификат клиента из задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4fc8f408-085e-43a0-9fa8-3d798ef107b1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5113214f106aea21b1b13f08cc08002237730daf
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928519"
---
# <a name="bitsadmin-getclientcertificate"></a>bitsadmin getclientcertificate

Получает сертификат клиента из задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getclientcertificate <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a>Примеры

Чтобы получить сертификат клиента для задания с именем *мидовнлоаджоб*, выполните следующие действия.

```
bitsadmin /getclientcertificate myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
