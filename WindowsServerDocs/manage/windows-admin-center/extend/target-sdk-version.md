---
title: Ориентироваться на разные версии пакета SDK Windows Admin Center
description: Ориентироваться на разные версии пакета SDK Windows Admin Center (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 47ae669e517f963762ee6267594e18f3413a72ff
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59833625"
---
# <a name="target-a-different-version-of-the-windows-admin-center-sdk"></a>Ориентироваться на разные версии пакета SDK Windows Admin Center

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Своевременное обновление расширения с помощью пакета SDK и платформы изменения очень просто.  Мы используем [NPM tags](https://www.npmjs.com/package/@microsoft/windows-admin-center-sdk) упорядочивать выпуск новых функций в версии пакета SDK.

Существует три версии пакета SDK, которые можно выбрать:

* ```latest``` — Этот пакет SDK выравнивается текущего выпуска общедоступной версии Windows Admin Center
* ```insider``` — Этот пакет SDK соответствует текущей предварительной версией Windows Admin Center (доступно в Windows Server Insider Preview)
* ```next``` — Этот пакет SDK содержит самые последние функциональные возможности

> [!NOTE]
> Дополнительные сведения о различных [версии](https://aka.ms/WACDownloadPage) из Windows Admin Center, которые доступны для загрузки.

## <a name="targeting-sdk-version-on-a-new-project"></a>Предназначенный для версии пакета SDK для нового проекта

При создании нового расширения, можно включить ```--version``` параметр, чтобы ориентироваться на разные версии пакета SDK:

```
wac create --company "{!Company Name}" --tool "{!Tool Name}" --version {!version}
```

| Значение | Объяснение | Пример |
| ----- | ----------- | ------- |
| ```{!Company Name}``` | Название организации (с пробелами) | ```Contoso Inc``` |
| ```{!Tool Name}``` | Имя инструмента (с пробелами) | ```Manage Foo Works``` |
| ```{!version}``` | Версия пакета SDK | ```latest``` |

Ниже приведен пример создания нового расширения нацеливания ```insider```:

```
wac create --company "Contoso Inc" --tool "Manage Foo Works" --version insider
```

## <a name="targeting-sdk-version-on-an-existing-project"></a>Предназначенный для версии пакета SDK для существующего проекта

Чтобы изменить существующий проект, чтобы ориентироваться на разные версии пакета SDK, измените следующую строку в ```package.json```:

```
"@microsoft/windows-admin-center-sdk": "latest",
```
В этом примере замените ```latest``` с нужную версию пакета SDK, т. е. ```insider```:

```
"@microsoft/windows-admin-center-sdk": "insider",
```

Затем запустите ```npm install``` для обновления ссылок во всем проекте.