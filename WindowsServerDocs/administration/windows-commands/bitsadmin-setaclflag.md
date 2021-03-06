---
title: bitsadmin setaclflag
description: Справочная статья по команде битсадмин сетаклфлаг, которая устанавливает флаги распространения списка управления доступом (ACL).
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e3bcda0-827d-4dfd-8384-d1da018f3e10
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dcf07f944813c0c8d7a4ff4c4f52c598c0f3bf47
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927953"
---
# <a name="bitsadmin-setaclflag"></a>bitsadmin setaclflag

Задает флаги распространения списка управления доступом (ACL) для задания. Флаги указывают, что вы хотите сохранить сведения о владельце и списке ACL с загружаемым файлом. Например, чтобы сохранить владельца и группу с файлом, установите для параметра **flags** значение `og` .

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
