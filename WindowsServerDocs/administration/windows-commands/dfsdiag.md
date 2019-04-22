---
title: dfsdiag
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: ab5c86ce7ed4760aef4941de55e8dcf8efe48c8f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59819145"
---
# <a name="dfsdiag"></a>dfsdiag



`Dfsdiag` Команда предоставляет диагностические сведения для пространств имен DFS.

## <a name="syntax"></a>Синтаксис

```
dfsdiag [ /TestDCs [/Domain:<Domain name>]| /TestSites </Machine:<server name>| /DFSPath:<namespace root or DFS folder> [/Recurse]> [/Full] | /TestDFSConfig /DFSRoot:<namespace> | /TestDFSIntegrity /DFSRoot:<DFS root path> [/Recurse] [/Full] | /TestReferral /DFSPath:<DFS path for getting referrals> [/Full] | /?] 

```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[Dfsdiag TestDCs](dfsdiag-testdcs.md)|Проверяет, что настройка контроллера домена.|
|[Dfsdiag TestSites](dfsdiag-testsites.md)|Проверка сайта ассоциации.|
|[dfsdiag TestDFSConfig](dfsdiag-testdfsconfig.md)|Проверяет конфигурацию пространства имен DFS.|
|[dfsdiag TestDFSIntegrity](dfsdiag-testdfsintegrity.md)|Проверяет целостность пространства имен DFS.|
|[Dfsdiag TestReferral](dfsdiag-testreferral.md)|Проверяет ответы ссылок.|
|/?|Отображение справки в командной строке.|

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)