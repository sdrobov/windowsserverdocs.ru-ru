---
title: bitsadmin getproxyusage
description: Справочный раздел по команде битсадмин жетпроксюсаже, который получает параметр использования прокси-сервера для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f940a70e-3b02-497e-a47f-b37b905c299e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 13a3f216b1ed3c77dbbefee37d73a657525daa36
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717651"
---
# <a name="bitsadmin-getproxyusage"></a>bitsadmin getproxyusage

Извлекает параметр использования прокси-сервера для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getproxyusage <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задание | Отображаемое имя задания или идентификатор GUID. |

#### <a name="output"></a>Вывод

Возвращаемые значения использования прокси-сервера могут быть:

- Предварительная **Настройка** — используйте значения по умолчанию для свойства Owner в Internet Explorer.

- **No_Proxy** — не использовать прокси-сервер.

- **Reoverride** — Используйте явный список прокси-серверов.

- **Автообнаружение** — автоматическое определение параметров прокси-сервера.

## <a name="examples"></a>Примеры

Чтобы получить сведения об использовании прокси-сервера для задания с именем *мидовнлоаджоб*:

```
bitsadmin /getproxyusage myDownloadJob
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
