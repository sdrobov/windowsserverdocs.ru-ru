---
title: Нацеливание на другую версию пакета SDK для Windows Admin Center
description: Назначение другой версии пакета SDK для Windows Admin Center (проект Хонолулу)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 0d3b7af5229f7b8487aa9f04eaf0d1756d8c02f4
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71356970"
---
# <a name="target-a-different-version-of-the-windows-admin-center-sdk"></a>Нацеливание на другую версию пакета SDK для Windows Admin Center

>Область применения. Windows Admin Center, ознакомительная версия Windows Admin Center

Обновление расширения с помощью изменений пакета SDK и изменение платформы — это просто.  Мы используем [теги NPM](https://www.npmjs.com/package/@microsoft/windows-admin-center-sdk) для организации выпуска новых функций в версии пакета SDK.

Вы можете выбрать три версии пакета SDK:

* ```latest``` — этот пакет SDK соответствует текущему общедоступному выпуску центра администрирования Windows
* ```insider``` — этот пакет SDK соответствует текущему предварительному выпуску центра администрирования Windows (доступен в предварительной версии Windows Server Insider Preview).
* ```next``` — этот пакет SDK содержит самые последние функции

> [!NOTE]
> Узнайте больше о различных [версиях](https://aka.ms/WACDownloadPage) центра администрирования Windows, доступных для загрузки.

## <a name="targeting-sdk-version-on-a-new-project"></a>Целевая версия пакета SDK для нового проекта

При создании нового расширения можно включить параметр ```--version```, чтобы выбрать другую версию пакета SDK:

```
wac create --company "{!Company Name}" --tool "{!Tool Name}" --version {!version}
```

| Значение | Объяснение | Пример |
| ----- | ----------- | ------- |
| ```{!Company Name}``` | Название вашей компании (с пробелами) | ```Contoso Inc``` |
| ```{!Tool Name}``` | Имя средства (с пробелами) | ```Manage Foo Works``` |
| ```{!version}``` | Версия пакета SDK | ```latest``` |

Ниже приведен пример создания нового расширения, предназначенного для ```insider```:

```
wac create --company "Contoso Inc" --tool "Manage Foo Works" --version insider
```

## <a name="targeting-sdk-version-on-an-existing-project"></a>Целевая версия пакета SDK для существующего проекта

Чтобы изменить существующий проект для другой версии пакета SDK, измените следующую строку в ```package.json```:

```
"@microsoft/windows-admin-center-sdk": "latest",
```
В этом примере замените ```latest``` на нужную версию пакета SDK, т. е. ```insider```:

```
"@microsoft/windows-admin-center-sdk": "insider",
```

Затем выполните ```npm install```, чтобы обновить ссылки в рамках проекта.