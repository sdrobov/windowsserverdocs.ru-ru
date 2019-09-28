---
title: Управление — автоматическое разблокирование BDE
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 063528bf-d235-4b44-887a-52a7d983e01a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e6927c964a3f35c70fc3b9467cc2d16bbd973b17
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374138"
---
# <a name="manage-bde-autounlock"></a>Manage-bde: автоматическое разблокирование



Управляет автоматическим разблокированием дисков данных, защищенных с помощью BitLocker. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde -autounlock [{-enable|-disable|-clearallkeys}] <Drive> [-computername <Name>] [{-?|/?}] [{-help|-h}]

```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|— включить|Включает автоматическое снятие блокировки для диска данных.|
|— отключить|Отключает автоматическое снятие блокировки для диска данных.|
|-клеараллкэйс|Удаляет все сохраненные внешние ключи на диске операционной системы.|
|@no__t 0Drive >|Представляет букву диска, за которой следует двоеточие.|
|-ComputerName|Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды.|
|\<Имя >|Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.|
|-? или/?|Отображает краткую справку в командной строке.|
|-Help или-h|Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеров

В следующем примере показано использование команды **-разблокировки** для включения автоматической разблокировки диска данных E.
```
manage-bde –autounlock -enable E:
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Управление — BDE](manage-bde.md)