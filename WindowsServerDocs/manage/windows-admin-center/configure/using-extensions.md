---
title: Установка и Управление расширениями
description: Установка расширений и управление ими в Windows Admin Center (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: c775dd5a3011115bbb031c0b9e4e24a8911d378e
ms.sourcegitcommit: 2977c707a299929c6ab0d1e0adab2e1c644b8306
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63748404"
---
# <a name="install-and-manage-extensions"></a>Установка и Управление расширениями

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Windows Admin Center построен это расширяемая платформа, где каждый тип соединения и средства — это расширение, можно установить, удалить и обновлять по отдельности. Можно искать новые расширения, опубликованные корпорацией Майкрософт и другими разработчиками и установить и обновить их по отдельности без обновления всей установки Windows Admin Center. Также можно настроить отдельные веб-канал NuGet или файловый ресурс и распространение расширений для внутреннего использования в вашей организации.

## <a name="installing-an-extension"></a>Установка расширения

Windows Admin Center покажет модулей, доступных из указанного веб-канал NuGet. По умолчанию Windows Admin Center указывает на веб-канал NuGet официальный Microsoft включающий расширения, опубликованные корпорацией Майкрософт и другими разработчиками.

1. Нажмите кнопку **параметры** кнопки в правом верхнем углу > в левой области щелкните **расширения**. 
2. **Доступных расширений** вкладке будет список расширений веб-канала, которые становятся доступными для установки.
3. Щелкните для расширения, чтобы просмотреть описание расширений, версию, издателя и другие сведения в **сведения** области.
4. Нажмите кнопку **установить** для установки расширения. Если шлюз необходимо запускать в режиме с повышенными правами, чтобы внести это изменение, появится запрос на повышение прав. После завершения установки браузера будут автоматически обновляться, и Windows Admin Center будет перезагружен с установленным расширением новый. Если расширение, к которому вы пытаетесь установить является обновлением ранее установленного расширения, можно щелкнуть **обновление до последней** кнопку, чтобы установить обновление. Вы также можете перейти к **установленные расширения** вкладке Просмотр установленных расширений и см. в разделе, если обновление доступно в **состояние** столбца.

## <a name="installing-extensions-from-a-different-feed"></a>Установка расширений из разных веб-канала

Windows Admin Center поддерживает несколько веб-каналов, и можно просматривать и управлять пакетами из более чем одного веб-канала одновременно. Любой веб-канал NuGet, поддерживаемые API-интерфейсы NuGet V2 или общей папки можно добавить Windows Admin Center для установки расширения.

1. Нажмите кнопку **параметры** кнопки в правом верхнем углу > в левой области щелкните **расширения**.
2. На правой панели щелкните **веб-каналов** вкладки.
3. Нажмите кнопку **добавить** кнопку, чтобы добавить другой веб-канал. Для веб-канал NuGet введите URL-адрес канала V2 NuGet. Поставщик веб-каналов NuGet или администратор должен иметь возможность предоставить их URL-адрес. Для файлового ресурса, введите полный путь файла совместного использования, в которой хранятся файлы пакета расширения (файла nupkg).
4. Нажмите кнопку **Добавить**. Если шлюз необходимо запускать в режиме с повышенными правами, чтобы внести это изменение, появится запрос на повышение прав.

**Доступных расширений** списке будут показаны модули из всех зарегистрированных каналов. Чтобы узнать, какие веб-канал, каждое расширение — с помощью **веб-канала пакетов** столбца.

## <a name="uninstalling-an-extension"></a>Удаление расширения

Можно удалить любые расширения, которые вы ранее установили или даже удалить любые инструменты, которые были предварительно установлены в процессе установки Windows Admin Center.

1. Нажмите кнопку **параметры** кнопки в правом верхнем углу > в левой области щелкните **расширения**. 
2. Нажмите кнопку **установленные расширения** вкладку, чтобы просмотреть все установленные расширения.
3. Выберите расширение для удаления, а затем щелкните **удаления**.

После удаления завершения, браузер будет автоматически обновлен и Windows Admin Center будет перезагружен с расширением удалены. Если вы удалили это средство, которое было предварительно устанавливается как часть Windows Admin Center, средство будет для переустановки в **доступных расширений** вкладки.

## <a name="installing-extensions-on-a-computer-without-internet-connectivity"></a>Установка расширений на компьютере без подключения к Интернету

Если Windows Admin Center устанавливается на компьютере, который не подключен к Интернету или находится за прокси-сервер, может оказаться доступ и возможность установить расширения из Windows Admin Center веб-канала. Можно скачать пакеты расширений, вручную или с помощью сценария PowerShell и настройка Windows Admin Center для получения пакетов из общей папки или локальный диск.

### <a name="manually-downloading-extension-packages"></a>Вручную загружать пакеты расширений

1. На другом компьютере, подключенном к Интернету откройте веб-браузер и перейдите по следующему АДРЕСУ: [https://msft-sme.myget.org/gallery/windows-admin-center-feed](https://msft-sme.myget.org/gallery/windows-admin-center-feed) 

  * Может потребоваться создать учетную запись на msft sme.myget.org и имя пользователя для просмотра пакетов расширения.

2. Щелкните имя пакета, который вы хотите установить, чтобы просмотреть страницу сведений о пакете.
3. Щелкните **загрузить** ссылку в области справа на странице сведений о пакете и скачайте файл nupkg для расширения.
4. Повторите шаги 2 и 3 для всех пакетов, который вы хотите загрузить.
5. Скопируйте файлы пакета в общую папку, доступную на компьютере установлены Windows Admin Center на или на локальный диск компьютера.
6. [Следуйте инструкциям, чтобы установить расширения из другой веб-канал](#installing-extensions-from-a-different-feed).

### <a name="downloading-packages-with-a-powershell-script"></a>Скачивание пакетов с помощью сценария PowerShell

Существует много сценариев в Интернете для загрузки пакетов NuGet из веб-канала NuGet. Мы будем использовать [сценария, предоставленного Джон Гэллоуэй](https://weblogs.asp.net/jongalloway/downloading-a-local-nuget-repository-with-powershell), старший руководитель программы в корпорации Microsoft.

1. Как описано в разделе [блога](https://weblogs.asp.net/jongalloway/downloading-a-local-nuget-repository-with-powershell), устанавливать этот сценарий как пакет NuGet, или скопируйте и вставьте сценарий в интегрированной среде Сценариев PowerShell.
2. Редактирование, первая часть скрипта NuGet веб-канала в URL-адрес версии 2. Если требуется загрузить пакеты из Windows Admin Center официальный веб-канала, используйте URL-адреса ниже.

```powershell
$feedUrlBase = "https://aka.ms/sme-extension-feed"
```

3. Запустите сценарий, а также загрузить все пакеты NuGet из канала в следующую папку на локальном: %USERPROFILE%\Documents\NuGetLocal
4. [Следуйте инструкциям, чтобы установить расширения из другой веб-канал](#installing-extensions-from-a-different-feed).

## <a name="manage-extensions-with-powershell"></a>Управление расширениями с помощью PowerShell

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Предварительная версия Windows Admin Center включает модуль PowerShell для управления расширениями шлюза.

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

### <a name="learn-more-about-building-an-extension-with-the-windows-admin-center-sdkextendextensibility-overviewmd"></a>[Дополнительные сведения о построении расширения с помощью пакета SDK Windows Admin Center](../extend/extensibility-overview.md).