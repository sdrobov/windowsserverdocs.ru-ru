---
title: С помощью команды get-AllServers
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe2e3c69-8f2e-457d-af55-d249ebf70f53
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 080836e406b329cf8c15f95ef6afc99973bb3e4d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59853095"
---
# <a name="using-the-get-allservers-command"></a>С помощью команды get-AllServers



Извлекает сведения обо всех серверах службы развертывания Windows.

> [!NOTE]
> Эта команда может занять продолжительное время выполнения, если имеется много серверов служб развертывания Windows в вашей среде или используется медленное подключение сети, связанные серверы.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL [Options] /Get-AllServers /Show:{Config | Images | All} [/Detailed] [/Forest:{Yes | No}]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/ Показать: {Config | Изображений | все}|Указывает, какой тип возвращаемых сведений.</br>-   **Config** возвращает сведения о конфигурации сервера.</br>-   **Образы** возвращает сведения о групп образов, образов загрузки и установки образов на сервере.</br>-   **Все** возвращает сведения о сервере конфигурации и изображения.|
|[/ Подробные]|При использовании в сочетании с **/Show:Images** или **/Show:All**, возвращает все изображений метаданные из каждого изображения. Если **/подробные** параметр не указан, по умолчанию задается для возврата имени образа, описание и имя файла.|
|[/ Леса: {Да | No}]|Указывает, следует ли возвращать сведения для всего леса или локального домена. Если значение данного параметра не указано, по умолчанию задается для возвращения серверов в локальном домене.|

## <a name="BKMK_examples"></a>Примеры

Чтобы просмотреть сведения обо всех серверах, введите следующую команду:
```
WDSUTIL /Get-AllServers /Show:Config
```
Чтобы просмотреть подробные сведения обо всех серверах, введите:
```
WDSUTIL /Verbose /Get-AllServers /Show:All /Detailed /Forest:Yes
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)