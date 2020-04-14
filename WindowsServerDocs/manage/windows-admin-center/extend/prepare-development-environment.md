---
title: Подготовка среды разработки
description: Подготовка среды разработки пакета SDK для Windows Admin Center (Project Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.date: 09/18/2018
ms.prod: windows-server
ms.openlocfilehash: 136107210d2a8a4b336c9e4eb809e2ca096bfba2
ms.sourcegitcommit: 20d07170c7f3094c2fb4455f54b13ec4b102f2d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2020
ms.locfileid: "81269221"
---
# <a name="prepare-your-development-environment"></a>Подготовка среды разработки

>Относится к Windows Admin Center, ознакомительной версии Windows Admin Center

Давайте приступим к разработке расширений с помощью пакета SDK для Windows Admin Center!  В этом документе мы расскажем о процессе подготовки и запуска среды для создания и тестирования расширения для центра администрирования Windows.

> [!NOTE]
> Не пользовались ранее пакетом SDK для Windows Admin Center?  Дополнительные сведения о [расширениях для Windows Admin Center](extensibility-overview.md)

Чтобы подготовить среду разработки, выполните следующие действия:

## <a name="install-prerequisites"></a>Установка необходимых компонентов

Чтобы приступить к разработке с помощью пакета SDK, скачайте и установите следующие компоненты:

* [Центр администрирования Windows](https://aka.ms/WACDownloadPage) (общедоступная или предварительная версия)
* Visual Studio или [Visual Studio Code](https://code.visualstudio.com)
* [Node. js](https://nodejs.org/en/download/releases/) (версия 10.3.0)
* [Диспетчер пакетов node](https://npmjs.com/get-npm) (8.12.0 или более поздней версии)
* [NuGet](https://www.nuget.org/downloads) (для публикации расширений)

> [!NOTE]
> Чтобы выполнить действия, описанные ниже, необходимо установить и запустить Windows Admin Center в режиме разработки. Режим разработки позволяет Windows Admin Center загружать неподписанные пакеты расширений. Центр администрирования Windows можно установить только в режиме разработки на компьютере с Windows 10. 
>
>  Чтобы включить режим разработки, установите Windows Admin Center из командной строки, используя параметр DEV_MODE=1. В приведенном ниже примере замените ```<version>``` на версию, которую вы устанавливаете, то есть ```WindowsAdminCenter1809.msi```.
>
> ```msiexec /i WindowsAdminCenter<version>.msi DEV_MODE=1```

## <a name="install-global-dependencies"></a>Установка глобальных зависимостей

Затем установите или обновите зависимости, необходимые для проектов, с помощью диспетчера пакетов узлов. Эти зависимости установятся глобально и будут доступны для всех проектов.

```
npm install -g npm

npm install -g @angular/cli@7.1.2

npm install -g gulp
npm install -g typescript
npm install -g tslint
npm install -g windows-admin-center-cli
```

>[!NOTE]
>Вы можете установить более позднюю версию @angular/cli, но имейте в виду, что при установке версии выше 7.1.2 вы получите предупреждение на этапе сборки gulp о том, что локальная версия CLI не соответствует установленной версии.

## <a name="next-steps"></a>Следующие шаги

Теперь, когда ваша среда подготовлена, можно приступать к созданию содержимого.

- Создание расширения [Средство](develop-tool.md)
- Создание расширения [Решение](develop-solution.md)
- Создание [подключаемого модуля шлюза](develop-gateway-plugin.md)
- Ознакомьтесь с нашими [руководствами](guides.md)

## <a name="sdk-design-toolkit"></a>Набор средств разработки SDK

Ознакомьтесь с нашим [набором средств разработки пакета SDK](https://github.com/Microsoft/windows-admin-center-sdk/blob/master/WindowsAdminCenterDesignToolkit.zip)для Windows Admin Center! Этот набор средств предназначен для быстрого макетирования расширений в PowerPoint с помощью стилей, элементов управления и шаблонов страниц центра администрирования Windows. Прежде чем приступить к написанию кода, посмотрите, как ваше расширение будет выглядеть в центре администрирования Windows!

