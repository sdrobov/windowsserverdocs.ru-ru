---
title: Установка и Управление расширениями
description: Установка расширениям и управления ими в Windows Admin Center (проект Honolulu)
ms.technology: manage
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: c775dd5a3011115bbb031c0b9e4e24a8911d378e
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9296706"
---
# Установка и Управление расширениями

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Windows Admin Center разработано в виде — расширяемую платформу, где каждый тип подключения и средство — это расширение, можно устанавливать, удалять и обновлять по отдельности. Можно найти новые расширения, выпущенные корпорацией Майкрософт и другими разработчиками и устанавливать и обновлять их по отдельности без необходимости обновления всей установки Windows Admin Center. Можно также настроить отдельные канал NuGet или файлового ресурса и распространение расширений для внутреннего использования в вашей организации.

## Установка расширения

Windows Admin Center будет отображаться расширений, доступных из указанного NuGet веб-каналов. По умолчанию Windows Admin Center указывает Microsoft официальной NuGet веб-каналов котором размещена расширения, выпущенные корпорацией Майкрософт и другими разработчиками.

1. Нажмите кнопку " **Параметры** " в правом верхнем > на левой панели, щелкните **расширения**. 
2. Вкладку " **Доступные расширения** " будет содержать список расширений в веб-канала, доступных для установки.
3. Нажмите кнопку с определенным расширением, чтобы просмотреть описание расширения, версия, издателя и другие сведения, в области **сведений** .
4. Нажмите кнопку **установки** для установки расширения. Если шлюз необходимо работать в режиме с повышенными правами, чтобы внести изменения, появится запрос повышение прав контроля учетных Записей. После завершения установки браузера будут обновляться автоматически, и Windows Admin Center загружается с помощью нового расширения установки. Если расширение, которое вы пытаетесь установить является обновлением ранее установленные расширения, можно нажмите кнопку **обновления на последнюю версию** для установки обновления. Также можно перейти на вкладку " **Установленные расширения** " для просмотра установленные расширения и имеет ли обновления в столбце " **состояние** ".

## Установка расширений из разных веб-канала

Windows Admin Center поддерживает несколько каналов и можно просматривать и управления пакетами из нескольких канала одновременно. Любой NuGet веб-каналов, поддерживаемые API-интерфейсы NuGet V2 или общего файлового ресурса можно добавить в Windows Admin Center для установки расширения.

1. Нажмите кнопку " **Параметры** " в правом верхнем > на левой панели, щелкните **расширения**.
2. В правой области щелкните вкладку **веб-каналов** .
3. Нажмите кнопку **Добавить** , чтобы добавить другой канал. Канал NuGet введите URL-адреса канала V2 NuGet. NuGet перевода поставщика или администратора должна быть возможность предоставления сведений URL-адрес. Для общего файлового ресурса, введите полный путь к файлу общего доступа, в котором хранятся файлы пакета расширения (.nupkg).
4. Нажмите кнопку **Добавить**. Если шлюз необходимо работать в режиме с повышенными правами, чтобы внести изменения, появится запрос повышение прав контроля учетных Записей.

Список **Доступных расширений** отобразит расширений из всех зарегистрированных веб-каналы. Можно проверить, какие веб-канала, каждое расширение — с помощью столбца **Пакета веб-каналов** .

## Удаление расширения

Можно удалить все расширения, которые вы ранее устанавливали или даже удалять все средства, которые были предварительно установлены во время установки Windows Admin Center.

1. Нажмите кнопку " **Параметры** " в правом верхнем > на левой панели, щелкните **расширения**. 
2. Щелкните вкладку " **Установленные расширения** " для просмотра всех установленных расширений.
3. Выберите расширения для удаления, а затем нажмите кнопку **удаления**.

После удаления завершения, браузер автоматически обновляются и Windows Admin Center загружается с расширением удален. При удалении средство, которое было предварительно установить как часть Windows Admin Center, средство будут доступны для повторной установки на вкладке " **Доступные расширения** ".

## Установка расширений на компьютере без подключения к Интернету

