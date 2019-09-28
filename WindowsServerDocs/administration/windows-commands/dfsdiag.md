---
title: дфсдиаг
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0891e67-0187-4f18-923d-5623e6127f90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 61a6ab9a90e4d0220cfe27d2d21120be19b9ff1f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71378307"
---
# <a name="dfsdiag"></a>дфсдиаг



Команда `Dfsdiag` предоставляет диагностические сведения для пространств имен DFS.

## <a name="syntax"></a>Синтаксис

```
dfsdiag [ /TestDCs [/Domain:<Domain name>]| /TestSites </Machine:<server name>| /DFSPath:<namespace root or DFS folder> [/Recurse]> [/Full] | /TestDFSConfig /DFSRoot:<namespace> | /TestDFSIntegrity /DFSRoot:<DFS root path> [/Recurse] [/Full] | /TestReferral /DFSPath:<DFS path for getting referrals> [/Full] | /?] 

```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[Дфсдиаг Тестдкс](dfsdiag-testdcs.md)|Проверяет конфигурацию контроллера домена.|
|[Дфсдиаг Тестситес](dfsdiag-testsites.md)|Проверяет связи сайтов.|
|[Дфсдиаг Тестдфсконфиг](dfsdiag-testdfsconfig.md)|Проверяет конфигурацию пространства имен DFS.|
|[Дфсдиаг Тестдфсинтегрити](dfsdiag-testdfsintegrity.md)|Проверяет целостность пространства имен DFS.|
|[Дфсдиаг Тестреферрал](dfsdiag-testreferral.md)|Проверяет ответы на ссылки.|
|/?|Отображение справки в командной строке.|

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)