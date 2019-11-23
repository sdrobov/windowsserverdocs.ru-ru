---
title: Управление — BDE Кэйпаккаже
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: a0a1b4fd0fff1153a0f778eca105ecfc618a4689
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374054"
---
# <a name="manage-bde-keypackage"></a>Manage-bde: Кэйпаккаже



Создает пакет ключей для диска. Пакет ключей можно использовать вместе с средством восстановления для восстановления поврежденных дисков. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -KeyPackage [<Drive>] [-ID <KeyProtectoryID>] [-path <PathToExternalKeyDirectory>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|> \<диска|Представляет букву диска, за которой следует двоеточие.|
|— Идентификатор|Создайте пакет ключей с помощью предохранителя ключа с идентификатором, указанным в этом значении идентификатора.|
|-path|Расположение, в котором нужно сохранить созданный пакет ключей.|
|-ComputerName|Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды.|
|Имя \<>|Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или/?|Отображает краткую справку в командной строке.|
|-Help или-h|Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеров

В следующем примере показано использование команды **-кэйпаккаже** для создания ключевого пакета для диска C на основе предохранителя ключа, ОПРЕДЕЛЯЕМого идентификатором GUID, и сохранения пакета ключей в ф:\фолдер.
```
manage-bde -KeyPackage C: -id {84E151C1...7A62067A512} -path "f:\Folder"
```

> [!TIP]
> Используйте **Manage-bde-protectors** . для получения списка доступных идентификаторов GUID, используемых в качестве значения идентификатора, получите имя диска, для которого нужно создать пакет ключей.

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Управление — BDE](manage-bde.md)