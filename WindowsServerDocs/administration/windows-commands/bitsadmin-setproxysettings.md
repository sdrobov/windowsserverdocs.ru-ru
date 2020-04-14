---
title: bitsadmin setproxysettings
description: Раздел команд Windows для **битсадмин setproxysettings**, который задает параметры прокси-сервера для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: be8edb1b-614e-4d0b-a8f8-64b4bde3e64b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0ea92383d9bd09372d21d3c1da84db060b0a9958
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122755"
---
# <a name="bitsadmin-setproxysettings"></a>bitsadmin setproxysettings

Задает параметры прокси-сервера для указанного задания.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /setproxysettings <job> <usage> [list] [bypass]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |
| usage | Задает использование прокси-сервера, в том числе:<ul><li>**PRECONFIG.** Используйте параметры по умолчанию для владельца Internet Explorer.</li><li>**NO_PROXY.** Не используйте прокси-сервер.</li><li>**Крывают.** Используйте явный список прокси-серверов и список обхода. Должны следовать список прокси-сервера и сведения для обхода прокси-сервера.</li><li>**Автообнаружение.** Автоматически определяет параметры прокси-сервера.</li></ul> |
| list | Используется, если параметру *использования* задано значение override. Должен содержать разделенный запятыми список прокси-серверов для использования. |
| Пустите | Используется, если параметру *использования* задано значение override. Должен содержать разделенный пробелами список имен узлов или IP-адресов, для которых передачи не направляются через прокси-сервер. Это может быть `<local>` для ссылки на все серверы в одной локальной сети. Значения NULL могут использоваться для пустого списка обхода прокси-сервера. |

## <a name="examples"></a>Примеры

В следующем примере задаются параметры прокси-сервера для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /setproxysettings myDownloadJob PRECONFIG
```

```
bitsadmin /setproxysettings myDownloadJob NO_PROXY
```
```
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1:80
```

```
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1,proxy2,proxy3 NULL
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)