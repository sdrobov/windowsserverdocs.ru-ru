---
title: tpmtool
description: Раздел Windows команды для tpmtool - получает сведения о доверенный платформенный модуль.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
author: ashleytqy
ms.author: ashleytqy
manager: ronaldai
ms.date: 05/07/2019
ms.openlocfilehash: d2939b693c3f9bd8d0d8c8e1fefdd5d8f892e4c9
ms.sourcegitcommit: 3582c38d87f23cc54467d63bf00c29ef07cdb7c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2019
ms.locfileid: "65517197"
---
>[!IMPORTANT]
>Некоторые сведения относятся к предварительным версиям продуктов, в которые перед коммерческим выпуском могут быть внесены существенные изменения. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

# <a name="tpmtool"></a>tpmtool

Эта программа может использоваться для получения сведений о [доверенного платформенного модуля (TPM)](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview).

В разделе [Примеры](#tpmtool_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
tpmtool /parameter [<arguments>]
```
## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|getdeviceinformation|Основные сведения, связанные с доверенного платформенного МОДУЛЯ.|
|gatherlogs [путь к выходному каталогу]|Собирает журналы доверенного платформенного МОДУЛЯ и помещает их в указанном каталоге. По умолчанию они помещаются в текущем каталоге.|
|/?|Отображение справки в командной строке.|

## <a name="tpmtool_examples"></a>Примеры

Чтобы отобразить сведения доверенного платформенного модуля, введите следующую команду:
```
tpmtool getdeviceinformation
```
Чтобы собирает журналы доверенного платформенного МОДУЛЯ и поместить их в текущем каталоге, введите:
```
tpmtool gatherlogs
```
Чтобы собирает журналы доверенного платформенного МОДУЛЯ и поместить их в `C:\Users\Public`, тип:
```
tpmtool gatherlogs C:\Users\Public
```
