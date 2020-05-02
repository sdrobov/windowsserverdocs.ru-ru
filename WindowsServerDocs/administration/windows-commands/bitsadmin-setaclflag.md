---
title: bitsadmin setaclflag
description: Справочный раздел по команде битсадмин сетаклфлаг, который задает флаги распространения списка управления доступом (ACL).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e3bcda0-827d-4dfd-8384-d1da018f3e10
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1852bd267fe22825d55f7522a81179e9290e2a00
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716989"
---
# <a name="bitsadmin-setaclflag"></a>bitsadmin setaclflag

Задает флаги распространения списка управления доступом (ACL) для задания. Флаги указывают, что вы хотите сохранить сведения о владельце и списке ACL с загружаемым файлом. Например, чтобы сохранить владельца и группу с файлом, установите для `og`параметра **flags** значение.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setaclflag <job> <flags>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задание | Отображаемое имя задания или идентификатор GUID. |
| flags | Укажите одно или несколько значений, включая:<ul><li>**o** — копирование сведений о владельце с помощью файла.</li><li>**g** — копирование сведений о группе с помощью файла.</li><li>**d** — копирование сведений о избирательном списке управления доступом (DACL) с помощью файла.</li><li>**s** -копирование данных системного списка управления доступом (SACL) с помощью файла.</li></ul> |

## <a name="examples"></a>Примеры

Чтобы задать флаги распространения списка управления доступом для задания с именем *мидовнлоаджоб*, необходимо сохранить сведения о владельце и группе с скачанными файлами.

```
bitsadmin /setaclflags myDownloadJob og
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
