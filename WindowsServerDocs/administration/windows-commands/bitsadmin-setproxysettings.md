---
title: bitsadmin setproxysettings
description: Справочная статья по команде битсадмин setproxysettings, которая задает параметры прокси-сервера для указанного задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: be8edb1b-614e-4d0b-a8f8-64b4bde3e64b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a59bbb560b8c89134e81c02f99aaecebdb65ca89
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927589"
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
| задание | Отображаемое имя задания или идентификатор GUID. |
| usage | Задает использование прокси-сервера, в том числе:<ul><li>**PRECONFIG.** Используйте параметры по умолчанию для владельца Internet Explorer.</li><li>**NO_PROXY.** Не используйте прокси-сервер.</li><li>**Крывают.** Используйте явный список прокси-серверов и список обхода. Должны следовать список прокси-сервера и сведения для обхода прокси-сервера.</li><li>**Автообнаружение.** Автоматически определяет параметры прокси-сервера.</li></ul> |
| list | Используется, если параметру *использования* задано значение override. Должен содержать разделенный запятыми список прокси-серверов для использования. |
| Обход | Используется, если параметру *использования* задано значение override. Должен содержать разделенный пробелами список имен узлов или IP-адресов, для которых передачи не направляются через прокси-сервер. Это может быть `<local>` ссылка на все серверы в одной локальной сети. Значения NULL могут использоваться для пустого списка обхода прокси-сервера. |

## <a name="examples"></a>Примеры

Чтобы задать параметры прокси-сервера с помощью различных параметров использования для задания с именем *мидовнлоаджоб*:

```
bitsadmin /setproxysettings myDownloadJob PRECONFIG
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

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда битсадмин](bitsadmin.md)
