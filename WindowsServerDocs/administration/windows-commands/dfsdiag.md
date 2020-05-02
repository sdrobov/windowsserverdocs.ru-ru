---
title: дфсдиаг
description: Справочный раздел по дфсдиаг, который предоставляет диагностические сведения для пространств имен DFS.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c0891e67-0187-4f18-923d-5623e6127f90
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2d5a9b147994628ccad6a723311decbccbe82ec6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719542"
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
|/?|Отображение справки в командной строке.|

## <a name="additional-references"></a>Дополнительные ссылки

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)