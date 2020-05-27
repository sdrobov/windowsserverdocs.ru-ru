---
title: 'Secedit: Проверка'
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9fb06354-f55a-4ca4-9fbc-9a872eb9b9cf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b93ad6ceadb08f6df8390edc3fc454d951519aad
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83821104"
---
# <a name="seceditvalidate"></a>Secedit: Проверка



Проверяет параметры безопасности, хранящиеся в шаблоне безопасности (INF-файле).

## <a name="syntax"></a>Синтаксис

```
Secedit /validate <configuration file name>

```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Имя файла конфигурации|Обязательный элемент.</br>Указывает путь и имя файла для шаблона безопасности, который будет проверен.|

## <a name="remarks"></a>Замечания

Проверка шаблонов безопасности может помочь в том, что один из них поврежден или настроен неправильно.

Недопустимый шаблон безопасности не будет применен.

Файл журнала не будет обновлен.

В Windows Server 2008 был `Secedit /refreshpolicy` заменен на `gpupdate` . Сведения о том, как обновить параметры безопасности, см. в разделе [gpupdate](gpupdate.md).

## <a name="examples"></a>Примеры

После выполнения отката в шаблоне безопасности необходимо убедиться, что INF-файл отката Секрбкконтосо. inf является допустимым.
```
Secedit /validate secRBKcontoso.inf
```

## <a name="additional-references"></a>Дополнительные ссылки

-   [Secedit:generaterollback](secedit-generaterollback.md)
-   [Программу Secedit](secedit.md)
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)