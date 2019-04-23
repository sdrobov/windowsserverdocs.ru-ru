---
title: KeyPackage готов
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c631ef10-2a2f-4541-8578-292f2d4e9e80
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8fb49ce8fbe4be076151b203560e62f44a78c9d4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886905"
---
# <a name="manage-bde-keypackage"></a>готов: KeyPackage



Создает пакет ключей для диска. Пакет ключей может использоваться вместе со средством восстановления для восстановления поврежденных дисков. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -KeyPackage [<Drive>] [-ID <KeyProtectoryID>] [-path <PathToExternalKeyDirectory>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<Диск >|Представляет букву диска, за которым следует двоеточие.|
|-ID|Создание ключа пакета с помощью предохранителя ключа с идентификатором, указанным это значение идентификатора.|
|-path|Расположение, в котором следует сохранить созданный пакет ключей.|
|-computername|Указывает, что Manage-bde.exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать **- cn** как сокращенную версию этой команды.|
|\<Имя >|Представляет имя компьютера, на которой требуется изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или /?|Отображение кратких справки в командной строке.|
|-help или -h|Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеры

В следующем примере демонстрируется использование **- KeyPackage** команду, чтобы создать пакет ключей для диска C, на основе предохранителя ключа с идентификатором GUID, так и для сохранения пакета ключа F:\Folder.
```
manage-bde -KeyPackage C: -id {84E151C1...7A62067A512} -path "f:\Folder"
```

> [!TIP]
> Используйте **готов — предохранители — получить** вместе с букву диска, который вы хотите создать пакет для ключа для получения списка доступных идентификаторов GUID для использования в качестве значения идентификатора.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Готов](manage-bde.md)