Если Windows Admin Center установлен на компьютере, который не подключен к Интернету или находится за прокси-сервера, его может не смогут получать доступ к и установить расширения в Windows Admin Center веб-каналов. Можно загрузить пакеты расширений вручную или с помощью сценария PowerShell и настройки Windows Admin Center получить пакеты из общей папке или на локальном диске.

### Загрузка пакеты расширений вручную

1. На другом компьютере, который подключен к Интернету откройте браузер и перейдите на следующий URL-адрес:[https://msft-sme.myget.org/gallery/windows-admin-center-feed](https://msft-sme.myget.org/gallery/windows-admin-center-feed) 

  * Необходимо создать учетную запись в msft sme.myget.org и имя пользователя для просмотра пакеты расширения.

2. Щелкните имя пакета, который вы хотите установить для просмотра на странице сведений о пакете.
3. Щелкните ссылку **загрузить** в области справа на странице сведений о пакете и загрузите файл .nupkg для расширения.
4. Повторите шаги 2 и 3 для всех пакетов, которые следует загрузить.
5. Скопируйте файлы пакетов для файлового ресурса, который может осуществляться из Windows Admin Center устанавливается на компьютер или на локальный диск компьютера.
6. [Следуйте инструкциям, чтобы установить расширения из разных веб-канала](#installing-extensions-from-a-different-feed).

### Загрузка пакетов с помощью сценария PowerShell

Существует много сценариев в Интернете для загрузки пакетов NuGet из NuGet веб-каналов. Мы будем использовать [сценарий, предоставляемые Jon Galloway](https://weblogs.asp.net/jongalloway/downloading-a-local-nuget-repository-with-powershell), старший руководитель программы в корпорации Майкрософт.

1. Как описано в [запись в блоге](https://weblogs.asp.net/jongalloway/downloading-a-local-nuget-repository-with-powershell), установите сценарий в виде пакета NuGet или копировать и вставить сценарий в интегрированной среды Сценариев PowerShell.
2. Редактирование, первая строка сценарий для вашей NuGet веб-каналов, v2 URL-адрес. Если требуется загрузить пакеты из Windows Admin Center официальный веб-каналов, используйте URL-АДРЕСУ.

```powershell
$feedUrlBase = "https://aka.ms/sme-extension-feed"
```

3. Запустите сценарий и все пакеты NuGet будут загружены из канала к следующей локальной папке: %USERPROFILE%\Documents\NuGetLocal
4. [Следуйте инструкциям, чтобы установить расширения из разных веб-канала](#installing-extensions-from-a-different-feed).

## Управление расширениями с помощью PowerShell

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Ознакомительная версия Windows Admin Center включает модуль PowerShell для управления расширений шлюза.

```powershell
# Add the module to the current session
Import-Module "$env:ProgramFiles\windows admin center\PowerShell\Modules\ExtensionTools"
# Available cmdlets: Get-Feed, Add-Feed, Remove-Feed, Get-Extension, Install-Extension, Uninstall-Extension, Update-Extension

# List feeds
Get-Feed "https://wac.contoso.com"

# Add a new extension feed
Add-Feed -GatewayEndpoint "https://wac.contoso.com" -Feed "\\WAC\our-private-extensions"

# Remove an extension feed
Remove-Feed -GatewayEndpoint "https://wac.contoso.com" -Feed "\\WAC\our-private-extensions"

# List all extensions
Get-Extension "https://wac.contoso.com"

# Install an extension (locate the latest version from all feeds and install it)
Install-Extension -GatewayEndpoint "https://wac.contoso.com" "msft.sme.containers"

# Install an extension (latest version from a specific feed, if the feed is not present, it will be added)
Install-Extension -GatewayEndpoint "https://wac.contoso.com" "msft.sme.containers" -Feed "https://aka.ms/sme-extension-feed"

# Install an extension (install a specific version)
Install-Extension "https://wac.contoso.com" "msft.sme.certificate-manager" "0.133.0"

# Uninstall-Extension
Uninstall-Extension "https://wac.contoso.com" "msft.sme.containers"

# Update-Extension
Update-Extension "https://wac.contoso.com" "msft.sme.containers"
```

### [Дополнительные сведения о построении расширения с помощью пакета SDK Windows Admin Center](../extend/extensibility-overview.md).