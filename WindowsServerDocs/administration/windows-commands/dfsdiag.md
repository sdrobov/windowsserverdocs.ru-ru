---
title: дфсдиаг
description: Раздел команд Windows для дфсдиаг, который предоставляет диагностические сведения для пространств имен DFS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c0891e67-0187-4f18-923d-5623e6127f90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2c895dabbbafbe8ea253920d3bc6de17f42918e6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846197"
---
# <a name="dfsdiag"></a>дфсдиаг

Предоставляет диагностические сведения для пространств имен DFS.

## <a name="syntax"></a>Синтаксис

```
dfsdiag [ /TestDCs [/Domain:<Domain name>]| /TestSites </Machine:<server name>| /DFSPath:<namespace root or DFS folder> [/Recurse]> [/Full] | /TestDFSConfig /DFSRoot:<namespace> | /TestDFSIntegrity /DFSRoot:<DFS root path> [/Recurse] [/Full] | /TestReferral /DFSPath:<DFS path for getting referrals> [/Full] | /?] 

```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[Дфсдиаг Тестдкс](dfsdiag-testdcs.md)|Проверяет конфигурацию контроллера домена.|
|[Дфсдиаг Тестситес](dfsdiag-testsites.md)|Проверяет связи сайтов.|
|[Дфсдиаг Тестдфсконфиг](dfsdiag-testdfsconfig.md)|Проверяет конфигурацию пространства имен DFS.|
|[Дфсдиаг Тестдфсинтегрити](dfsdiag-testdfsintegrity.md)|Проверяет целостность пространства имен DFS.|
|[Дфсдиаг Тестреферрал](dfsdiag-testreferral.md)|Проверяет ответы на ссылки.|
|/?|Отображает справку в командной строке.|

## <a name="additional-references"></a>Дополнительные материалы

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)